---
title: "编译器错误 C3553 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3553"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3553"
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# 编译器错误 C3553
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

decltype 应为表达式而不是类型  
  
 `decltype()` 关键字要求使用表达式作为参数，而非类型的名称。 例如，以下代码片段中的最后一个语句生成错误 C3553。  
  
 `int x = 0;`  
  
 `decltype(x+1);`  
  
 `decltype(int); // C3553`