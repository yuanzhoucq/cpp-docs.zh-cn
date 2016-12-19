---
title: "链接器工具错误 LNK1140 | Microsoft Docs"
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
  - "LNK1140"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1140"
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1140
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用于程序数据库的模块太多；链接时使用 \/PDB:NONE  
  
 项目包含的模块超过 4096 个。  
  
### 通过使用下面可能的解决方案进行修复  
  
1.  使用 [\/PDB:NONE](../../build/reference/pdb-use-program-database.md) 重新链接。  
  
2.  编译某些模块时不使用调试信息。  
  
3.  减少模块数量。