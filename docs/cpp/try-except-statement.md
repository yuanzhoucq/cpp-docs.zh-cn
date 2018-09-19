---
title: 请尝试-除非语句 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- EXCEPTION_CONTINUE_SEARCH
- _exception_info
- __except
- EXCEPTION_CONTINUE_EXECUTION
- _exception_code
- __except_cpp
- _exception_info_cpp
- EXCEPTION_EXECUTE_HANDLER
- _abnormal_termination
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 107b759345e221ad8100f11d97b79c5bd9fd2b65
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031428"
---
# <a name="try-except-statement"></a>try-except 语句

**Microsoft 专用**

**重-除**语句是 Microsoft 扩展，对 C 和 C++ 语言的支持结构化异常处理。

## <a name="syntax"></a>语法

> **__try** {/ / 受保护的代码} **__except** (*表达式*) {/ / 异常处理程序代码}

## <a name="remarks"></a>备注

**重-除**语句是 Microsoft 扩展，对 C 和 C++ 语言，使目标应用程序能够获得控制正常终止程序执行的事件发生时。 此类事件称为*异常*，并处理异常的机制称为*结构化异常处理*(SEH)。

有关相关信息，请参阅[try-finally 语句](../cpp/try-finally-statement.md)。

异常可基于硬件，也可基于软件。 即使应用程序无法从硬件或软件异常中完全恢复，结构化异常处理也可以显示错误信息并捕获应用程序的内部状态，从而帮助诊断问题。 这对于无法轻松重现的间歇性问题特别有用。

> [!NOTE]
> 结构化异常处理适用于 Win32 中的 C 和 C++ 源文件。 但是，这不是专门为 C++ 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理更为灵活，因此它可以处理任何类型的异常。 对于 C++ 程序，建议你使用 C++ 异常处理机制 ([try、 catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)语句)。

后的复合语句 **__try**子句是主体或受保护的节。 后的复合语句 **__except**子句是异常处理程序。 处理程序指定在执行受保护节的主体时引发了异常的情况下要执行的一组操作。 执行过程如下所示：

1. 执行受保护节。

2. 如果在受保护节执行过程中不发生任何异常，则继续执行之后的语句 **__except**子句。

3. 如果受保护节执行过程中发生异常或任何例程中受保护的节调用的 **__except** *表达式*(称为*筛选器*表达式)进行评估，值将确定异常的处理方式。 有三个值：

   EXCEPTION_CONTINUE_EXECUTION (-1) 异常已消除。 从出现异常的点继续执行。

   EXCEPTION_CONTINUE_SEARCH (0) 异常无法识别。 继续向上搜索堆栈查找处理程序，首先是所在的 **try-except** 语句，然后是具有下一个最高优先级的处理程序。

   EXCEPTION_EXECUTE_HANDLER (1) 异常可识别。 将控件传输到异常处理程序，通过执行 **__except**复合语句，然后继续执行后的 **__except**块。

因为 **__except**作为 C 表达式计算表达式，它被限制为单个值、 条件表达式运算符或逗号运算符。 如果需要更大量的处理，表达式可调用返回上面列出的三个值之一的例程。

每个应用程序都可以有各自的异常处理程序。

它不是有效的跳转到 **__try**语句，但有效跳出。 如果在执行会终止进程不调用异常处理程序**试用-除**语句。

有关详细信息，请参阅知识库文章 Q315937：“如何：捕获 Visual C++ 应用程序中的堆栈溢出”。

## <a name="the-leave-keyword"></a>__leave 关键字

**__Leave**关键字是仅在受保护节的有效**试用-除**语句和其效果是跳转到受保护部分的结尾。 将继续执行异常处理程序后的第一个语句。

一个**goto**语句也可以跳出受保护节，它不会不会降低性能中的一样**的 try-finally**语句由于堆栈展开不会出现。 但是，我们建议你使用 **__leave**关键字而非**goto**语句由于您不太可能进行编程错误，如果受保护的节很大或很复杂。

### <a name="structured-exception-handling-intrinsic-functions"></a>结构化异常处理内部函数

结构化的异常处理提供了两个可用于内部函数**试用-除**语句：`GetExceptionCode`和`GetExceptionInformation`。

`GetExceptionCode` 返回异常的代码 （32 位整数）。

内部函数`GetExceptionInformation`返回指向包含有关异常的其他信息的结构的指针。 通过此指针，您可以访问在出现硬件异常时存在的计算机状态。 该结构如下所示：

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

指针类型`PEXCEPTION_RECORD`并`PCONTEXT`在包含文件中定义\<winnt.h 中的 >，和`_EXCEPTION_RECORD`并`_CONTEXT`包含文件中定义\<excpt.h >

可以使用`GetExceptionCode`在异常处理程序。 但是，可以使用`GetExceptionInformation`仅在异常筛选器表达式中。 它指向的信息通常位于堆栈上，并且这些信息在控制权转交给异常处理程序之后不再可用。

内部函数`AbnormalTermination`终止处理程序中可用。 如果将返回 0 的正文**的 try-finally**语句按顺序终止。 在所有其他情况下，它将返回 1。

excpt.h 定义这些内部函数的一些替代名称：

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

## <a name="output"></a>输出

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

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)