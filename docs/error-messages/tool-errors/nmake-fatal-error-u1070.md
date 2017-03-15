---
title: "NMAKE 错误 U1070 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1070"
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 错误 U1070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

宏定义“macroname”中的循环  
  
 给定的宏定义包含其定义已包含给定宏的宏。  循环宏定义无效。  
  
## 示例  
 下列宏定义  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 产生以下错误：  
  
```  
cycle in macro definition 'TWO'  
```