---
title: "编译器错误 C2477 | Microsoft Docs"
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
  - "C2477"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2477"
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2477
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“成员”: 静态数据成员无法通过派生类初始化  
  
 模板类的静态数据成员已被错误初始化。  这是对早于 Visual Studio .NET 2003 的 Visual C\+\+ 编译器版本的重大更改，以便与 ISO C\+\+ 标准相符。  
  
 下面的示例生成 C2477：  
  
```  
// C2477.cpp  
// compile with: /Za /c  
template <class T>  
struct S {  
   static int n;  
};  
  
struct X {};  
struct A: S<X> {};  
  
int A::n = 0;   // C2477  
  
template<>  
int S<X>::n = 0;  
```