---
title: "编译器警告（等级 4）C4487 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4487"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4487"
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4487
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“derived\_class\_function”: 匹配继承的非虚方法“base\_class\_function”，但没有显式标记为“new”  
  
 派生类中的函数与非虚拟基类函数有相同的签名。  C4487 提醒您派生类函数不重写基类函数。  显式将派生类函数标记为 `new` 可消除此警告。  
  
 有关详细信息，请参阅[新的 \(在 vtable 的新槽\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)。  
  
## 示例  
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