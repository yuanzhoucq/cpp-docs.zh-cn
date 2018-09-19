---
title: 编译器错误 C3379 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f90a4ccc17e63c21d4b6fb26e607450849f27b48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109322"
---
# <a name="compiler-error-c3379"></a>编译器错误 C3379

class： 嵌套的类不能将程序集访问说明符作为其声明的一部分

当应用于托管类型，例如类或结构，[公共](../../cpp/public-cpp.md)并[专用](../../cpp/private-cpp.md)关键字指示是否将程序集元数据通过公开的类。 `public` 或`private`不能应用于嵌套类，该类将继承封闭类的程序集访问权限。

与一起使用时[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，则`ref`并`value`关键字指示该类受托管 (请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md))。

下面的示例生成 C3379:

```
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
