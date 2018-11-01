---
title: 编译器错误 C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: 998067e9af178c1898c3443c4e84da965c22fa81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576899"
---
# <a name="compiler-error-c2229"></a>编译器错误 C2229

类型 identifier 具有非法的零大小的数组

结构或位域的成员包含不是最后一个成员的大小为零的数组。

由于你可以有零大小的数组作为结构的最后一个成员，必须指定其大小，当分配结构。

如果零大小的数组不是该结构的最后一个成员，编译器无法计算剩余的字段的偏移量。

下面的示例生成 C2229:

```
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```