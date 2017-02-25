---
title: "C 运行时错误 R6017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6017"
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C 运行时错误 R6017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

意外的多线程锁定错误  
  
 进程在尝试访问系统资源上的 C 运行时多线程锁定时接收到意外错误。  
  
 如果进程不小心改变了运行时堆数据，通常会发生该错误。  但该错误也可由运行时或操作系统代码中的内部错误引起。