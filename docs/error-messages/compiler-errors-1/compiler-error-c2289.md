---
title: "编译器错误 C2289 | Microsoft Docs"
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
  - "C2289"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2289"
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2289
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

多次使用同一类型限定符  
  
 类型声明或定义多次使用类型限定符（`const`、`volatile`、`signed` 或 `unsigned`），从而导致 ANSI 兼容性错误 \(**\/Za**\)。  
  
 下面的示例生成 C2286：  
  
```  
// C2289.cpp // compile with: /Za /c volatile volatile int i;   // C2289 volatile int j;   // OK  
```