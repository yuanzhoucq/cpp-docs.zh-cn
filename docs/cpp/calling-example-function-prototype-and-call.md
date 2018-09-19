---
title: 调用示例： 函数原型和调用 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04e681560854be4c93b1c93786d38771c07244ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099572"
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