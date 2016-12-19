---
title: "表达式计算器错误 CXX0015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0015"
  - "CXX0015"
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 表达式计算器错误 CXX0015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表达式太复杂\(堆栈溢出\)  
  
 输入的表达式对于 C 表达式计算器可用的存储空间太复杂或嵌套太深。  
  
 溢出通常因挂起的计算太多而发生。  
  
 重新排列表达式，使得表达式的每一个部分在被遇到时就能立刻计算，而不必等到表达式的其他部分计算完后再计算。  
  
 将表达式断开为多个命令。  
  
 该错误与 CAN0015 相同。