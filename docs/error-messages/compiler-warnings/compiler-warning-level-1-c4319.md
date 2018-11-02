---
title: 编译器警告（等级 1）C4319
ms.date: 1/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 20b268bacd6e7e259e9b4fa1c9e98fa6fd353718
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599441"
---
# <a name="compiler-warning-level-1-c4319"></a>编译器警告（等级 1）C4319

> ~： 零扩展*type1*到*type2*更大的

结果**~** （按位求补） 运算符是无符号，然后零扩展转换为更大的类型时。

## <a name="example"></a>示例

在以下示例中，`~(a - 1)`是作为 32 位无符号 long 表达式计算，然后通过零扩展转换为 64 位。 这会导致意外的运算结果。

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
