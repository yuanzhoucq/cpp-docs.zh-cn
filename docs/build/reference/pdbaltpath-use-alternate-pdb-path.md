---
title: "/PDBALTPATH（使用备用 PDB 路径） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/pdbaltpath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 文件, 路径"
  - "/PDBALTPATH dumpbin 选项"
  - "PDB 文件, 路径"
  - "PDBALTPATH dumpbin 选项"
  - "-PDBALTPATH dumpbin 选项"
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /PDBALTPATH（使用备用 PDB 路径）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/PDBALTPATH:pdb_file_name  
```  
  
## 备注  
 其中：  
  
 *pdb\_file\_name*  
 .pdb 文件的路径和文件名。  
  
## 备注  
 使用此选项可以在已编译二进制文件中为程序数据库 \(.pdb\) 文件提供一个备用位置。  通常，链接器将 .pdb 文件的位置记录到它所生成的二进制文件中。  使用此选项可以为 .pdb 文件提供另一个路径和文件名。  \/PDBALTPATH 提供的信息不会更改实际 .pdb 文件的位置或名称；它更改链接器写入二进制文件中的信息。  这样，你可以提供一个独立于生成计算机的文件结构的路径。  此选项的两个常见用途是提供网络路径或不包含路径信息的文件。  
  
 *pdb\_file\_name* 的值可以是任意字符串，也可以是环境变量（即 **%\_PDB%**）。  链接器将环境变量（如 **%SystemRoot%**）扩展为它的值。  链接器将定义环境变量 **%\_PDB%** 和 **%\_EXT%**。  **%\_PDB%** 扩展为实际 .pdb 文件的文件名（不包含任何路径信息），**%\_EXT%** 是所生成的可执行文件的扩展名。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)   
 [\/PDBPATH](../../build/reference/pdbpath.md)