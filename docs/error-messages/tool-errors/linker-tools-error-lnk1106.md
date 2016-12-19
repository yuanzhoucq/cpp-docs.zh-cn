---
title: "链接器工具错误 LNK1106 | Microsoft Docs"
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
  - "LNK1106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1106"
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1106
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

文件无效或磁盘已满: 无法查找到 location  
  
 工具未能读取或写入内存映射文件中的 `location`。  
  
### 通过检查以下可能的原因进行修复  
  
1.  磁盘已满。  
  
     释放一些空间并重新链接。  
  
2.  尝试通过网络进行链接。  
  
     一些网络不完全支持链接器使用的内存映射文件。  尝试在本地磁盘上链接。  
  
3.  磁盘上的块错误。  
  
     尽管操作系统和磁盘硬件应该已检测到这样的错误，但仍可能需要运行磁盘检查程序。  
  
4.  堆空间不足。  
  
     有关更多信息，请参见 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)。