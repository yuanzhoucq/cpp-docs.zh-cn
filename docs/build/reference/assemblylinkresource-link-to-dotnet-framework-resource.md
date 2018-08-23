---
title: -ASSEMBLYLINKRESOURCE （链接到.NET Framework 资源） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
dev_langs:
- C++
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a922ac1a96a59d574f46f7b04db8b160a5079918
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374045"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE（链接到 .NET Framework 资源）
```  
/ASSEMBLYLINKRESOURCE:filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 希望从程序集链接到的 .NET Framework 资源文件。  
  
## <a name="remarks"></a>备注  
 /ASSEMBLYLINKRESOURCE 选项创建到.NET Framework 资源链接到输出文件; 中资源文件不位于输出文件中。 [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)将资源文件嵌入到输出文件中。  
  
 链接的资源是公共的中创建链接器时，该程序集。  
  
 /ASSEMBLYLINKRESOURCE 要求编译包含[/clr](../../build/reference/clr-common-language-runtime-compilation.md);[/LN](../../build/reference/ln-create-msil-module.md)或[/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) /ASSEMBLYLINKRESOURCE 不允许。  
  
 如果*filename*是.NET Framework 创建的资源文件，例如，通过[Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)或在开发环境中，它可以访问其成员保持**System.Resources**命名空间。 有关详细信息，请参阅[System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx)。 对于所有其他资源，请使用**GetManifestResource** \*中的方法**System.Reflection.Assembly**类在运行时访问资源。  
  
 *filename*可以是任何文件格式。 例如，你可能想要使本机 DLL 是程序集的一部分，以便它可以安装到全局程序集缓存并且从程序集中的托管代码访问。  
  
 影响程序集生成其他链接器选项包括：  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击**链接器**文件夹。  
  
3.  点击“命令行”  属性页。  
  
4.  该选项键入**其他选项**框。  
  
### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项  
  
-   请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)