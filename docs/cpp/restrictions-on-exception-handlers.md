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

The principal limitation to using exception handlers in code is that you cannot use a **goto** statement to jump into a **__try** statement block. 相反，您必须通过常规控制流进入此语句块。 You can jump out of a **__try** statement block and nest exception handlers as you choose.

## <a name="see-also"></a>请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)