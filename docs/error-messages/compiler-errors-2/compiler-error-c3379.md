---
title: "编译器错误 C3379 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e6fa111a525d81c418d3285c05af86b700e8cb08
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3379"></a>编译器错误 C3379
class： 嵌套的类不能将作为其声明的一部分的程序集访问说明符  
  
 当应用于托管类型，例如类或结构，[公共](../../cpp/public-cpp.md)和[私有](../../cpp/private-cpp.md)关键字指示是否将程序集元数据通过公开的类。 `public`或`private`不能应用于嵌套类，该类将继承封闭类的程序集访问权限。  
  
 如果用于[/clr](../../build/reference/clr-common-language-runtime-compilation.md)、`ref`和`value`关键字指示该类受托管 (请参阅[类和结构](../../windows/classes-and-structs-cpp-component-extensions.md))。  
  
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

