---
title: "编译器警告（等级 1）C4114 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4114"
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4114
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

多次使用同一类型限定符  
  
 类型声明或定义多次使用某类型限定符（**const**、`volatile`、**signed** 或 `unsigned`）。  这导致 Microsoft 扩展 \(\/Ze\) 下的警告和 ANSI 兼容性 \(\/Za\) 下的错误。  
  
 下面的示例生成 C4114：  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 下面的示例生成 C4114：  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```