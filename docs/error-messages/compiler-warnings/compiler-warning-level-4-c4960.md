---
title: "编译器警告（等级 4）C4960 | Microsoft Docs"
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
  - "C4960"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4960"
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4960
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”太大，无法配置  
  
 当使用 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) 时，编译器检测到某个输入模块的函数具有的指令超过 65,535 条。 如此大的函数不可用于按配置进行的优化。  
  
 若要解决此警告，请减小该函数的大小。