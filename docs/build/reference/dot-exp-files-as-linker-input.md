---
title: "用作链接器输入的 .Exp 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".exp 文件 [C++]"
  - "EXP 文件"
  - "导出数据, 导出 (.exp) 文件"
  - "导出函数"
  - "导出函数, 关于导出的函数的信息"
  - "函数 [C++], 导出"
  - "导入库, 链接器文件"
  - "链接 [C++], 导出"
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 用作链接器输入的 .Exp 文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导出 \(.exp\) 文件包含有关导出函数和数据项的信息。  LIB 在创建导入库时还创建 .exp 文件。  当直接或间接地链接一个既导出到另一程序又从其导入的程序时，请使用 .exp 文件。  如果用 .exp 文件链接，则 LINK 不产生导入库，因为它假定 LIB 已经创建了导入库。  有关 .exp 文件和导入库的详细信息，请参见[处理导入库和导出文件](../../build/reference/working-with-import-libraries-and-export-files.md)。  
  
## 请参阅  
 [LINK 输入文件](../../build/reference/link-input-files.md)   
 [链接器选项](../../build/reference/linker-options.md)