---
title: 编译器错误 C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 9fe9b765af72a8864e3e899cafcf648a9facb67e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528115"
---
# <a name="compiler-error-c2289"></a>编译器错误 C2289

多次使用同一类型限定符

类型声明或定义多次使用类型限定符（`const`、 `volatile`、 `signed`或 `unsigned`），从而导致 ANSI 兼容性错误 (**/Za**)。

下面的示例生成 C2286：

```
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```