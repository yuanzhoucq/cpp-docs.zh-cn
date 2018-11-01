---
title: 编译器警告（等级 4）C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: 743069c0ed3103a2ed8d459def65083146b971e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496998"
---
# <a name="compiler-warning-level-4-c4487"></a>编译器警告（等级 4）C4487

derived_class_function： 匹配继承非虚方法 base_class_function 但不是显式标记为 new

在派生类中的函数具有与非虚拟基类函数相同的签名。 C4487 提醒您在派生的类函数不重写基类函数。 显式标记为派生的类函数`new`若要解决此警告。

有关详细信息，请参阅[新 (新 vtable 中的槽）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C4487。

```
// C4487.cpp
// compile with: /W4 /clr
using namespace System;
public ref struct B {
   void f() { Console::WriteLine("in B::f"); }
   void g() { Console::WriteLine("in B::g"); }
};

public ref struct D : B {
   void f() { Console::WriteLine("in D::f"); }   // C4487
   void g() new { Console::WriteLine("in D::g"); }   // OK
};

int main() {
   B ^ a = gcnew D;
   // will call base class functions
   a->f();
   a->g();
}
```