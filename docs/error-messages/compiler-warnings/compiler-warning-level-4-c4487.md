---
title: 编译器警告（等级 4）C4487
ms.date: 11/04/2016
f1_keywords:
- C4487
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
ms.openlocfilehash: b83b3b33727db300367156e10f902aaa6ff4bfdb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990772"
---
# <a name="compiler-warning-level-4-c4487"></a>编译器警告（等级 4）C4487

"derived_class_function"：匹配继承的非虚方法 "base_class_function"，但没有显式标记为 "new"

派生类中的函数与非虚拟基类函数具有相同的签名。 C4487 提醒你派生类函数不会重写基类函数。 将派生类函数显式标记为 `new` 以解决此警告。

有关详细信息，请参阅[new （vtable 中的新槽）](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C4487。

```cpp
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
