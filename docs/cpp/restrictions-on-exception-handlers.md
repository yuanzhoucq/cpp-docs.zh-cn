---
title: 对于异常处理程序的限制
ms.date: 11/04/2016
helpviewer_keywords:
- restrictions, exception handlers
- exception handling [C++], exception handlers
ms.assetid: 31d63524-0e8c-419f-b87c-061f4c0ea470
ms.openlocfilehash: 7d5bf20da61f4b9f5012b7f2aab932dfc904c302
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573982"
---
# <a name="restrictions-on-exception-handlers"></a>对于异常处理程序的限制

在代码中使用异常处理程序的主要限制是，您不能使用**goto**语句跳转到 **__try**语句块。 相反，您必须通过常规控制流进入此语句块。 您可以带跳转 **__try**语句块和嵌套异常处理程序，您选择。

## <a name="see-also"></a>请参阅

[编写异常处理程序](../cpp/writing-an-exception-handler.md)<br/>
[结构化异常处理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)