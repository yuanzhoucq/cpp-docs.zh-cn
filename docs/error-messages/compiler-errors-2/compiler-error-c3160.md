---
title: "编译器错误 C3160 | Microsoft Docs"
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
  - "C3160"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3160"
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3160
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“pointer”: 托管或 WinRT 类的数据成员不能具有此类型  
  
 内部垃圾回收指针可能会指向托管或 WinRT 类的内部。  因为它们比整个对象的指针慢，并且需要垃圾回收器进行特殊处理，因此你不能将内部托管的指针声明为类的成员。  
  
 以下示例生成 C3160：  
  
```  
// C3160.cpp  
// compile with: /clr  
ref struct A {  
   // cannot create interior pointers inside a class  
   interior_ptr<int> pg;   // C3160  
   int g;   // OK  
   int* pg2;   // OK  
};  
  
int main() {  
   interior_ptr<int> pg2;   // OK  
}  
```  
  
 **C\+\+ 托管扩展**  
  
 以下示例生成 C3160：  
  
```  
// C3160b.cpp  
// compile with: /clr:oldSyntax  
  
__gc struct A {  
   // cannot create interior pointers inside a class  
   int __gc* pg; // C3160  
   int g;   // OK  
   int __nogc *pg2;   // OK  
};  
  
int main() {  
   int __gc* pg2;   // OK  
}  
```