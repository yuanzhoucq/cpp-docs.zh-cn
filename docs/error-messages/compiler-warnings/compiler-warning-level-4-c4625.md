---
title: "编译器警告（等级 4）C4625 | Microsoft Docs"
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
  - "C4625"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4625"
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4625
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“derived class”: 未能生成复制构造函数，因为基类复制构造函数不可访问或已被删除  
  
 复制构造函数已删除或在基类中不可访问，因此并未为派生类生成。  复制此类型的对象的任何尝试都将导致编译器错误。  
  
 默认情况下，此警告处于关闭状态。  请参阅[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)了解详细信息。  
  
## 示例  
 下面的示例生成 C4625，并演示如何修复此错误。  
  
```  
// C4625.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4625)  
  
struct A {  
   A() {}  
  
private:  
   A(const A&) {}  
};  
  
struct C : private virtual A {};  
struct B :  C {};   // C4625 no copy constructor  
  
struct D : A {};  
struct E :  D {};   // OK  
```