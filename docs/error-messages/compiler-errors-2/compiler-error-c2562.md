---
title: 编译器错误 C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: c665c4ed82fefaf0ee724defb8c205f86fc06dd0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435303"
---
# <a name="compiler-error-c2562"></a>编译器错误 C2562

identifier: void 函数返回值

该函数声明为`void`但返回一个值。

此错误可能引起错误的函数原型。

如果在函数声明中指定的返回类型，可能会修复此错误。

下面的示例生成 C2562:

```
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```