---
title: "编译器警告（等级 4）C4152 | Microsoft Docs"
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
  - "C4152"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4152"
ms.assetid: 6025ab70-d7cf-4730-913a-3ca0b1186a3a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4152
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非标准扩展, 表达式中的函数\/数据指针转换  
  
 在函数指针与数据指针之间转换。 在 Microsoft 扩展 \(\/Ze\) 下允许此类转换，但在 ANSI C 下则不允许。