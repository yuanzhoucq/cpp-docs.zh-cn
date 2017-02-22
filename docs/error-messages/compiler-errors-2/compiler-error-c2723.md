---
title: "编译器错误 C2723 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2723"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2723"
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2723
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“函数”：“specifier”说明符在函数定义上非法  
  
 说明符不能与类声明外部的函数定义同时出现。  仅能对类声明内的成员函数声明指定 `virtual` 说明符。  
  
 下面的示例生成 C2723 并显示如何修复它：  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```