---
title: "-ASSEMBLYMODULE （对程序集添加 MSIL 模块） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
dev_langs: C++
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efe45bd6a3225f50e1f842c6d247aae9626302a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE（向程序集添加 MSIL 模块）
```  
/ASSEMBLYMODULE:filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 你想要包括在此程序集中的模块。  
  
## <a name="remarks"></a>备注  
 进行选项，可添加对程序集的模块引用。 模块中的类型信息将不能添加的模块引用的程序集程序。 但是，在模块中的类型信息将可供引用程序集的任何程序。  
  
 使用[#using](../../preprocessor/hash-using-directive-cpp.md)添加对程序集的模块引用，并使模块的类型信息对程序集程序可用。  
  
 例如，考虑以下情况：  
  
1.  创建的模块[/LN](../../build/reference/ln-create-msil-module.md)。  
  
2.  使用其他项目中进行将该模块包含在当前的编译，将创建一个程序集。 此项目不能引用的模块`#using`。  
  
3.  引用此程序集的任何项目现在还可以使用的模块中的类型。  
  
 影响程序集生成其他链接器选项包括：  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Visual C++ 链接器接受 .netmodule 文件作为输入，链接器生成的输出文件将是与输入到链接器的任何 .netmodule 没有运行时依赖关系的程序集或 .netmodule。  有关详细信息，请参阅 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  单击**输入**属性页。  
  
4.  修改**将模块添加到程序集**属性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)