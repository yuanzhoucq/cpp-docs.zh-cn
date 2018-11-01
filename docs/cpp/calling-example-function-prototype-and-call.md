---
title: 调用示例：函数原型和调用
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508171"
---
# <a name="calling-example-function-prototype-and-call"></a>调用示例：函数原型和调用

## <a name="microsoft-specific"></a>Microsoft 专用

以下示例显示了使用各种调用约定执行函数调用的结果。

此示例基于以下函数主干。 将 `calltype` 替换为适当的调用约定。

```
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

有关详细信息，请参阅[调用结果示例](../cpp/results-of-calling-example.md)。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[调用约定](../cpp/calling-conventions.md)