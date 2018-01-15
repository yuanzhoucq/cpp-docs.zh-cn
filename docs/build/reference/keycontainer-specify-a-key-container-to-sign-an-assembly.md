---
title: "-KEYCONTAINER （指定密钥容器程序集进行签名） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
dev_langs: C++
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f0e1f31e85c23b32bee1b8b968bbec65ee82beb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER（指定密钥容器以便为程序集签名）
```  
/KEYCONTAINER:name  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 *name*  
 包含密钥的容器。 将字符串放置在双引号 ("") 如果它包含空格。  
  
## <a name="remarks"></a>备注  
 链接器将通过将公钥插入程序集清单，并使用私钥签名最终的程序集创建签名的程序集。 若要生成的密钥文件，请键入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令行。 **sn-i**安装到容器的密钥对。  
  
 如果使用编译[/LN](../../build/reference/ln-create-msil-module.md)，密钥文件的名称保存在模块中，并合并到编译通过包括对该模块的显式引用程序集时创建的程序集[#using](../../preprocessor/hash-using-directive-cpp.md)，或使用链接时[进行](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。  
  
 此外可以将你的加密信息传递给编译器使用[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)。 使用[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)如果你想部分签名的程序集。 请参阅[强名称程序集 （程序集签名） (C + + /cli CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)有关程序集进行签名的详细信息。  
  
 影响程序集生成其他链接器选项包括：  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
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