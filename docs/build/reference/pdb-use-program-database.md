---
title: "-PDB （使用程序数据库） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs: C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ea27dd7106e8490e9ba8ec9eacdcbbb02d33036
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pdb-use-program-database"></a>/PDB（使用程序数据库）
```  
/PDB:filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 链接器将创建程序数据库 (PDB) 的用户指定名称。 它将替换默认名称。  
  
## <a name="remarks"></a>备注  
 默认情况下，当[/调试](../../build/reference/debug-generate-debug-info.md)指定，则链接器将创建包含调试信息的程序数据库 (PDB)。 PDB 的默认文件名称具有程序和扩展名为.pdb 的基名称。  
  
 使用 /PDB:*filename*指定 PDB 文件的名称。 如果未指定 /DEBUG，则忽略 /PDB 选项。  
  
 PDB 文件可以是最多为 2 GB。  
  
 有关详细信息，请参阅[用作链接器输入的.pdb 文件](../../build/reference/dot-pdb-files-as-linker-input.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**调试**属性页。  
  
4.  修改**生成程序数据库文件**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)