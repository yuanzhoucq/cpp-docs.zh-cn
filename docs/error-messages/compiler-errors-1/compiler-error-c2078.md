---
title: 编译器错误 C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: 514776c0feb12c46dea56dd8e85043345754a229
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756443"
---
# <a name="compiler-error-c2078"></a>编译器错误 C2078

初始值设定项太多

初始值设定项数超过要初始化的对象的数目。

如果内部大括号省略了初始值设定项列表，编译器可以推断出对对象和内部对象初始值设定项的正确分配。 完整的大括号还有助于消除歧义，从而获得正确分配。 由于对对象的初始值设定项的分配不明确，大括号不完整可能会导致 C2078。

下面的示例产生 C2078，并演示如何修复此错误：

```cpp
// C2078.cpp
// Compile by using: cl /c /W4 C2078.cpp
struct S {
   struct {
      int x, y;
   } z[2];
};

int main() {
   int d[2] = {1, 2, 3};   // C2078
   int e[2] = {1, 2};      // OK

   char a[] = {"a", "b"};  // C2078
   char *b[] = {"a", "b"}; // OK
   char c[] = {'a', 'b'};  // OK

   S s1{1, 2, 3, 4};       // OK
   S s2{{1, 2}, {3, 4}};   // C2078
   S s3{{1, 2, 3, 4}};     // OK
   S s4{{{1, 2}, {3, 4}}}; // OK
}
```
