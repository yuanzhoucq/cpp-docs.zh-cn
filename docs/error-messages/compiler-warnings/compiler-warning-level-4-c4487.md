---
title: 编译器警告 （等级 C4487 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4487
dev_langs:
- C++
helpviewer_keywords:
- C4487
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffc1a25d362cad95f2aad43d626e4918955903f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46135836"
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