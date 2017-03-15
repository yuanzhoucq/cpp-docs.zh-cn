---
title: "编译器警告（等级 1）C4627 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4627"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4627"
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器警告（等级 1）C4627
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“\<identifier\>”：在查找预编译头使用时跳过  
  
 当搜索使用预编译头的位置时，编译器遇到 *\<identifier\>* 包含文件的 `#include` 指令。 如果预编译头尚未包含 *\<identifier\>* 包含文件，编译器将忽略 `#include` 指令，但发出警告 **C4627**。  
  
## 请参阅  
 [创建预编译的头文件](../../build/reference/creating-precompiled-header-files.md)