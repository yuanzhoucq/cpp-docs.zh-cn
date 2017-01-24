---
title: "编译器错误 C2952 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2952"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2952"
ms.assetid: a40e18a2-d02c-4511-854f-6c6fd6789a1a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2952
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration”：类型声明缺少模板参数列表  
  
 模板声明格式不正确。  
  
 以下示例生成 C2952：  
  
```  
// C2952.cpp // compile with: /c template <class T> struct S { template <class T1> struct S1 { void f(); }; }; template <class T> void S<T>::S1<T>::f() {}   // C2952 // OK template <class T> template <class T1> void S<T>::S1<T1>::f() {}  
```  
  
 使用泛型时也可能发生 C2952：  
  
```  
// C2952b.cpp // compile with: /clr /c generic <class T> ref struct GC { generic <class T1> ref struct GC1 { void f(); }; }; generic <class T> void GC<T>::GC1<T>::f() {}   // C2952 // OK generic <class T> generic <class T1> void GC<T>::GC1<T1>::f() {}  
```