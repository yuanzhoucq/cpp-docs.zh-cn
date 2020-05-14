---
title: try-finally 语句 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 61a6a9edd9faaf8afb06bb7bfdc619cddde3e6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349605"
---
# <a name="try-finally-statement-c"></a>try-finally 语句 (C)

**Microsoft 专用**

`try-finally` 语句是 C 语言的 Microsoft 扩展，用于使应用程序能够在代码块的执行被中断时保证清理代码的执行。 清理包括多个任务，如释放内存、关闭文件和释放文件句柄。 `try-finally` 语句对此类例程特别有用：具有几个位置，在这些位置上执行了检查以找出可能导致例程提前返回内容的错误。

*try-finally-statement*: **__try**  *compound-statement*

**__finally**  *compound-statement*

`__try` 子句后的复合语句是受保护节。 `__finally` 子句后的复合语句是终止处理程序。 该处理程序将指定在退出受保护节时执行的一组操作，无论该受保护节是因异常（非正常终止）还是标准贯穿（正常终止）而退出。

控制权通过简单的顺序执行（贯穿）传递到 `__try` 语句。 当控制权交给 `__try` 语句时，其关联的处理程序将变为活动状态。 执行过程如下所示：

1. 执行受保护节。

1. 调用终止处理程序。

1. 当终止处理程序完成时，执行在 `__finally` 语句后继续。 无论受保护节如何结尾（例如，通过受保护体外部的 `goto` 语句或通过 `return` 语句），终止处理程序都在控制流移出受保护节之前执行。

`__leave` 关键字在 `try-finally` 语句块中有效。 `__leave` 的效果是跳转到 `try-finally` 块的末尾。 终止处理程序将立即执行。 尽管可使用 `goto` 语句来达到相同的结果，但 `goto` 语句会导致堆栈展开。 由于 `__leave` 语句不涉及堆栈展开，因此更有效。

使用 `try-finally` 语句或 `return` 运行时函数退出 `longjmp` 语句被视为异常终止。 跳转到 `__try` 语句是非法的，但跳出该语句是合法的。 必须运行在起点和终点之间处于活动状态的所有 `__finally` 语句。 这称为“局部展开”。

如果在执行 `try-finally` 语句时取消了进程，则不会调用终止处理程序。

> [!NOTE]
> 结构化异常处理适用于 C 和 C++ 源文件。 但是，这不是专门为 C++ 设计的。 您可通过使用 C++ 异常处理来确保提高代码的可移植性。 此外，C++ 异常处理机制灵活得多，因为它可以处理任何类型的异常。

> [!NOTE]
> 对于 C++ 程序，应使用 C++ 异常处理，而不是结构化异常处理。 有关详细信息，请参阅《C++ 语言参考》  中的[异常处理](../cpp/exception-handling-in-visual-cpp.md)。

请参阅 [try-except statement](../c-language/try-except-statement-c.md) 的示例以了解 `try-finally` 语句如何运行。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[try-finally 语句](../cpp/try-finally-statement.md)
