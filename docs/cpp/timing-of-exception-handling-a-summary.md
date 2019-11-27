---
title: 异常处理的计时：摘要
ms.date: 05/07/2019
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 870606c3661df3654581760214e48ef2bdfb1987
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246332"
---
# <a name="timing-of-exception-handling-a-summary"></a>异常处理的计时：摘要

不管 **__try**语句块的终止方式如何，都将执行终止处理程序。 导致包括跳出 **__try**块、将控制转移到块的 `longjmp` 语句，并由于异常处理而展开堆栈。

> [!NOTE]
>  Microsoft C++编译器支持两种形式的 `setjmp` 和 `longjmp` 语句。 快速版本会跳过终止处理，但更高效。 若要使用此版本，请将文件包括 \<setjmp >。 另一个版本支持上一段中所述的终止处理。 若要使用此版本，请包含文件 \<setjmpex.h >。 快速版本的性能提升取决于硬件配置。

在执行任何其他代码前，操作系统将以适当的顺序执行所有终止处理程序，包括异常处理程序的主体。

当中断的原因是异常时，系统在决定要终止的内容前必须先执行一个或多个异常处理程序的筛选器部分。 事件的顺序如下：

1. 引发异常。

1. 系统查看活动异常处理程序的层次结构并执行具有最高优先级的处理程序的筛选器；从块和函数调用来看，这是最新安装且嵌套最深的异常处理程序。

1. 如果此筛选器传递控制权（返回 0），过程将继续，直到发现筛选器不传递控制权。

1. 如果此筛选器返回-1，则执行将在引发异常的位置继续，而不会发生终止。

1. 如果筛选器返回 1，则发生以下事件：

   - 系统展开堆栈，以清除当前执行的代码之间的所有堆栈帧（引发异常处）以及包含获取控制权的异常处理程序的堆栈帧。

   - 当堆栈展开时，堆栈上的所有终止处理程序都将执行。

   - 执行异常处理程序本身。

   - 控制权将交给此异常处理程序末尾后的代码行。

## <a name="see-also"></a>另请参阅

[编写终止处理程序](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)