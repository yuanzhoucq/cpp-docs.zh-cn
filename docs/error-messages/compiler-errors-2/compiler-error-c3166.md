---
title: "编译器错误 C3166 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3166"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3166"
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3166
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“pointer”: 不能将指向内部 \_\_gc 指针的指针声明为“type”的成员  
  
 编译器发现了无效的指针声明（指向 [\_\_gc](../../misc/gc.md) 指针的 [\_\_nogc](../../misc/nogc.md) 指针）。  在将来的版本中可能支持此语法。  
  
 只有使用 **\/clr:oldSyntax** 才会出现 C3166 错误。  
  
 下面的示例生成 C3166：  
  
```  
// C3166.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc struct G {  
   int __gc* __nogc* p;   // C3166  
};  
  
public __gc class H {  
public:  
   Int32 __gc* __nogc* p;   // C3166  
};  
  
public __value struct I {  
   int __gc* __nogc* p;   // C3166  
};  
  
public __value class J {  
public:  
   int __gc* __nogc* p;   // C3166  
};  
  
int main() {  
   G* pG = new G;  
   H* pH = new H;  
}  
```