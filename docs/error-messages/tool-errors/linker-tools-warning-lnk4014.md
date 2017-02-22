---
title: "链接器工具警告 LNK4014 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4014"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4014"
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具警告 LNK4014
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法找到成员对象“objectname”  
  
 LIB 在库中未能找到 `objectname`。  
  
 **\/REMOVE** 和 **\/EXTRACT** 选项需要将要删除或复制到文件的成员对象的全名。  全名包括原始对象文件的路径。  若要查看库中成员对象的全名，请使用 DUMPBIN [\/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) 或 LIB [\/LIST](../../build/reference/managing-a-library.md)。