---
title: "链接器工具错误 LNK1200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1200"
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具错误 LNK1200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

读取程序数据库“filename”时出错  
  
 未能读取程序数据库 \(PDB\)。  
  
 此错误可能是由于文件损坏而造成的。  
  
 如果 `filename` 是对象文件的 PDB，请使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 重新编译对象文件。  
  
 如果 `filename` 是主输出文件的 PDB，并且在增量链接期间发生该错误，请删除 PDB 并重新链接。