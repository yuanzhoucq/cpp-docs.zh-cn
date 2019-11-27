---
title: 对异常处理程序的限制
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 030d444443b3a6e3e2e0ac0e015619046a76d562
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245148"
---
# <a name="restrictions-on-exception-handlers"></a>对异常处理程序的限制

在代码中使用异常处理程序的主要限制是不能使用**goto**语句跳转到 **__try**的语句块。 相反，您必须通过常规控制流进入此语句块。 你可以跳过 **__try**语句块并在选择时嵌套异常处理程序。

## <a name="see-also"></a>另请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)