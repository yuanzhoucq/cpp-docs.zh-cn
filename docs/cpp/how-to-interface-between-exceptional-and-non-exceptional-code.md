---
title: 'How to: Interface between exceptional and non-exceptional code'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
ms.openlocfilehash: fccc40302ab7bd43b3e6b2f87eef488c7813c9be
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245610"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>How to: Interface between exceptional and non-exceptional code

本文介绍如何在 C++ 模块中实现一致的异常处理，以及如何在异常边界将异常和错误代码进行互相转换。

有时 C++ 模块必须与不使用异常的代码（非异常代码）进行交互。 Such an interface is known as an *exception boundary*. 例如，您可能希望在 C++程序中调用 Win32 的函数 `CreateFile`。 `CreateFile` 不会引发异常；而会设置 `GetLastError` 函数可能检索到的错误代码。 如果您的 C++ 程序很重要，则您可能更愿意在其中部署一致的基于异常的错误处理策略。 此外，你可能不想放弃异常，因为你与异常代码相接；你也不希望在 C ++ 模块中将基于异常的错误策略与不基于异常的错误策略混合。

## <a name="calling-non-exceptional-functions-from-c"></a>Calling non-exceptional functions from C++

当您从 C++ 调用非异常函数时，您的想法是将该函数包装在检测任何错误的 C++函数中，然后可能引发异常。 当设计此类包装器函数时，首先应确定提供的异常保证的类型：no-throw、strong 或 basic。 其次，设计函数以使得异常引发时能够正确发布所有资源（例如文件句柄）。 通常，这意味着您可使用智能指针或类似的资源管理器来拥有资源。 For more information about design considerations, see [How to: Design for Exception Safety](how-to-design-for-exception-safety.md).

### <a name="example"></a>示例

以下示例演示使用 Win32 `CreateFile` 和 `ReadFile`函数在内部打开并读取两个文件的 C++ 函数。  `File` 类是文件句柄的“资源获取即是初始化”(RAII) 包装器。 其构造函数检测到“找不到文件”条件并引发了在 C++ 模块的调用堆栈（本示例中为 `main()` 函数）中向上传播错误的异常。 如果在完全构造好 `File` 对象后引发了异常，析构函数将自动调用 `CloseHandle` 以释放文件句柄。 (If you prefer, you can use the Active Template Library (ATL) `CHandle` class for this same purpose, or a `unique_ptr` together with a custom deleter.) The functions that call Win32 and CRT APIs detect errors and then throw C++ exceptions using the locally-defined `ThrowLastErrorIf` function, which in turn uses the `Win32Exception` class, derived from the `runtime_error` class. 本示例中的所有函数提供了强力的异常保证；当这些函数中的任何点上引发异常时，资源不会泄漏，程序状态也不会修改。

