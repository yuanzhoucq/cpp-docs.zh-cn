---
title: 编译器错误 C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: aba4de518b9296fadc4746540e4e738c74908617
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743817"
---
# <a name="compiler-error-c2466"></a>编译器错误 C2466

不能分配常量大小为0的数组

使用大小0来分配或声明数组。 数组大小的常量表达式必须是大于零的整数。 带有零下标的数组声明仅对类、结构或联合成员有效，且仅适用于 Microsoft 扩展（[/ze](../../build/reference/za-ze-disable-language-extensions.md)）。

下面的示例生成 C2466：

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
