---
title: "编译器错误 C3398 | Microsoft Docs"
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
  - "C3398"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3398"
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3398
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”：无法从“function\_signature”转换为“function\_pointer”。 源表达式必须是函数符号  
  
 当使用 **\/clr** 进行编译时，如果未指定 [\_\_clrcall](../../cpp/clrcall.md) 调用约定，编译器将为每个函数生成两个入口点（地址）：一个本机入口点和一个托管入口点。  
  
 默认情况下，编译器返回本机入口点，但有些情况需要托管入口点（例如将地址分配给 `__clrcall` 函数指针时）。 为了使编译器能够在分配中可靠地选择托管入口点，右侧必须为函数符号。