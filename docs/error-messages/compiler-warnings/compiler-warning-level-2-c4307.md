---
title: 编译器警告（等级 2）C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: f6e06acaf43708d6c0da6d67531b6c4b9f202971
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161875"
---
# <a name="compiler-warning-level-2-c4307"></a>编译器警告（等级 2）C4307

"operator"：整型常量溢出

运算符用于导致整数常量溢出为其分配的空间的表达式。 可能需要对常数使用较大的类型。 **带符号的 int**保存的值比 `unsigned int` 更小，因为**有符号的 int**使用一位表示符号。

下面的示例生成 C4307：

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```
