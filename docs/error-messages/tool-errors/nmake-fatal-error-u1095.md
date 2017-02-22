---
title: "NMAKE 错误 U1095 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1095"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1095"
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# NMAKE 错误 U1095
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

扩展命令行“commandline”太长  
  
 宏展开之后，给定的命令行超过操作系统命令行长度的限制。  
  
 MS\-DOS 允许一个命令行上最多有 128 个字符。  
  
 如果命令用于可从文件中接受命令行输入的程序，则更改该命令并从磁盘上的文件或内联文件中提供输入。  例如，LINK 和 LIB 从响应文件中接受输入。