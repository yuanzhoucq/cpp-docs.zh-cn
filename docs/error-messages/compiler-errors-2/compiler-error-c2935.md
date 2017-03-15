---
title: "编译器错误 C2935 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2935"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2935"
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2935
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：type\-class\-id 重新定义为全局函数  
  
 不能将泛型或模板类用作全局函数。  
  
 如果大括号匹配不正确，则可能导致此错误。  
  
 以下示例生成 C2935：  
  
```  
// C2935.cpp // compile with: /c template<class T> struct TC {}; void TC<int>() {}   // C2935 // OK struct TC2 {}; void TC2() {}  
```  
  
 使用泛型时也可能发生 C2935：  
  
```  
// C2935b.cpp // compile with: /clr /c generic<class T> ref struct GC { }; void GC<int>() {}   // C2935 void GC() {}   // OK  
```