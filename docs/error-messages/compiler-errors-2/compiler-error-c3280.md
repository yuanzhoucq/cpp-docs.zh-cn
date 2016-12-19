---
title: "编译器错误 C3280 | Microsoft Docs"
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
  - "C3280"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3280"
ms.assetid: 86dc5bbc-8818-4786-a728-9334268d308b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3280
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 无法将托管类型的成员函数编译成非托管函数  
  
 托管的类成员函数不能编译为非托管函数。  
  
 以下示例生成 C3280：  
  
```  
// C3280_2.cpp // compile with: /clr ref struct A { void func(); }; #pragma managed(push,off) void A::func()   // C3280 { } #pragma managed(pop)  
```  
  
 以下示例生成 C3280：  
  
```  
// C3280.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> __gc struct A { void func(); }; #pragma managed(push,off) void A::func()   // C3280 { } #pragma managed(pop)  
```