---
title: "编译器错误 C2936 | Microsoft Docs"
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
  - "C2936"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2936"
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2936
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：type\-class\-id 被重新定义为了全局数据变量  
  
 不能将泛型或模板类用作全局数据变量。  
  
 如果大括号匹配不正确，则可能导致此错误。  
  
 下面的示例生成 C2936：  
  
```  
// C2936.cpp // compile with: /c template<class T> struct TC { }; int TC<int>;   // C2936 // OK struct TC2 { }; int TC2;  
```  
  
 使用泛型时，也可能会生成 C2936：  
  
```  
// C2936b.cpp // compile with: /clr /c generic<class T> ref struct GC {}; int GC<int>;   // C2936 // OK ref struct GC2 {}; int GC2;  
```