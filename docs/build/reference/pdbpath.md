---
title: "-PDBPATH |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdbpath
dev_langs:
- C++
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ccbcedbf9cdd376fa7d9bced5c9d49542cee9f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pdbpath"></a>/PDBPATH
```  
/PDBPATH[:VERBOSE] filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 你想要查找匹配的.pdb 文件在.dll 或.exe 文件的名称。  
  
 详细 （可选）  
 报告其中尝试找到.pdb 文件的所有目录。  
  
## <a name="remarks"></a>备注  
 / 沿相同路径，调试器将搜索.pdb 文件，并将报告，如果有的话，.pdb 文件与到中指定的文件相对应的计算机中将搜索 PDBPATH *filename*。  
  
 当使用 Visual Studio 调试器，你可能遇到的问题，因为，调试器使用正在调试的文件的不同版本的.pdb 文件。  
  
 / PDBPATH 将搜索沿下列路径的.pdb 文件：  
  
-   检查可执行文件所在的位置。  
  
-   检查写入到可执行文件的 PDB 的位置。 这通常是在该映像已链接时的位置。  
  
-   检查在 Visual Studio IDE 中配置的搜索路径。  
  
-   检查沿 _NT_SYMBOL_PATH 和 _NT_ALT_SYMBOL_PATH 中路径环境变量。  
  
-   检查 Windows 目录中。  
  
## <a name="see-also"></a>请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)   
 [/PDBALTPATH（使用备用 PDB 路径）](../../build/reference/pdbaltpath-use-alternate-pdb-path.md)