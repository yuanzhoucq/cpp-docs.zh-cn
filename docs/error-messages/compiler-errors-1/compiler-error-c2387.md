---
title: "编译器错误 C2387 | Microsoft Docs"
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
  - "C2387"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2387"
ms.assetid: 6847b8e1-ffac-458d-ab88-0c92f72f2527
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2387
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 不明确的基类  
  
 编译器未能明确地解析函数调用，因为该函数存在于多个基类中。  
  
 若要消除此错误，可以从继承中移除基类之一，或者显式限定该函数调用。  
  
 下面的示例生成 C2387：  
  
```  
// C2387.cpp  
namespace N1 {  
   struct B {  
      virtual void f() {  
      }  
   };  
}  
  
namespace N2 {  
   struct B {  
      virtual void f() {  
      }  
   };  
}  
  
struct D : N1::B, N2::B {  
   virtual void f() {  
      B::f();   // C2387  
      // try the following line instead  
      // N1::B::f();  
   }  
};  
  
int main() {  
   D aD;  
   aD.f();  
}  
```