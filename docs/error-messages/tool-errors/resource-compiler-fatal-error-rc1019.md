---
title: "资源编译器错误 RC1019 | Microsoft Docs"
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
  - "RC1019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1019"
ms.assetid: 432fff44-04a9-4e13-91c6-870df6f0b4e4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RC1019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的“\#else”  
  
 `#else` 指令没有出现在 `#if`、**\#ifdef** 或 **\#ifndef** 构造中。  
  
 确保在此语句前有一个生效的 `#if`、**\#ifdef** 或 **\#ifndef** 语句。