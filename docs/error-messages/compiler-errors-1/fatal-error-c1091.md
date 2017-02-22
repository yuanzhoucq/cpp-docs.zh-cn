---
title: "错误 C1091 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1091"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1091"
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 错误 C1091
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译器限制：字符串长度超过“length”个字节  
  
 字符串常量超过当前的字符串长度限制。  
  
 你可能希望将静态字符串拆分为两个（或更多）变量，以及使用 [strcpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) 在声明或在运行时联接结果。