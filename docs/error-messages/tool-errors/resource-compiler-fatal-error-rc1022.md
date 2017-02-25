---
title: "资源编译器错误 RC1022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1022"
ms.assetid: 30a0f3c7-08a8-4c40-b0de-46ee5feb789d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RC1022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

应输入“\#endif”  
  
 `#if`、**\#ifdef** 或 **\#ifndef** 指令没有以 `#endif` 指令终止。  
  
 确保在此语句前有一个生效的 `#if`、**\#ifdef** 或 **\#ifndef** 语句。