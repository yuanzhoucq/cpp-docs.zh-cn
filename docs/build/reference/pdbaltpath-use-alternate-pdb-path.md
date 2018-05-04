---
title: -PDBALTPATH （使用备用 PDB 路径） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdbaltpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dec06c3d6a8a981a059f173700e716431acc53a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH（使用备用 PDB 路径）
```  
/PDBALTPATH:pdb_file_name  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *pdb_file_name*  
 .pdb 文件的路径和文件名。  
  
## <a name="remarks"></a>备注  
 使用此选项可以在已编译二进制文件中为程序数据库 (.pdb) 文件提供一个备用位置。 通常，链接器将 .pdb 文件的位置记录到它所生成的二进制文件中。 使用此选项可以为 .pdb 文件提供另一个路径和文件名。 /PDBALTPATH 提供的信息不会更改实际 .pdb 文件的位置或名称；它更改链接器写入二进制文件中的信息。 这样，你可以提供一个独立于生成计算机的文件结构的路径。 此选项的两个常见用途是提供网络路径或不包含路径信息的文件。  
  
 值*pdb_file_name*可以是任意字符串，环境变量，或 **%_PDB %**。 链接器将展开环境变量，例如 **%systemroot%**，为其值。 链接器将定义环境变量 **%_PDB %** 和 **%_EXT %**。 **%_PDB %** 扩展为实际.pdb 文件不包含任何路径信息的文件名称和 **%_EXT %** 是生成的可执行文件的扩展名。  
  
## <a name="see-also"></a>请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)   
 [/PDBPATH](../../build/reference/pdbpath.md)