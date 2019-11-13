---
title: 编译器警告（等级2） C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: b5566bca22c328328a49e82268b96e8ec0fedc95
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052058"
---
# <a name="compiler-warning-level-2-c4307"></a>编译器警告（等级2） C4307

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