---
title: "编译器错误 C2990 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2990"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2990"
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C2990
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 非类类型已声明为类类型  
  
 非泛型或模板类重定义了泛型或模板类。  检查头文件中是否有冲突。  
  
 下面的示例生成 C2990：  
  
```  
// C2990.cpp  
// compile with: /c  
template <class T>  
class C{};  
class C{};   // C2990  
```  
  
 使用泛型时也可能发生 C2990：  
  
```  
// C2990b.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC;  
  
ref struct GC {};   // C2990  
```  
  
 Visual C\+\+ 编译器中对 Visual C\+\+ 2005 的重大更改也可能导致 C2990；对于模板规范，该编译器现在要求相同类型的多个声明应相同。  
  
 下面的示例生成 C2990：  
  
```  
// C2990c.cpp  
// compile with: /c  
template<class T>  
class A;  
  
template<class T>  
struct A2 {  
   friend class A;   // C2990  
};  
  
// OK  
template<class T>  
struct B {  
   template<class T>  
   friend class A;  
};  
```