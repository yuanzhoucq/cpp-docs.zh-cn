---
title: "链接器工具错误 LNK1201 | Microsoft Docs"
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
  - "LNK1201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1201"
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

写入程序数据库“filename”时出错；请检查是否是磁盘空间不足、路径无效或权限不够  
  
 LINK 未能写入输出文件的程序数据库 \(PDB\)。  
  
### 通过检查以下可能的原因进行修复  
  
1.  文件已损坏。  删除 PDB 文件然后重新链接。  
  
2.  没有足够的磁盘空间写入文件。  
  
3.  可能由于网络问题，驱动器不可用。  
  
4.  调试器在您尝试链接的程序上是活动的。  
  
5.  堆空间不足。有关更多信息，请参见 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)。