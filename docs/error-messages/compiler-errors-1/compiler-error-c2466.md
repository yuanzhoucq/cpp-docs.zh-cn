---
title: 编译器错误 C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: 516f9b024947e0100a753e4e010a5b51b1fb24a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230524"
---
# <a name="compiler-error-c2466"></a>编译器错误 C2466

不能分配常量大小为 0 的数组

分配或使用大小为零声明数组时。 数组大小的常量表达式必须是大于零的整数。 与零个下标的数组声明是合法的仅对类、 结构或联合成员的和仅可与 Microsoft 扩展 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。

下面的示例生成 C2466:

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```