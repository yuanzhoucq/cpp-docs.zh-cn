---
title: "如何：异常和非异常代码之间的接口 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：异常和非异常代码之间的接口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍如何在C\+\+模块实现异常一致处理，以及如何向以及从异常边界转换错误代码。。  
  
 有时C\+\+模块必须以不使用异常的代码为接口 \(非异常代码\)。  此类接口称为*异常边界*。  例如，你可能在你的C\+\+程序中调用Win32的函数`CreateFile`。  `CreateFile` 不会抛出异常；而设置错误代码可以由 `GetLastError` 函数检索。  如果您的C\+\+程序很重要，则在您可能希望一直有基于异常的错误处理的策略。  因为你的接口中没有异常代码，所以你可能不会遗弃异常，你也不会在C\+\+模块中混合基于异常和不基于异常的错误策略。  
  
## 从C\+\+中调用非异常功能  
 当您从C\+\+调用非异常功能时，则该目的是用一个C\+\+函数包装他用来探测任何错误，这样就有可能抛出异常。  当设计这样的包装函数时，首先确定提供哪一种类型的异常：不抛出，强壮型，基本型。  接下来，设计功能，以便异常抛出时所有资源会正确的发布。例如文件处理。  通常，这意味着您使用智能指针或类似的资源管理器来拥有资源。  有关大小设计需要考虑的信息，请参见[如何：设计异常安全性](../cpp/how-to-design-for-exception-safety.md)。  
  
### 示例  
 下面的示例演示C\+\+函数使用 Win32 `CreateFile` 和 `ReadFile`函数在在内部打开并读取两个文件。`File` 选件类是"获取资源即初始化"的文件句柄的 \(RAII\) 包装。  其构造函数检测一个“文件未找到”条件并引发异常传播 C\+\+ 模块的调用堆栈的错误\(在此示例中，`main()` 函数\)。  如果引发异常，在 `File` 对象完全构造后，析构函数自动调用 `CloseHandle`释放文件句柄。\(如果您愿意，可以使用活动模板库 \(ATL\) `CHandle` 选件类或包含传统删除的 `unique_ptr`为了共同的目的\)函数通过调用 Win32 和 CRT的API 使用本地定义的 `ThrowLastErrorIf` 函数的功能，检测错误然后引发 C\+\+ 异常，使用从`runtime_error`类派生的`Win32Exception`类。  在此示例中的所有功能提供可靠的异常保护；如果在这些功能在任何时候引发，资源不会泄漏并且不修改程序状态。  
  
```cpp  
// compile with: /EHsc  
#include <Windows.h>  
#include <stdlib.h>  
#include <vector>  
#include <iostream>  
#include <string>  
#include <limits>  
#include <stdexcept>  
  
using namespace std;  
  
string FormatErrorMessage(DWORD error, const string& msg)  
{  
    static const int BUFFERLENGTH = 1024;  
    vector<char> buf(BUFFERLENGTH);  
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),   
        BUFFERLENGTH - 1, 0);   
    return string(buf.data()) + "   ("  + msg  + ")";  
}  
  
class Win32Exception : public runtime_error  
{      
private:  
    DWORD m_error;  
public:  
    Win32Exception(DWORD error, const string& msg)  
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }  
  
    DWORD GetErrorCode() const { return m_error; }  
};  
  
void ThrowLastErrorIf(bool expression, const string& msg)   
{   
    if (expression) {   
        throw Win32Exception(GetLastError(), msg);   
    }   
}   
  
class File  
{  
private:  
    HANDLE m_handle;  
  
    // Declared but not defined, to avoid double closing.  
    File& operator=(const File&);  
    File(const File&);  
public:  
    explicit File(const string& filename)   
    {  
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,   
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);  
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,   
            "CreateFile call failed on file named " + filename);  
    }  
  
    ~File() { CloseHandle(m_handle); }  
  
    HANDLE GetHandle() { return m_handle; }  
};  
  
size_t GetFileSizeSafe(const string& filename)  
{  
    File fobj(filename);  
    LARGE_INTEGER filesize;  
  
    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);  
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);  
  
    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {  
        return filesize.QuadPart;  
    } else {  
        throw;   
    }  
}  
  
vector<char> ReadFileVector(const string& filename)  
{  
    File fobj(filename);  
    size_t filesize = GetFileSizeSafe(filename);  
    DWORD bytesRead = 0;  
  
    vector<char> readbuffer(filesize);  
  
    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),   
        &bytesRead, nullptr);  
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);  
  
    cout << filename << " file size: " << filesize << ", bytesRead: "   
        << bytesRead << endl;  
  
    return readbuffer;  
}  
  
bool IsFileDiff(const string& filename1, const string& filename2)   
{  
    return ReadFileVector(filename1) != ReadFileVector(filename2);  
}   
  
#include <iomanip>  
  
int main ( int argc, char* argv[] )  
{  
    string filename1("file1.txt");  
    string filename2("file2.txt");  
  
    try  
    {  
        if(argc > 2) {  
            filename1 = argv[1];  
            filename2 = argv[2];  
        }   
  
        cout << "Using file names " << filename1 << " and " << filename2 << endl;  
  
        if (IsFileDiff(filename1, filename2)) {  
            cout << "*** Files are different." << endl;  
        } else {  
            cout<< "*** Files match." << endl;  
        }  
    }  
    catch(const Win32Exception& e)  
    {          
        ios state(nullptr);  
        state.copyfmt(cout);  
        cout << e.what() << endl;  
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')   
            << e.GetErrorCode() << endl;  
        cout.copyfmt(state); // restore previous formatting  
    }  
}  
  
```  
  
## 从非异常代码中调用异常代码  
 声明为“extern C”的 C\+\+ 函数可由C程序调用。  C\+\+ COM服务器可以通过在编写的代码使用任何许多不同的语言。  在实现在非异常代码时要调用的C\+\+的公共异常识别功能，C\+\+函数无法允许任何异常传播回调用方。  因此，C\+\+ 函数必须明确地捕获它知道如何处理的任何异常，并且，如果需要，将异常转换为调用者明白的错误代码  如果并非了解所有潜在的异常，C\+\+函数应具有 `catch(…)` 块作为最后一个处理程序。  在这种情况下，最好向调用者报告一个致命错误，因为你的程序处于一个未知状态。  
  
 下面的示例演示假定抛出任何异常，不管是Win32异常或从 `std::exception`派生的异常类型。  该函数捕获这些类型的所有异常并向调用方传递Win32的错误信息。  
  
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
  
 当从异常转换为错误代码时，一个潜在问题是错误代码通常不包含异常可以存储的丰富的信息  若要解决此问题，可为每个可能抛出的特殊异常提供 `catch`语句块块，并在转换成错误代码之前执行日志记录异常的详细信息的记录。  此方法可以创建大量代码副本，如果同一组的多个函数都使用`catch` 块。  一种好方法避免代码重复是通过重构这些块来实现 `try`和`catch` 并且接受`try`块加入后的函数。  在每个公共功能，过滤掉用希腊字母表示的外围函数。  
  
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
  
 下面的示例演示如何编写用希腊字母表示的表达式。  当用希腊字母表达表示一个“inline”函数定义时，比如果用命名函数对象命名好理解。  
  
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
  
 有关 lambda 表达式的更多信息，请参见 [lambda 表达式](../cpp/lambda-expressions-in-cpp.md)。  
  
## 请参阅  
 [错误和异常处理](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [如何：设计异常安全性](../cpp/how-to-design-for-exception-safety.md)