---
title: "编译器警告（等级 4）C4718 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4718"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4718"
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 4）C4718
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function call”：递归调用无副作用，正在删除  
  
 函数包含递归调用，但却没有副作用。 正在删除对此函数的调用。 不影响程序的正确性，而是影响其行为。 但保留该调用会导致运行时堆栈溢出异常，请删除该调用，从而排除这种可能性。