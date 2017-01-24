---
title: "编译器错误 C3228 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3228"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3228"
ms.assetid: 9015adf9-17b0-4312-b4a7-c1f33e4126f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3228
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：“param”的泛型类型实参不能是“type”，它必须是值类型或句柄类型  
  
 作为泛型类型实参传递了不正确的类型。  
  
 下面的示例生成 C3228：  
  
```  
// C3228.cpp // compile with: /clr class A {}; value class B {}; generic <class T> void Test() {} ref class C { public: generic <class T> static void f() {} }; int main() { C::f<A>();   // C3228 C::f<B>();   // OK Test<C>();   // C3228 Test<C ^>();   // OK }  
```