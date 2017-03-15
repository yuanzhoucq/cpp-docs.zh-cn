---
title: "编译器错误 C2942 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2942"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2942"
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2942
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：type\-class\-id 重新定义为函数的形参  
  
 不能将泛型或模板类用作形参。 不能直接将参数传递到泛型或模板类的构造函数。  
  
 下面的示例生成 C2942：  
  
```  
  
// C2942.cpp // compile with: /c template<class T> struct TC {}; void f(int TC<int>) {}   // C2942 // OK struct TC2 {}; void f(TC2 i) {}  
```  
  
 使用泛型时也可能发生 C2942：  
  
```  
// C2942b.cpp // compile with: /clr /c generic<class T> ref struct GC {}; void f(int GC<int>) {}   // C2942 ref struct GC2 { }; void f(int GC2) {}  
```