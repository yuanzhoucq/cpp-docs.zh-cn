---
title: "BSCMAKE 警告 BK4502 | Microsoft Docs"
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
  - "BK4502"
  - "BK1513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1513"
  - "BK4502"
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 警告 BK4502
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

被截断的 .SBR 文件“filename”不在 filename 中  
  
 在更新期间指定了最初不是 .bsc 文件一部分的零长度 .sbr 文件。  
  
### 通过检查以下可能的原因进行修复  
  
1.  指定的文件名错误。  
  
2.  文件已删除。（导致 [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) 错误。）  
  
3.  文件已损坏，需要 BSCMAKE 生成完整版本。