---
title: "资源编译器错误 RW1022 | Microsoft Docs"
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
  - "RW1022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW1022"
ms.assetid: 6747c8a9-9c9b-4422-b414-0645d22092d0
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RW1022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**写入文件时出现 I\/O 错误**  
  
 资源编译器未能写入文件。  
  
### 通过检查以下可能的原因进行修复  
  
1.  磁盘空间不足。  剩余空间必须是您正在创建的可执行文件大小的至少两倍。  
  
2.  卷为只读。  
  
3.  坏扇区。  
  
4.  共享冲突。