---
title: 对于终止处理程序的限制
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], limitations
- restrictions, termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
ms.openlocfilehash: 6c39407270037756c55dc42aed80e1d04616c9ee
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246385"
---
# <a name="restrictions-on-termination-handlers"></a>对于终止处理程序的限制

不能使用**goto**语句跳转到 **__try**语句块或 **__finally**语句块。 相反，您必须通过常规控制流进入此语句块。 （但是，您可以跳出 **__try**语句块。）此外，不能在 **__finally**块中嵌套异常处理程序或终止处理程序。

此外，终止处理程序中允许的某些类型的代码会生成有问题的结果，因此您应小心使用它们（如果要使用）。 一个是跳转到 **__finally**语句块的**goto**语句。 如果该块正在作为正常终止的一部分执行，则不会发生任何异常。 但如果系统正在展开堆栈，则该展开会停止，并且当前函数会获取控制权，就象异常终止不存在一样。

**__Finally**语句块内的**return**语句大致相同。 控制权将返回给包含终止处理程序的函数的直接调用方。 如果系统正在展开堆栈，此进程将暂停，如果没有引发过异常，则程序将继续执行。

## <a name="see-also"></a>另请参阅

[编写终止处理程序](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)