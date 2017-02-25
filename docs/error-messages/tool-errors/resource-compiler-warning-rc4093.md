---
title: "资源编译器警告 RC4093 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC4093"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4093"
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器警告 RC4093
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非活动代码的字符常数中的非转义换行符  
  
 `#if`、`#elif`、**\#ifdef** 或 **\#ifndef** 预处理器指令的常数表达式计算结果为零，使得跟随的代码不活动。  在此非活动代码中，换行符出现在一组单引号或双引号中。  
  
 下一个双引号之前的所有文本都被看成了是在字符常数中。