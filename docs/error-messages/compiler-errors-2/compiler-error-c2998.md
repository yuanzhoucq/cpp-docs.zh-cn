---
title: "编译器错误 C2998 | Microsoft Docs"
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
  - "C2998"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2998"
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2998
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：不能是模板定义  
  
 编译器无法处理模板定义中使用的语法。  
  
 下面的示例生成 C2998：  
  
```  
// C2998.cpp // compile with: /c template <class T> int x = 1018; // C2998  
```