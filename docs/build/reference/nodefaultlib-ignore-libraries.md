---
title: -NODEFAULTLIB （忽略库） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
dev_langs:
- C++
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51caac10218d5f4d1787b2256875001ac32dc2b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB（忽略库）
```  
/NODEFAULTLIB[:library]   
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *库*  
 您希望链接器来解析外部引用时忽略库。  
  
## <a name="remarks"></a>备注  
 /NODEFAULTLIB 选项通知链接器从它所解析外部引用时搜索的库列表中删除一个或多个默认库。  
  
 若要创建的.obj 文件，不包含对默认库的引用，使用[/Zl （省略默认库名称）](../../build/reference/zl-omit-default-library-name.md)。  
  
 默认情况下，/NODEFAULTLIB 从的解析外部引用时搜索的库的列表中移除所有默认库。 可选*库*参数允许你从在解析外部引用时搜索的库的列表中删除指定的库。 指定你想要排除的每个库的一个 /NODEFAULTLIB 选项。  
  
 链接器通过第一次搜索的库中显式指定，则在指定的默认库使用 /DEFAULTLIB 选项，然后在.obj 文件中命名的默认库解析对外部定义的引用。  
  
 /NODEFAULTLIB:*库*重写[/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*库*时相同*库*中同时指定名称。  
  
 如果你使用 /NODEFAULTLIB，例如，若要生成程序而不 C 运行时库，你可能必须也使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)在程序中指定的入口点 （函数）。 有关详细信息，请参阅 [ CRT 库功能](../../c-runtime-library/crt-library-features.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**输入**属性页。  
  
4.  选择**忽略所有默认库**属性或指定你想要忽略中的库的列表**忽略特定库**属性。 **命令行**属性页将显示这些属性所做的更改的效果。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)