---
title: try-finally 语句
ms.date: 11/19/2018
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
ms.openlocfilehash: 045d2bf5617c81bcc4d7a202f36b112d5f0142a6
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246294"
---
# <a name="try-finally-statement"></a>try-finally 语句

**Microsoft 专用**

The following syntax describes the **try-finally** statement:

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// guarded code<br/>
> }<br/>
> **\_\_finally**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;// termination code<br/>
> }

## <a name="grammar"></a>语法

try-finally-statement:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\_\_try** *compound-statement* **\_\_finally** *compound-statement*

The **try-finally** statement is a Microsoft extension to the C and C++ languages that enables target applications to guarantee execution of cleanup code when execution of a block of code is interrupted. 清理包括多个任务，如释放内存、关闭文件和释放文件句柄。 The **try-finally** statement is especially useful for routines that have several places where a check is made for an error that could cause premature return from the routine.

For related information and a code sample, see [try-except Statement](../cpp/try-except-statement.md). For more information on structured exception handling in general, see [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). For more information on handling exceptions in managed applications with C++/CLI, see [Exception Handling under /clr](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> 结构化异常处理适用于 Win32 中的 C 和 C++ 源文件。 但是，这不是专门为 C++ 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理更为灵活，因此它可以处理任何类型的异常。 For C++ programs, it is recommended that you use the C++ exception-handling mechanism ([try, catch, and throw](../cpp/try-throw-and-catch-statements-cpp.md) statements).

The compound statement after the **__try** clause is the guarded section. The compound statement after the **__finally** clause is the termination handler. 处理程序指定了在退出受保护部分时执行的一组操作，无论受保护部分是因异常（不正常终止）还是因标准失效（正常终止）导致退出。

Control reaches a **__try** statement by simple sequential execution (fall through). When control enters the **__try**, its associated handler becomes active. 如果控制流到达 try 块的末尾，执行将继续，如下所示：

1. 调用终止处理程序。

1. When the termination handler completes, execution continues after the **__finally** statement. Regardless of how the guarded section ends (for example, via a **goto** out of the guarded body or a **return** statement), the termination handler is executed *before* the flow of control moves out of the guarded section.

   A **__finally** statement does not block searching for an appropriate exception handler.

If an exception occurs in the **__try** block, the operating system must find a handler for the exception or the program will fail. If a handler is found, any and all **__finally** blocks are executed and execution resumes in the handler.

例如，假设一个函数调用系列将函数 A 链接到函数 D，如下图所示。 每个函数均有一个终止处理程序。 如果异常在函数 D 中引发并在函数 A 中得到处理，则当系统展开堆栈时，按以下顺序调用终止处理程序：D、C、B。

![Order of termination&#45;handler execution](../cpp/media/vc38cx1.gif "Order of termination&#45;handler execution") <br/>
终止处理程序执行顺序

> [!NOTE]
> The behavior of try-finally is different from some other languages that support the use of **finally**, such as C#.  A single **__try** may have either, but not both, of **__finally** and **__except**.  如果同时使用二者，则外部 try-except 语句必须包含内部 try-finally 语句。  指定何时执行每个块的规则也有所不同。

For compatibility with previous versions, **_try**, **_finally**, and **_leave** are synonyms for **__try**, **__finally**, and **__leave** unless compiler option [/Za \(Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) is specified.

## <a name="the-__leave-keyword"></a>__leave 关键字

The **__leave** keyword is valid only within the guarded section of a **try-finally** statement, and its effect is to jump to the end of the guarded section. 执行将在终止处理程序中的第一个语句处继续。

A **goto** statement can also jump out of the guarded section, but it degrades performance because it invokes stack unwinding. The **__leave** statement is more efficient because it does not cause stack unwinding.

## <a name="abnormal-termination"></a>异常终止

Exiting a **try-finally** statement using the [longjmp](../c-runtime-library/reference/longjmp.md) run-time function is considered abnormal termination. It is illegal to jump into a **__try** statement, but legal to jump out of one. All **__finally** statements that are active between the point of departure (normal termination of the **__try** block) and the destination (the **__except** block that handles the exception) must be run. 这称为本地展开。

If a **try** block is prematurely terminated for any reason, including a jump out of the block, the system executes the associated **finally** block as a part of the process of unwinding the stack. In such cases, the [AbnormalTermination](/windows/win32/Debug/abnormaltermination) function returns **true** if called from within the **finally** block; otherwise, it returns **false**.

The termination handler is not called if a process is killed in the middle of executing a **try-finally** statement.

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[Termination-Handler Syntax](/windows/win32/Debug/termination-handler-syntax)