---
title: 对于异常处理程序的限制
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 1f80cb1574cbfef0783c7e55dcd198dfb822f566
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225899"
---
# <a name="restrictions-on-exception-handlers"></a>对于异常处理程序的限制

在代码中使用异常处理程序的主要限制是不能使用 **`goto`** 语句跳转到 **__try**的语句块。 相反，您必须通过常规控制流进入此语句块。 你可以跳过 **__try**语句块并在选择时嵌套异常处理程序。

## <a name="see-also"></a>另请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
