---
title: "编译器错误 C3637 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3637"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3637"
ms.assetid: 72391377-8519-43d9-870a-73a6423deb74
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3637
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 友元函数定义不能是函数类型的专用化  
  
 为模板或泛型错误地定义了友元函数。  
  
 下面的示例生成 C3637：  
  
```  
// C3637.cpp  
template <class T>  
void f();  
  
struct S {  
   friend void f<int>() {}   // C3637  
};  
```  
  
 可能的解决方案：  
  
```  
// C3637b.cpp  
// compile with: /c  
template <class T>  
void f();  
  
struct S {  
   friend void f() {}  
};  
```  
  
 使用以下泛型时也可能发生 C3637 错误：  
  
```  
// C3637c.cpp  
// compile with: /clr  
  
generic <class T>  
void gf();  
  
struct S {  
   friend void gf<int>() {}   // C3637  
};  
```  
  
 可能的解决方案：  
  
```  
// C3637d.cpp  
// compile with: /clr /c  
generic <class T>  
void gf();  
  
struct S {  
   friend void gf() {}  
};  
```