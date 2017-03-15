---
title: "C 运行时错误 R6009 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6009"
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C 运行时错误 R6009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

环境所需的空间不足  
  
 有足够的内存加载程序，但没有足够的内存创建 **envp** 数组。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  增加程序可用的内存量。  
  
2.  减少命令行参数的数目和大小。  
  
3.  移除多余变量以减小环境大小。