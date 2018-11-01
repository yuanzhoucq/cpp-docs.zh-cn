---
title: 编译器警告（等级 2）C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: e9ad30f60260893130beed921aab811c894868cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528145"
---
# <a name="compiler-warning-level-2-c4307"></a>编译器警告（等级 2）C4307

operator： 整型常量溢出

导致溢出为其分配的空间的整数常量的表达式中使用的运算符。 您可能需要使用更大的类型的常量。 一个**带符号整型**包含较小的值比`unsigned int`因为**带符号整型**使用一个位来表示符号。

下面的示例生成 C4307:

```
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```