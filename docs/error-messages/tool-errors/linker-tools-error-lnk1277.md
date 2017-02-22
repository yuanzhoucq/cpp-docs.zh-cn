---
title: "链接器工具错误 LNK1277 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1277"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1277"
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK1277
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未能在 pgd \(filename\) 中找到对象记录  
  
 当使用 [\/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md) 时，.lib、.def 或 .obj 输入文件之一的路径与在使用 \/LTCG:PGINSTRUMENT 期间找到这些文件的路径不同。  在 \/LTCG:PGINSTRUMENT 后面 LIB 环境变量的更改可解释此问题。  输入文件的完整路径存储在 .pgd 文件中。  
  
 \/LTCG:PGOPTIMIZE 要求输入与 \/LTCG:PGINSTRUMENT 阶段相同。  
  
 若要解除此警告，请执行以下操作之一：  
  
-   运行 \/LTCG:PGINSTRUMENT，重复所有测试运行，然后运行 \/LTCG:PGOPTIMIZE。  
  
-   将 LIB 环境变量更改为运行 \/LTCG:PGINSTRUMENT 时的相应内容。  
  
 不建议通过使用 \/LTCG:PGUPDATE 解决 LNK1277。