---
title: "编译器警告（等级 1）C4544 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4544"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4544"
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4544
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration”：已忽略此模板声明中的默认模板参数  
  
 默认模板参数在错误的位置指定，并且已被忽略。  类模板的默认模板参数只能在类模板的声明或定义中指定，不能在类模板的成员上指定。  
  
 此示例生成 C4545，而下一个示例演示如何修复此问题：  
  
```  
// C4544.cpp  
// compile with: /W1 /LD  
template <class T>   
struct S  
{  
   template <class T1>   
      struct S1;  
   void f();  
};  
  
template <class T=int>  
template <class T1>  
struct S<T>::S1 {};   // C4544  
```  
  
 在此示例中，默认参数应用于类模板 `S`：  
  
```  
// C4544b.cpp  
// compile with: /LD  
template <class T = int>   
struct S  
{  
   template <class T1>   
      struct S1;  
   void f();  
};  
  
template <class T>  
template <class T1>  
struct S<T>::S1 {};  
```