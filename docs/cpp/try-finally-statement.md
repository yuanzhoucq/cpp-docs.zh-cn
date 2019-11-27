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

以下语法介绍了**try finally**语句：

> **\_\_尝试**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//受保护代码<br/>
> }<br/>
> **\_\_最后**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//终止代码<br/>
> }

## <a name="grammar"></a>语法

try-finally-statement:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **\_\_** \_**finally**复合*语句*\_

**Try-catch**语句是 C 和C++语言的 Microsoft 扩展，使目标应用程序能够在代码块的执行被中断时保证清理代码的执行。 清理包括多个任务，如释放内存、关闭文件和释放文件句柄。 对于有多个位置的例程，使用**try finally**语句对于可能导致例程提前返回的错误，特别有用。

有关相关信息和代码示例，请参阅[try-Except 语句](../cpp/try-except-statement.md)。 有关结构化异常处理的一般详细信息，请参阅[结构化异常处理](../cpp/structured-exception-handling-c-cpp.md)。 有关通过C++/cli 处理托管应用程序中的异常的详细信息，请参阅[/Clr 下的异常处理](../extensions/exception-handling-cpp-component-extensions.md)。

> [!NOTE]
> 结构化异常处理适用于 Win32 中的 C 和 C++ 源文件。 但是，这不是专门为 C++ 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理更为灵活，因此它可以处理任何类型的异常。 对于C++程序，建议使用C++异常处理机制（[try、catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)语句）。

**__Try**子句后的复合语句是受保护的部分。 **__Finally**子句后的复合语句是终止处理程序。 处理程序指定了在退出受保护部分时执行的一组操作，无论受保护部分是因异常（不正常终止）还是因标准失效（正常终止）导致退出。

Control 通过简单的顺序执行（贯穿）到达 **__try**语句。 当控件进入 **__try**时，其关联的处理程序将变为活动状态。 如果控制流到达 try 块的末尾，执行将继续，如下所示：

1. 调用终止处理程序。

1. 当终止处理程序完成时，执行将在 **__finally**语句后继续。 无论受保护的部分如何结束（例如，通过受保护的主体或**返回**语句的**goto** ），都将在控制流移出受保护部分*之前*执行终止处理程序。

   **__Finally**语句不会阻止搜索适当的异常处理程序。

如果 **__try**块中发生异常，则操作系统必须查找异常的处理程序，否则程序将失败。 如果找到处理程序，则将执行所有 **__finally**块并在处理程序中恢复执行。

例如，假设一个函数调用系列将函数 A 链接到函数 D，如下图所示。 每个函数均有一个终止处理程序。 如果异常在函数 D 中引发并在函数 A 中得到处理，则当系统展开堆栈时，按以下顺序调用终止处理程序：D、C、B。

![终止&#45;处理程序执行顺序](../cpp/media/vc38cx1.gif "终止&#45;处理程序执行顺序") <br/>
终止处理程序执行顺序

> [!NOTE]
> Try-finally 的行为不同于支持**最终**使用的其他一些语言，如C#。  单个 **__try**可以同时具有 **__finally**和 **__except**。  如果同时使用二者，则外部 try-except 语句必须包含内部 try-finally 语句。  指定何时执行每个块的规则也有所不同。

为了与早期版本兼容， **_try**、 **_finally**和 **_leave**是 **__try**、 **__finally**和 **__leave**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="the-__leave-keyword"></a>__leave 关键字

**__Leave**关键字仅在**try finally**语句的受保护部分中有效，其作用是跳转到受保护部分的结尾。 执行将在终止处理程序中的第一个语句处继续。

**Goto**语句还可以跳过受保护的部分，但会降低性能，因为它会调用堆栈展开。 **__Leave**语句的效率更高，因为它不会导致堆栈展开。

## <a name="abnormal-termination"></a>异常终止

使用[longjmp](../c-runtime-library/reference/longjmp.md)运行时函数退出**try-catch**语句被视为异常终止。 跳转到 **__try**语句是非法的，但要跳出该语句是合法的。 必须运行在出发点之间处于活动状态的所有 **__finally**语句（ **__try**块的正常终止）和目标（处理异常的 **__except**块）。 这称为本地展开。

如果出于任何原因提前终止了**try**块，包括跳出块，系统会在展开堆栈的过程中执行关联的**finally**块。 在这种情况下，如果从**finally**块内调用， [AbnormalTermination](/windows/win32/Debug/abnormaltermination)函数将返回**true** ;否则，返回**false**。

如果在执行**try finally**语句的过程中终止进程，则不会调用终止处理程序。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[编写终止处理程序](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[终止处理程序语法](/windows/win32/Debug/termination-handler-syntax)