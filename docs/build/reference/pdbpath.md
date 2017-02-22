---
title: "/PDBPATH | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdbpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 文件, 路径"
  - "/PDBPATH dumpbin 选项"
  - "PDB 文件, 路径"
  - "PDBPATH dumpbin 选项"
  - "-PDBPATH dumpbin 选项"
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /PDBPATH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBPATH[:VERBOSE] filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 要为其查找匹配 .pdb 文件的 .dll 或 .exe 文件名。  
  
 VERBOSE（可选）  
 报告曾尝试在其中定位 .pdb 文件的所有目录。  
  
## 备注  
 \/PDBPATH 将沿调试器搜索 .pdb 文件的同一路径搜索计算机，并将报告哪些 .pdb 文件（若有）和 *filename* 中指定的文件相对应。  
  
 使用 Visual Studio 调试器时可能会遇到问题，这是因为调试器对调试文件的不同版本使用 .pdb 文件。  
  
 \/PDBPATH 将沿下列路径搜索 .pdb 文件：  
  
-   检查可执行文件驻留的位置。  
  
-   检查写入可执行文件的 PDB 的位置。  这通常是图像被链接时的位置。  
  
-   沿 Visual Studio IDE 中配置的搜索路径检查。  
  
-   沿 \_NT\_SYMBOL\_PATH 和 \_NT\_ALT\_SYMBOL\_PATH 环境变量中的路径检查。  
  
-   在 Windows 目录中检查。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)   
 [\/PDBALTPATH（使用备用 PDB 路径）](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)