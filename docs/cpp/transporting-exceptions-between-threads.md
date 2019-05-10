---
title: 线程之间传输异常
ms.date: 05/07/2019
helpviewer_keywords:
- std::current_exception
- transporting exceptions between threads
- std::copy_exception
- exception_ptr
- std::exception_ptr
- std::rethrow_exception
- current_exception
- transport exceptions between threads
- copy_exception
- rethrow_exception
- move exceptions between threads
ms.assetid: 5c95d57b-acf5-491f-8122-57c5df0edd98
ms.openlocfilehash: e59883c75fde9938a213fb4e888e6b05a79cf4f7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221924"
---
# <a name="transporting-exceptions-between-threads"></a>线程之间传输异常

MicrosoftC++编译器 (MSVC) 支持*传输异常*到另一个线程中。 通过传输异常，你可以在一个线程中捕获异常，然后使该异常看似是在另一个线程中引发的。 例如，你可以使用该功能编写多线程应用程序，其中主线程将处理其辅助线程引发的所有异常。 传输异常对创建并行编程库或系统的开发人员最有用处。 若要实现传输异常，MSVC 提供[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)类型并[current_exception](../standard-library/exception-functions.md#current_exception)， [rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)，和[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)函数。

## <a name="syntax"></a>语法

```cpp
namespace std
{
   typedef unspecified exception_ptr;
   exception_ptr current_exception();
   void rethrow_exception(exception_ptr p);
   template<class E>
       exception_ptr make_exception_ptr(E e) noexcept;
}
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*unspecified*|用于实现 `exception_ptr` 类型的未指定的内部类。|
|*p*|引用异常的 `exception_ptr` 对象。|
|*E*|表示异常的类。|
|*e*|参数 `E` 类的实例。|

## <a name="return-value"></a>返回值

`current_exception` 函数返回引用当前进行中的异常的 `exception_ptr` 对象。 如果没有进行中的异常，该函数将返回未与任何异常关联的 `exception_ptr` 对象。

`make_exception_ptr`函数返回`exception_ptr`对象，它引用指定的异常*e*参数。

## <a name="remarks"></a>备注

### <a name="scenario"></a>方案

假设你要创建能伸缩以处理可变工作负荷的应用程序。 为了实现此目标，你要设计一个多线程应用程序，其中初始的主线程会创建所需数量的辅助线程，以完成该工作。 辅助线程可帮助主线程管理资源、平衡负载和提高吞吐量。 通过分发工作，多线程应用程序的表现优于单线程应用程序。

但是，如果辅助线程引发异常，你希望主线程予以处理。 这是因为你希望你的应用程序无论有多少辅助线程，都能以一致统一的方式处理异常。

### <a name="solution"></a>解决方案

为处理先前的方案，C++ 标准支持在线程之间传输异常。 如果辅助线程引发异常，该异常会成为*当前异常*。 现实世界打比方，当前异常被认为是*起飞*。 当前异常从引发之时到捕获它的异常处理程序返回之时就处于飞行状态。

辅助线程可以捕获中的当前异常**捕获**阻止，，然后调用`current_exception`函数来存储中的异常`exception_ptr`对象。 `exception_ptr` 对象必须可用于辅助线程和主线程。 例如，`exception_ptr` 对象可以是全局变量，由 mutex 控制对它的访问。 术语*传输异常*意味着一个线程中的异常可以转换为另一个线程可以访问的窗体。

接下来，主线程调用 `rethrow_exception` 函数，该函数提取并继而引发 `exception_ptr` 对象中的异常。 异常引发后，将成为主线程中的当前异常。 也就是说，该异常看起来源自主线程。

最后，主线程可以捕获中的当前异常**捕获**阻止然后对其进行处理或其抛给更高级别的异常处理程序。 或者，主线程可以忽略该异常并允许该进程结束。

大多数应用程序不必在线程之间传输异常。 但是，该功能在并行计算系统中有用，是因为该系统可以在辅助线程、处理器或内核间分配工作。 在并行计算环境中，单个专用线程可以处理辅助线程中的所有异常，并可以为任何应用程序提供一致的异常处理模型。

有关 C++ 标准委员会建议的详细信息，请在 Internet 中搜索编号为 N2179，标题为“Language Support for Transporting Exceptions between Threads”（在线程之间传输异常的语言支持）的文档。

### <a name="exception-handling-models-and-compiler-options"></a>异常处理模型和编译器选项

你的应用程序的异常处理模型决定了它是否可以捕获和传输异常。 Visual C++ 支持三种模型，这些模型可以处理 C++ 异常、结构化异常处理 (SEH) 异常和公共语言运行时 (CLR) 异常。 使用[/EH](../build/reference/eh-exception-handling-model.md)并[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项可指定应用程序的异常处理模型。

只有编译器选项和编程语句的以下组合可以传输异常。 其他组合要么不能捕获异常，要么能捕获但不能传输异常。

- **/EHa**编译器选项和**捕获**语句可以传输 SEH 和C++异常。

- **/EHa**， **/EHs**，并 **/EHsc**编译器选项和**捕获**语句可以传输C++的异常。

- **/CLR**编译器选项和**捕获**语句可以传输C++异常。 **/CLR**编译器选项暗指的规范 **/EHa**选项。 请注意，编译器不支持传输托管异常。 这是因为托管异常，派生自[System.Exception 类](../standard-library/exception-class.md)，已经是您可以通过使用公共语言运行时的功能的线程之间移动的对象。

   > [!IMPORTANT]
   > 我们建议您指定 **/EHsc**编译器选项和 catch 仅 C++ 异常。 你可能面临安全威胁如果您使用 **/EHa**或 **/CLR**编译器选项和一个**捕获**语句使用省略号*异常声明*(`catch(...)`)。 你可能希望使用**捕获**语句捕获几个特定的异常。 但是，`catch(...)` 语句将捕获所有的 C++ 和 SEH 异常，包括致命的意外异常。 如果忽略意外异常或处理不当，恶意代码就可以趁此机会破坏你程序的安全性。

## <a name="usage"></a>用法

以下部分介绍如何通过使用传输异常`exception_ptr`类型，并`current_exception`， `rethrow_exception`，和`make_exception_ptr`函数。

## <a name="exceptionptr-type"></a>exception_ptr 类型

使用 `exception_ptr` 对象可引用当前异常或用户指定异常的实例。 在 Microsoft 实现中，异常由 [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) 结构表示。 每个 `exception_ptr` 对象包含一个异常引用字段，该字段指向表示异常的 `EXCEPTION_RECORD` 结构的副本。

当你声明 `exception_ptr` 变量时，该变量不与任何异常相关联。 也就是说，其异常引用字段为 NULL。 此类 `exception_ptr` 对象称为 *null exception_ptr*。

使用 `current_exception` 或 `make_exception_ptr` 函数可将异常指派给 `exception_ptr` 对象。 将异常指派给 `exception_ptr` 变量时，该变量的异常引用字段将指向该异常的副本。 如果没有足够的内存来复制异常，异常引用字段将指向 [std::bad_alloc](../standard-library/bad-alloc-class.md) 异常的副本。 如果`current_exception`或`make_exception_ptr`函数不能复制异常，任何其他原因，该函数将调用[终止](../c-runtime-library/reference/terminate-crt.md)函数退出当前进程。

尽管名称像是一个指针，但 `exception_ptr` 对象本身不属于指针。 它不遵循指针语义，不能与指针成员访问 (`->`) 或间接寻址 (`*`) 运算符。 `exception_ptr` 对象没有公共数据成员或成员函数。

### <a name="comparisons"></a>比较

你可以使用相等 (`==`) 和不相等 (`!=`) 运算符比较两个 `exception_ptr` 对象。 这两个运算符不比较表示异常的 `EXCEPTION_RECORD` 结构的二进制值（位模式）， 而是比较 `exception_ptr` 对象的异常引用字段中的地址。 因此，null `exception_ptr` 和 NULL 值的比较结果为相等。

## <a name="currentexception-function"></a>current_exception 函数

调用`current_exception`函数，在**捕获**块。 如果异常处于飞行状态并**捕获**块可捕获该异常`current_exception`函数返回`exception_ptr`引用异常的对象。 否则，该函数将返回 null `exception_ptr` 对象。

### <a name="details"></a>详细信息

`current_exception`函数会捕获的异常处于飞行状态，而不管是否**捕获**语句指定[异常声明](../cpp/try-throw-and-catch-statements-cpp.md)语句。

当前异常的析构函数调用的末尾**捕获**阻止如果不重新引发异常。 但是，即使调用析构函数中的 `current_exception` 函数，该函数仍返回引用当前异常的 `exception_ptr` 对象。

对 `current_exception` 函数的相继调用将返回引用当前异常的不同副本的 `exception_ptr` 对象。 因此，由于对象引用不同的副本，即使副本具有相同的二进制值，其比较结果也是不相等。

### <a name="seh-exceptions"></a>SEH 异常

如果您使用 **/EHa**编译器选项，可以捕获 SEH 异常中的C++**捕获**块。 `current_exception` 函数返回引用 SEH 异常的 `exception_ptr` 对象。 并`rethrow_exception`函数将引发 SEH 异常，如果调用使用 thetransported`exception_ptr`对象作为其参数。

`current_exception`函数将返回 null`exception_ptr`如果调用 seh **__finally**终止处理程序 **__except**异常处理程序，或 **__except**筛选器表达式。

传输的异常不支持嵌套异常。 如果处理异常时引发了另一个异常，会发生嵌套异常。 如果你捕获嵌套异常，`EXCEPTION_RECORD.ExceptionRecord` 数据成员将指向描述关联异常的 `EXCEPTION_RECORD` 结构链。 `current_exception` 函数不支持嵌套异常，因为它返回 `exception_ptr` 数据成员调零的 `ExceptionRecord` 对象。

如果你捕获 SEH 异常，则必须管理 `EXCEPTION_RECORD.ExceptionInformation` 数据成员数组中的任何指针所引用的内存。 你必须确保内存在相应的 `exception_ptr` 对象的生存期内有效，并且在 `exception_ptr` 对象删除时释放内存。

你可以将结构化异常 (SE) 转换器函数与传输异常功能结合使用。 如果 SEH 异常转换为 C++ 异常，`current_exception` 函数返回的 `exception_ptr` 将引用转换后的异常，而不是原始 SEH 异常。 `rethrow_exception` 函数随后引发转换后的异常，而不是原始异常。 有关 SE 转换器函数的详细信息，请参阅[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)。

## <a name="rethrowexception-function"></a>rethrow_exception 函数

在 `exception_ptr` 对象中存储捕获的异常后，主线程便可以处理该对象。 在主线程中，调用 `rethrow_exception` 函数，将 `exception_ptr` 对象作为其参数。 `rethrow_exception` 函数从 `exception_ptr` 对象中提取异常，然后在主线程的上下文中引发异常。 如果*p*的参数`rethrow_exception`函数为 null `exception_ptr`，该函数将引发[std:: bad_exception](../standard-library/bad-exception-class.md)。

提取的异常现在是主线程中的当前异常，因此你可以像处理任何其他异常一样对其进行处理。 如果你捕获异常，可以立即处理它，或使用**引发**语句，以将其发送到更高级别的异常处理程序。 否则，不执行任何操作并允许默认系统异常处理程序来终止进程。

## <a name="makeexceptionptr-function"></a>make_exception_ptr 函数

`make_exception_ptr` 函数采用类的实例作为其参数，然后返回引用该实例的 `exception_ptr`。 通常，指定[异常类](../standard-library/exception-class.md)对象作为参数传递给 `make_exception_ptr` 函数，但任意类对象都可以是参数。

调用`make_exception_ptr`函数是等效于引发C++异常，即捕获该中**捕获**块中，并调用`current_exception`函数以返回`exception_ptr`引用异常的对象。 Microsoft 实现的 `make_exception_ptr` 函数比调用并捕获异常更高效。

应用程序通常不需要 `make_exception_ptr` 函数，因此，我们不建议使用此函数。

## <a name="example"></a>示例

以下示例从一个线程向另一个线程传输标准 C++ 异常和自定义 C++ 异常。

```cpp
// transport_exception.cpp
// compile with: /EHsc /MD
#include <windows.h>
#include <stdio.h>
#include <exception>
#include <stdexcept>

using namespace std;

// Define thread-specific information.
#define THREADCOUNT 2
exception_ptr aException[THREADCOUNT];
int           aArg[THREADCOUNT];

DWORD WINAPI ThrowExceptions( LPVOID );

// Specify a user-defined, custom exception.
// As a best practice, derive your exception
// directly or indirectly from std::exception.
class myException : public std::exception {
};
int main()
{
    HANDLE aThread[THREADCOUNT];
    DWORD ThreadID;

    // Create secondary threads.
    for( int i=0; i < THREADCOUNT; i++ )
    {
        aArg[i] = i;
        aThread[i] = CreateThread(
            NULL,       // Default security attributes.
            0,          // Default stack size.
            (LPTHREAD_START_ROUTINE) ThrowExceptions,
            (LPVOID) &aArg[i], // Thread function argument.
            0,          // Default creation flags.
            &ThreadID); // Receives thread identifier.
        if( aThread[i] == NULL )
        {
            printf("CreateThread error: %d\n", GetLastError());
            return -1;
        }
    }

    // Wait for all threads to terminate.
    WaitForMultipleObjects(THREADCOUNT, aThread, TRUE, INFINITE);
    // Close thread handles.
    for( int i=0; i < THREADCOUNT; i++ ) {
        CloseHandle(aThread[i]);
    }

    // Rethrow and catch the transported exceptions.
    for ( int i = 0; i < THREADCOUNT; i++ ) {
        try {
            if (aException[i] == NULL) {
                printf("exception_ptr %d: No exception was transported.\n", i);
            }
            else {
                rethrow_exception( aException[i] );
            }
        }
        catch( const invalid_argument & ) {
            printf("exception_ptr %d: Caught an invalid_argument exception.\n", i);
        }
        catch( const myException & ) {
            printf("exception_ptr %d: Caught a  myException exception.\n", i);
        }
    }
}
// Each thread throws an exception depending on its thread
// function argument, and then ends.
DWORD WINAPI ThrowExceptions( LPVOID lpParam )
{
    int x = *((int*)lpParam);
    if (x == 0) {
        try {
            // Standard C++ exception.
            // This example explicitly throws invalid_argument exception.
            // In practice, your application performs an operation that
            // implicitly throws an exception.
            throw invalid_argument("A C++ exception.");
        }
        catch ( const invalid_argument & ) {
            aException[x] = current_exception();
        }
    }
    else {
        // User-defined exception.
        aException[x] = make_exception_ptr( myException() );
    }
    return TRUE;
}
```

```Output
exception_ptr 0: Caught an invalid_argument exception.
exception_ptr 1: Caught a  myException exception.
```

## <a name="requirements"></a>要求

**标头：**\<exception>

## <a name="see-also"></a>请参阅

[异常处理](../cpp/exception-handling-in-visual-cpp.md)<br/>
[/EH（异常处理模型）](../build/reference/eh-exception-handling-model.md)<br/>
[/cgthreads（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)