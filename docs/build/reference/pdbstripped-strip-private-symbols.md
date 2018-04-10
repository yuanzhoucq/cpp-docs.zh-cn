---
title: -PDBSTRIPPED （去除私有符号） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
dev_langs:
- C++
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff124dec52a77ed5bf35d2454f95854ebea5eea0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED（去除私有符号）
```  
/PDBSTRIPPED:pdb_file_name  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *pdb_file_name*  
 链接器将创建去除的程序数据库 (PDB) 的用户指定名称。  
  
## <a name="remarks"></a>备注  
 /PDBSTRIPPED 选项创建另一个程序数据库 (PDB) 文件，当你生成程序图像与任意的编译器或链接器生成 PDB 文件的选项 ([/调试](../../build/reference/debug-generate-debug-info.md)， [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)，/Zd 或 /Zi)。 此 PDB 文件省略您不希望交付给客户的符号。 第二个的 PDB 文件将仅包含：  
  
-   公共符号  
  
-   对象文件和它们参与构成的可执行文件中的部分列表  
  
-   用于遍历堆栈帧指针优化 (FPO) 调试记录  
  
 已去除的 PDB 文件将不包含：  
  
-   类型信息  
  
-   行号信息  
  
-   例如，那些用于函数、 局部变量和静态数据的每个对象文件 CodeView 符号  
  
 当你使用 /PDBSTRIPPED 时，仍会生成完整的 PDB 文件。  
  
 如果你没有创建 PDB 文件，则忽略 /PDBSTRIPPED。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**调试**属性页。  
  
4.  修改**去除私有符号**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)