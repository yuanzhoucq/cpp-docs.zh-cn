---
title: "-KEYFILE （指定密钥或密钥对程序集进行签名） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
dev_langs: C++
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6a061abf3a8f16bdd38a8b41a3b97a5f4ba1a885
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE（指定密钥或密钥对以便为程序集签名）
```  
/KEYFILE:filename  
```  
  
## <a name="remarks"></a>备注  
 其中：  
  
 *filename*  
 包含密钥的文件。 将字符串放置在双引号 ("") 如果它包含空格。  
  
## <a name="remarks"></a>备注  
 链接器将公钥插入程序集清单，然后使用私钥进行签名最终的程序集。 若要生成的密钥文件，请键入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令行。 签名的程序集被认为具有强名称。  
  
 如果使用编译[/LN](../../build/reference/ln-create-msil-module.md)，密钥文件的名称保存在模块中，并合并到编译通过包括对该模块的显式引用程序集时创建的程序集[#using](../../preprocessor/hash-using-directive-cpp.md)，或使用链接时[进行](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。  
  
 此外可以将你的加密信息传递到链接器使用[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)。 使用[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)如果你想部分签名的程序集。 请参阅[强名称程序集 （程序集签名） (C + + /cli CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)有关程序集进行签名的详细信息。  
  
 两者**/KEYFILE**和**/KEYCONTAINER**指定链接器 （通过命令行选项或通过自定义特性），将首先尝试密钥容器。 如果成功，则使用密钥容器中的信息对程序集签名。 如果链接器未找到密钥容器，它将尝试使用 /KEYFILE 指定的文件。 如果成功，则使用密钥文件中的信息对程序集签名，并且将密钥信息安装到密钥容器中（类似于 sn -i），以便在下一次编译中，密钥容器选项将生效。  
  
 请注意，密钥文件可能仅包含公钥。  
  
 请参阅[创建和使用具有强名称程序集](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)有关程序集进行签名的详细信息。  
  
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
  
-   请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)