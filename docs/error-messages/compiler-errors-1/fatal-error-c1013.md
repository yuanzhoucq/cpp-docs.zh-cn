---
title: "错误 C1013 | Microsoft Docs"
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
  - "C1013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1013"
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制 : 左括号太多  
  
 表达式在单个表达式中包含太多级别的括号。 简化表达式，或将其分解为多个语句。  
  
 在 Visual C\+\+ 6.0 Service Pack 3 之前，单个表达式中嵌套括号的上限是 59 个。 目前，嵌套括号的上限是 256 个。