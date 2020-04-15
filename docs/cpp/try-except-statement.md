---
title: try-except 语句
description: Microsoft C++引用__try，__except结构化异常处理语句。
ms.date: 04/03/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: 132edf7cc9819637fafa3947686972d311924b99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366238"
---
# <a name="try-except-statement"></a>try-except 语句

**try-除了**语句是 Microsoft 扩展，支持 C 和 C++语言的结构化异常处理。 此扩展特定于**Microsoft。**

## <a name="syntax"></a>语法

> **\_\_尝试**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;守卫代码<br/>
> }<br/>
> （表达式*expression*） ** \_ \_**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;异常处理程序代码<br/>
> }

## <a name="remarks"></a>备注

**try-除了**语句是 Microsoft 对 C 和 C++语言的扩展。 它使目标应用程序能够在通常终止程序执行的事件发生时获得控制。 此类事件称为*结构化异常*，或简称*为例外*。 处理这些异常的机制称为*结构化异常处理*（SEH）。

有关相关信息，请参阅[尝试最后语句](../cpp/try-finally-statement.md)。

例外情况可以是基于硬件的，也可以是基于软件的。 即使应用程序无法从硬件或软件异常中完全恢复，结构化异常处理也很有用。 SEH 能够显示错误信息并捕获应用程序的内部状态，以帮助诊断问题。 它对于不易重现的间歇性问题特别有用。

> [!NOTE]
> 结构化异常处理适用于 Win32 中的 C 和 C++ 源文件。 但是，它不是专门为C++设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理更为灵活，因此它可以处理任何类型的异常。 对于C++程序，我们建议您使用本机C++异常处理：[尝试、捕获和引发](../cpp/try-throw-and-catch-statements-cpp.md)语句。

**__try**条款后的复合语句是*正文*或*受保护*部分。 **__except**表达式也称为*筛选器*表达式。 其值确定如何处理异常。 **__except**子句之后的复合语句是异常处理程序。 处理程序指定在执行正文部分期间引发异常时要执行的操作。 执行过程如下所示：

1. 执行受保护节。

1. 如果在执行受保护部分期间未发生异常，则在 **__except**子句之后的语句将继续执行。

1. 如果在执行受保护节期间或在任何例程中发生异常，则计算 **__except**表达式。 有三种可能的值：

   - `EXCEPTION_CONTINUE_EXECUTION`(-1)异常将被驳回。 从出现异常的点继续执行。

   - `EXCEPTION_CONTINUE_SEARCH`（0） 例外情况未识别。 继续向上搜索堆栈查找处理程序，首先是所在的 **try-except** 语句，然后是具有下一个最高优先级的处理程序。

   - `EXCEPTION_EXECUTE_HANDLER`（1） 确认例外情况。 通过执行 **__except**复合语句将控件转移到异常处理程序，然后在 **__except**块之后继续执行。

**__except**表达式被计算为 C 表达式。 它仅限于单个值、条件表达式运算符或逗号运算符。 如果需要更大量的处理，表达式可调用返回上面列出的三个值之一的例程。

每个应用程序都可以有各自的异常处理程序。

跳入 **__try**语句无效，但跳出一个语句无效。 如果在执行**try-除外**语句的过程中终止进程，则不调用异常处理程序。

为了与以前的版本兼容 **，_try、_except**和 **_leave**是 **_except****__try、__except**和 **__except****__leave**的同义词，除非指定编译器选项[/Za\(禁用语言扩展）。](../build/reference/za-ze-disable-language-extensions.md)

### <a name="the-__leave-keyword"></a>__leave 关键字

**__leave**关键字仅在**try-除了**语句的受保护部分内有效，其效果是跳转到受保护部分的末尾。 将继续执行异常处理程序后的第一个语句。

**goto**语句也可以跳出受保护的部分，并且它不会像**尝试-最终**语句那样降低性能。 这是因为不会进行堆栈展开。 但是，我们建议您使用 **__leave**关键字而不是**goto**语句。 原因是，如果受保护的部分很大或很复杂，则不太可能出现编程错误。

### <a name="structured-exception-handling-intrinsic-functions"></a>结构化异常处理内部函数

结构化异常处理提供了两个可用于**try-除一**语句的固有函数：[获取ExceptionCode](/windows/win32/Debug/getexceptioncode)和[Getexception信息](/windows/win32/Debug/getexceptioninformation)。

`GetExceptionCode`返回异常的代码（32 位整数）。

内部函数`GetExceptionInformation`返回指向[EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers)结构的指针，其中包含有关异常的其他信息。 通过此指针，您可以访问在出现硬件异常时存在的计算机状态。 结构如下：

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

指针`PEXCEPTION_RECORD`类型和`PCONTEXT`定义在 include 文件\<winnt.h>，`_EXCEPTION_RECORD`并在`_CONTEXT`include 文件\<excpt.h>

您可以在异常处理程序`GetExceptionCode`中使用。 但是，`GetExceptionInformation`只能在异常筛选器表达式中使用。 它指向的信息通常位于堆栈上，当控件传输到异常处理程序时，这些信息不再可用。

内在函数[异常终止](/windows/win32/Debug/abnormaltermination)在终止处理程序中可用。 如果**try-finally**语句的正文按顺序终止，则返回 0。 在所有其他情况下，它将返回 1。

\<excpt.h>定义这些内部函数的一些备用名称：

`GetExceptionCode` 等效于 `_exception_code`

`GetExceptionInformation` 等效于 `_exception_info`

`AbnormalTermination` 等效于 `_abnormal_termination`

## <a name="example"></a>示例

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>输出

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

## <a name="see-also"></a>另请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
