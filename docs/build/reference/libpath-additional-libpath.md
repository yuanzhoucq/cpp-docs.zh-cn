---
title: -LIBPATH (附加的 Libpath) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
dev_langs:
- C++
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ccb94ad20735e81fc3d83f757cc0265cdc32169
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="libpath-additional-libpath"></a>/LIBPATH（附加的 Libpath）
```  
/LIBPATH:dir  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 `dir`  
 指定的路径之前搜索 LIB 环境选项中指定的路径，将搜索链接器。  
  
## <a name="remarks"></a>备注  
 /LIBPATH 选项用于重写环境库路径。 链接器将首先在此选项，指定的路径中搜索，然后搜索在 LIB 环境变量中指定的路径。 你可以指定您输入每个 /LIBPATH 选项只能将一个目录。 如果你想要指定多个目录，则必须指定多个 /LIBPATH 选项。 链接器将会按顺序搜索指定的目录。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**常规**属性页。  
  
4.  修改**附加库目录**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)