---
title: "资源编译器错误 RC1018 | Microsoft Docs"
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
  - "RC1018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1018"
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RC1018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的“\#elif”  
  
 `#elif` 指令没有出现在 `#if`、**\#ifdef** 或 **\#ifndef** 构造中。  
  
 确保在此语句前有一个生效的 `#if`、**\#ifdef** 或 **\#ifndef** 语句。