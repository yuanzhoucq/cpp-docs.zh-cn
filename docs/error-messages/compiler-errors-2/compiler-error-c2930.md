---
title: "编译器错误 C2930 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2930"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2930"
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2930
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：type\-class\-id 被重新定义为 “enum identifier” 的枚举器  
  
 不能将泛型或模板类用作枚举的成员。  
  
 如果大括号匹配不正确，则可能导致此错误。  
  
 以下示例生成 C2930：  
  
```  
// C2930.cpp // compile with: /c template<class T> class x{}; enum SomeEnum { x };   // C2930 class y{}; enum SomeEnum { y };  
```  
  
 使用泛型时，也可能发生 C2930：  
  
```  
// C2930c.cpp // compile with: /clr /c generic<class T> ref struct GC {}; enum SomeEnum { GC };   // C2930 ref struct GC2 {}; enum SomeEnum2 { GC2 };  
```