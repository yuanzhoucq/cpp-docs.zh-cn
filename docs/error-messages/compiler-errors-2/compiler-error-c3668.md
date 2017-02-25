---
title: "编译器错误 C3668 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3668"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3668"
ms.assetid: 53a96698-bde4-4447-95b5-b5108291f60c
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C3668
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“method”: 包含重写说明符“override”的方法没有重写任何基类方法  
  
 函数尝试重写一个不存在的函数。  
  
 有关更多信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3668。  
  
```  
// C3668.cpp  
// compile with: /c  
__interface I {  
   void f(int);   // virtual by default  
};  
  
class J {  
public:  
   void g(int);  
   virtual void h(int);  
};  
  
struct R : I,J {  
   virtual void f() override {}   // C3668  
   virtual void f(int) override {}   // OK  
  
   virtual void g(int) override {}   // C3668  
   virtual void h(int) override {}   // OK  
};  
```