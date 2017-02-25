---
title: "编译器错误 C2914 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2914"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2914"
ms.assetid: fc6a0592-f53e-4f5a-88cb-780bbed4acf2
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2914
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 无法推导出类型参数，因为函数参数不明确  
  
 编译器无法确定要对泛型参数或模板参数使用的重载函数。  
  
 下面的示例生成 C2914：  
  
```  
// C2914.cpp  
// compile with: /c  
void f(int);  
void f(double);  
template<class T> void g(void (*) (T));  
void h() { g(f); }   // C2914  
// try the following line instead  
// void h() { g<int>(f); }  
```  
  
 使用以下泛型时也可能发生 C2914 错误。下面的示例生成 C2914：  
  
```  
// C2914b.cpp  
// compile with: /clr /c  
void f(int);  
void f(double);  
  
template<class T>   
void gf(void (*) (T));  
  
void h() { gf(f);}   // C2914  
// try the following line instead  
void h() { gf<int>(f); }  
```