---
title: "链接器工具警告 LNK4099 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4099"
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 链接器工具警告 LNK4099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在“object\/library”或“path”中未找到 PDB “filename”；正在链接对象，就像没有调试信息一样  
  
 链接器未能找到 .pdb 文件。  将该文件复制到包含 `object/library` 的目录中。  
  
 查找与对象文件相关联的 .pdb 文件的名称：  
  
1.  使用 [lib](../../build/reference/lib-reference.md) **\/extract:**`objectname`**.obj** `xyz`**.lib** 从库中解压缩对象文件。  
  
2.  使用 **dumpbin \/section:.debug$T \/rawdata** `objectname`**.obj** 检查 .pdb 文件的路径。  
  
 也可以用 [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) 编译，这样就无需使用 pdb；或者，如果正在链接的对象不具有 .pdb 文件，请移除 [\/DEBUG](../../build/reference/debug-generate-debug-info.md) 链接器选项。