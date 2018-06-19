---
title: -DEF （指定模块定义文件） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0c712b81fbb755edd132c6f97efc906ba4f5ff9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371146"
---
# <a name="def-specify-module-definition-file"></a>/DEF（指定模块定义文件）
```  
/DEF:filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 模块定义文件 (.def) 传递给链接器的名称。  
  
## <a name="remarks"></a>备注  
 /DEF 选项将模块定义文件 (.def) 传递给链接器。 只有一个.def 文件可以指定到链接。 有关.def 文件的详细信息，请参阅[模块定义文件](../../build/reference/module-definition-dot-def-files.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**输入**属性页。  
  
4.  修改**模块定义文件**属性。  
  
 若要指定.def 文件从开发环境中的，你应将其添加到其他文件以及项目，，然后指定给 /DEF 选项文件。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)