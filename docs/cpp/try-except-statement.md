---
title: "重试-除非语句 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24be4e7fd6b4dc95d9964e69943a94ecad947a47
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/25/2018
---
# <a name="try-except-statement"></a>try-except 语句

**Microsoft 专用**  
**重-除**语句是 Microsoft 扩展，对 C 和 c + + 语言的支持结构化异常处理。  

## <a name="syntax"></a>语法  
  
> **__try**   
> {  
>    受保护的代码  
> }  
> **__except** ( *expression* )  
> {  
>    异常处理程序代码  
> }  

## <a name="remarks"></a>备注

**重-除**语句是 Microsoft 扩展，对 C 和 c + + 语言，使目标应用程序能够获得控制正常终止程序执行的事件发生时。 此类事件称为*异常*，和处理异常的机制称为*结构化异常处理*(SEH)。

有关相关信息，请参阅[try-finally 语句](../cpp/try-finally-statement.md)。

异常可基于硬件，也可基于软件。 即使应用程序无法从硬件或软件异常中完全恢复，结构化异常处理也可以显示错误信息并捕获应用程序的内部状态，从而帮助诊断问题。 这对于无法轻松重现的间歇性问题特别有用。

> [!NOTE]
> 结构化异常处理适用于 Win32 中的 C 和 C++ 源文件。 但是，这不是专门为 C++ 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理更为灵活，因此它可以处理任何类型的异常。 对于 c + + 程序，建议你使用 c + + 异常处理机制 ([try、 catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)语句)。

在 `__try` 子句后的复合语句是主体或受保护节。 在 `__except` 子句后的复合语句是异常处理程序。 处理程序指定在执行受保护节的主体时引发了异常的情况下要执行的一组操作。 执行过程如下所示：

1. 执行受保护节。

2. 如果在受保护节执行过程中未发生异常，则继续执行 `__except` 子句之后的语句。  

3. 如果受保护节执行过程中发生异常或任何例程中受保护的节调用， `__except` *表达式*(调用*筛选器*表达式) 计算和值确定如何处理异常。 有三个值：

   **EXCEPTION_CONTINUE_EXECUTION (-1)**异常已消除。 从出现异常的点继续执行。

   **EXCEPTION_CONTINUE_SEARCH (0)**无法识别异常。 继续向上搜索堆栈查找处理程序，首先是所在的 **try-except** 语句，然后是具有下一个最高优先级的处理程序。

   **EXCEPTION_EXECUTE_HANDLER (1)**识别异常。 通过执行 `__except` 复合语句将控制权传输到异常处理程序，然后在 `__except` 块之后继续执行。

由于 `__except` 表达式将作为 C 表达式来计算，因此它被限制为单个值、条件表达式运算符或逗号运算符。 如果需要更大量的处理，表达式可调用返回上面列出的三个值之一的例程。

每个应用程序都可以有各自的异常处理程序。

跳转到 `__try` 语句是无效的，但是，跳出这样一个语句是有效的。 如果在执行终止进程，不调用异常处理程序**重-除**语句。  
  
有关详细信息，请参阅知识库文章 Q315937：“如何：捕获 Visual C++ 应用程序中的堆栈溢出”。  
  
## <a name="the-leave-keyword"></a>__leave 关键字

`__leave`关键字是有效的受保护节中仅**重-除**语句和其效果是跳转到受保护节的结尾处。 将继续执行异常处理程序后的第一个语句。

A`goto`语句还可以跳出受保护的部分中，并且它不降低性能中的一样**的 try-finally**语句因为堆栈展开不会发生。 但是，建议使用 `__leave` 关键字而不是 `goto` 语句，这样在受保护节很大或者很复杂的情况下出现编程错误的可能性小一些。

### <a name="structured-exception-handling-intrinsic-functions"></a>结构化异常处理内部函数

结构化的异常处理提供了可供使用的两个内部函数**重-除**语句：`GetExceptionCode`和`GetExceptionInformation`。

`GetExceptionCode`返回异常的代码 （32 位整数）。

内部函数`GetExceptionInformation`返回指向包含有关异常的其他信息的结构的指针。 通过此指针，您可以访问在出现硬件异常时存在的计算机状态。 该结构如下所示：

```cpp  
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS; 
```  

将指针类型`PEXCEPTION_RECORD`和`PCONTEXT`包含文件中定义\<winnt.h >，和`_EXCEPTION_RECORD`和`_CONTEXT`包含文件中定义\<excpt.h >

你可以使用`GetExceptionCode`在异常处理程序。 但是，你可以使用`GetExceptionInformation`只能在异常筛选器表达式。 它指向的信息通常位于堆栈上，并且这些信息在控制权转交给异常处理程序之后不再可用。

内部函数`AbnormalTermination`终止处理程序内可用。 如果将返回 0 的正文**的 try-finally**语句将按顺序终止。 在所有其他情况下，它将返回 1。

excpt.h 定义为这些内部函数一些替代名称：

`GetExceptionCode`等效于`_exception_code`

 `GetExceptionInformation`等效于`_exception_info`

 `AbnormalTermination`等效于`_abnormal_termination`
  
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
  
```  
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

[编写异常处理程序](../cpp/writing-an-exception-handler.md)   
[结构化的异常处理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)   
[关键字](../cpp/keywords-cpp.md)