```cpp
// compile with: /EHsc
#include <Windows.h>
#include <stdlib.h>
#include <vector>
#include <iostream>
#include <string>
#include <limits>
#include <stdexcept>

using namespace std;

string FormatErrorMessage(DWORD error, const string& msg)
{
    static const int BUFFERLENGTH = 1024;
    vector<char> buf(BUFFERLENGTH);
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),
        BUFFERLENGTH - 1, 0);
    return string(buf.data()) + "   ("  + msg  + ")";
}

class Win32Exception : public runtime_error
{
private:
    DWORD m_error;
public:
    Win32Exception(DWORD error, const string& msg)
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }

    DWORD GetErrorCode() const { return m_error; }
};

void ThrowLastErrorIf(bool expression, const string& msg)
{
    if (expression) {
        throw Win32Exception(GetLastError(), msg);
    }
}

class File
{
private:
    HANDLE m_handle;

    // Declared but not defined, to avoid double closing.
    File& operator=(const File&);
    File(const File&);
public:
    explicit File(const string& filename)
    {
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,
            "CreateFile call failed on file named " + filename);
    }

    ~File() { CloseHandle(m_handle); }

    HANDLE GetHandle() { return m_handle; }
};

size_t GetFileSizeSafe(const string& filename)
{
    File fobj(filename);
    LARGE_INTEGER filesize;

    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);

    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {
        return filesize.QuadPart;
    } else {
        throw;
    }
}

vector<char> ReadFileVector(const string& filename)
{
    File fobj(filename);
    size_t filesize = GetFileSizeSafe(filename);
    DWORD bytesRead = 0;

    vector<char> readbuffer(filesize);

    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),
        &bytesRead, nullptr);
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);

    cout << filename << " file size: " << filesize << ", bytesRead: "
        << bytesRead << endl;

    return readbuffer;
}

bool IsFileDiff(const string& filename1, const string& filename2)
{
    return ReadFileVector(filename1) != ReadFileVector(filename2);
}

#include <iomanip>

int main ( int argc, char* argv[] )
{
    string filename1("file1.txt");
    string filename2("file2.txt");

    try
    {
        if(argc > 2) {
            filename1 = argv[1];
            filename2 = argv[2];
        }

        cout << "Using file names " << filename1 << " and " << filename2 << endl;

        if (IsFileDiff(filename1, filename2)) {
            cout << "+++ Files are different." << endl;
        } else {
            cout<< "=== Files match." << endl;
        }
    }
    catch(const Win32Exception& e)
    {
        ios state(nullptr);
        state.copyfmt(cout);
        cout << e.what() << endl;
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')
            << e.GetErrorCode() << endl;
        cout.copyfmt(state); // restore previous formatting
    }
}
```

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>Calling exceptional code from non-exceptional code

声明为“Extern C”的 C++ 函数可由 C 程序调用。 C++ COM 服务器可由采用很多不同的语言中的任何一种编写的代码使用。 在使用 C++ 实现将由非异常代码调用的可识别异常的公共函数时，C++ 函数不得允许将任何异常传播回调用方。 因此，C++ 函数必须专门捕获它知道如何处理的所有异常，并根据需要将异常转换为调用方能理解的错误代码 如果 C++函数并非了解所有可能的异常，它应将 `catch(...)` 块作为最后一个处理程序。 在这种情况下，最好向调用方报告错误，因为您的程序可能处于未知状态。

以下示例演示了一个函数，该函数假定可能引发的任何异常是 Win32 异常或者属于派生自 `std::exception` 的异常类型。 该函数将捕获这些类型的任何异常并将错误信息作为 Win32 错误代码传递给调用方。

```cpp
BOOL DiffFiles2(const string& file1, const string& file2)
{
    try
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return FALSE;
        }
        return TRUE;
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }

    catch(std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return FALSE;
}
```

当从异常转换为错误代码时，一个潜在问题是错误代码包含的信息通常不及异常可存储的信息丰富。 To address this, you can provide a **catch** block for each specific exception type that might be thrown, and perform logging to record the details of the exception before it is converted to an error code. This approach can create a lot of code repetition if multiple functions all use the same set of **catch** blocks. A good way to avoid code repetition is by refactoring those blocks into one private utility function that implements the **try** and **catch** blocks and accepts a function object that is invoked in the **try** block. 在每个公用函数中，将代码传递到实用工具函数以作为 lambda 表达式。

```cpp
template<typename Func>
bool Win32ExceptionBoundary(Func&& f)
{
    try
    {
        return f();
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }
    catch(const std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return false;
}
```

以下示例演示如何编写函数定义的 lambda 表达式。 如果使用 lambda 表达式将某个函数定义为“内联”，该函数通常比作为命名函数对象编写时更容易读取。

```cpp
bool DiffFiles3(const string& file1, const string& file2)
{
    return Win32ExceptionBoundary([&]() -> bool
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return false;
        }
        return true;
    });
}
```

有关 lambda 表达式的详细信息，请参阅 [Lambda 表达式](lambda-expressions-in-cpp.md)。

## <a name="see-also"></a>请参阅

[Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)<br/>
[如何：设计异常安全性](how-to-design-for-exception-safety.md)<br/>
