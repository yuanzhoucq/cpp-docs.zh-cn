---
title: "BSCMAKE 错误 BK1514 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1514"
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# BSCMAKE 错误 BK1514
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有 .SBR 文件都被截断，在 filename 中未找到任何此类文件  
  
 为更新指定的所有 .sbr 文件都不是原始浏览信息 \(.bsc\) 文件的一部分。  若要查找导致该错误的 .sbr 文件的文件名，请阅读该错误之前出现的 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) 警告。  
  
### 通过检查以下可能的原因进行修复  
  
1.  为 .sbr 或 .bsc 文件指定的文件名错误。  
  
2.  损坏的 .bsc 文件要求 BSCMAKE 重新生成它。