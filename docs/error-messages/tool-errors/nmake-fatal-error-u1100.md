---
title: "NMAKE 错误 U1100 | Microsoft Docs"
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
  - "U1100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1100"
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

宏“macroname”在批处理规则“rule”的上下文中非法  
  
 当批模式规则的命令块直接或间接地引用非$\< 的特殊文件宏时，NMAKE 生成该错误。  
  
 $\<是批模式规则唯一可以使用的宏。