---
title: 编译器警告（等级 2）C4356
ms.date: 11/04/2016
f1_keywords:
- C4356
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
ms.openlocfilehash: ffcf0098799b893f83e331b3b4cc602e1b538b1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161823"
---
# <a name="compiler-warning-level-2-c4356"></a>编译器警告（等级 2）C4356

"member"：静态数据成员不能通过派生类初始化

静态数据成员的初始化格式不正确。 编译器接受了初始化。 若要避免出现此警告，请通过基类初始化成员。

使用[警告](../../preprocessor/warning.md)杂注来禁止显示此警告。

下面的示例生成 C4356：

```cpp
// C4356.cpp
// compile with: /W2 /EHsc
#include <iostream>

template <class T>
class C {
   static int n;
};

class D : C<int> {};

int D::n = 0; // C4356
// try the following line instead
// int C<int>::n = 0;

class A {
public:
   static int n;
};

class B : public A {};

int B::n = 10;   // C4356
// try the following line instead
// int A::n = 99;

int main() {
   using namespace std;
   cout << B::n << endl;
}
```
