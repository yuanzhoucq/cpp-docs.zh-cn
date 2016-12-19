---
title: "编译器错误 C2932 | Microsoft Docs"
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
  - "C2932"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2932"
ms.assetid: c28e88d9-e654-4367-bfb4-13c780bca9bd
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2932
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：type\-class\-id 重新定义为“identifier”的数据成员  
  
 不能将泛型或模板类用作数据成员。  
  
 以下示例生成 C2932：  
  
```  
// C2932.cpp // compile with: /c template<class T> struct TC {}; struct MyStruct { int TC<int>;   // C2932 int TC;   // OK };  
```  
  
 使用泛型时也可能发生 C2932：  
  
```  
// C2932b.cpp // compile with: /clr /c generic<class T> ref struct GC {}; struct MyStruct { int GC<int>;   // C2932 int GC;   // OK };  
```