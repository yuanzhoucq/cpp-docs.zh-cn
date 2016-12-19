---
title: "使用 NMAKE 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宏, NMAKE"
  - "NMAKE 宏, using"
ms.assetid: 95c87fbc-76e6-48c0-8536-9bfe179f328e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 NMAKE 宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用宏，请将它的名称括在括号内并在前面加一个美元符号 \($\)，如下所示。  
  
## 语法  
  
```  
$(macroname)  
```  
  
## 备注  
 不允许有空格。  如果 *macroname* 是单个字符，可以不使用括号。  定义字符串替换 $\(*macroname*\)；未定义的宏由空字符串替换。  
  
## 您想进一步了解什么？  
 [宏替换](../build/macro-substitution.md)  
  
## 请参阅  
 [宏和 NMAKE](../build/macros-and-nmake.md)