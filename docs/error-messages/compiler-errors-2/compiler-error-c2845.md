---
title: "编译器错误 C2845 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2845"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2845"
ms.assetid: 31b28ee9-978f-403b-94d8-dbaacd24cce0
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2845
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 此类型上不允许使用指针算法  
  
 不能递增指向托管类的指针。  
  
 **C\+\+ 托管扩展**  
  
 不能递增指向 [\_\_gc](../../misc/gc.md) 类的指针。同时，string 运算符只对 **\/clr**（不是 **\/clr:oldSyntax**）有效。  
  
 下面的示例生成 C2845：  
  
```  
// C2845b.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__gc class X {};  
  
int main() {  
   X *pX = new X;  
   pX++;   // C2845  
  
   String * a = new String("abc");  
   String * b = new String("def");  
   Console::WriteLine(a + b);   // C2845 not with /clr:oldSyntax  
}  
```