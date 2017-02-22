---
title: "链接器工具错误 LNK1158 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1158"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1158"
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK1158
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法运行“filename”  
  
 [LINK](../../build/reference/linker-command-line-syntax.md) 调用的给定可执行文件不在包含 LINK 的目录中，也不在 PATH 环境变量指定的目录中。  
  
 例如，如果尝试在使用 32 位操作系统的计算机上使用 [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) 链接器选项的 PGOPTIMIZE 参数，将出现该错误。