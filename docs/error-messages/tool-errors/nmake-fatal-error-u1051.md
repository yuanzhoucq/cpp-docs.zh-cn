---
title: "NMAKE 错误 U1051 | Microsoft Docs"
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
  - "U1051"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1051"
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NMAKE 错误 U1051
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

内存不足  
  
 由于生成文件太大或太复杂，NMAKE 的内存（包括虚拟内存）已不足。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  释放一些磁盘空间。  
  
2.  增加 Windows NT 页面文件或 Windows 交换文件的大小。  
  
3.  如果仅有部分生成文件正在使用，则通过将生成文件分成单独的几个文件或使用 **\!IF** 预处理指令来限制 NMAKE 必须处理的量。  **\!IF** 预处理指令包括 **\!IF**、`!IFDEF`、**\!IFNDEF**、**\!ELSE IF**、**\!ELSE** `IFDEF` 和 **\!ELSE** `IFNDEF`。