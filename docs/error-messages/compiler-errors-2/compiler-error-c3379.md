---
title: 编译器错误 C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 9d99214f3ad7e7db1edc215d94c98e9cf9ec4ca2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742894"
---
# <a name="compiler-error-c3379"></a>编译器错误 C3379

"class"：嵌套类不能将程序集访问说明符作为声明的一部分

当应用于托管类型（如类或结构）时， [public](../../cpp/public-cpp.md)和[private](../../cpp/private-cpp.md)关键字指示是否通过程序集元数据公开此类。 `public` 或 `private` 不能应用于嵌套类，这将继承封闭类的程序集访问权限。

与[/clr](../../build/reference/clr-common-language-runtime-compilation.md)一起使用时，`ref` 和 `value` 关键字指示类是托管的（请参阅[类和结构](../../extensions/classes-and-structs-cpp-component-extensions.md)）。

下面的示例生成 C3379：

```cpp
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```
