---
title: "C 运行时错误 R6008 | Microsoft Docs"
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
  - "R6008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6008"
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# C 运行时错误 R6008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

参数所需的空间不足  
  
 有足够的内存加载程序，但没有足够的内存创建 **argv** 数组。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  增加程序可用的内存量。  
  
2.  减少命令行参数的数目和大小。  
  
3.  移除多余变量以减小环境大小。