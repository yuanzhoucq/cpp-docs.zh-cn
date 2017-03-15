---
title: "编译器错误 C2251 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2251"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2251"
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2251
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

命名空间“namespace”不具有成员“member”\- 是否要使用“member”？  
  
 编译器无法在指定的命名空间中找到标识符。  
  
 下面的示例生成 C2251：  
  
```  
// C2251.cpp // compile with: /c namespace A { namespace B { void f1(); } using namespace B; } void A::f1() {}   // C2251 void A::B::f1() {}   // OK  
```