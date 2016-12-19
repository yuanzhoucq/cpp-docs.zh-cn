---
title: "编译器警告（等级 1）C4153 | Microsoft Docs"
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
  - "C4153"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4153"
ms.assetid: 37a15754-9dba-470b-adda-c4b888064b3e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4153
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表达式中的函数\/数据指针转换  
  
 在函数指针与数据指针之间转换。 在 Microsoft 扩展 \(\/Ze\) 下允许此类转换，但在 ANSI C 下则不允许。