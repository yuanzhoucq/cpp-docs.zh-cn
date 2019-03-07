---
title: /KEYFILE（指定密钥或密钥对以便为程序集签名）
ms.date: 11/04/2016
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
ms.openlocfilehash: 279f83dd66777c0f1bb0aca836808da196886281
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414728"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE（指定密钥或密钥对以便为程序集签名）

```
/KEYFILE:filename
```

## <a name="arguments"></a>自变量

*filename*<br/>
包含密钥的文件。 将字符串放置在双引号 ("") 如果包含空格。

## <a name="remarks"></a>备注

链接器将公钥插入到程序集清单，然后使用私钥签名最终程序集。 若要生成的密钥文件，请键入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令行。 被认为具有强名称签名的程序集。

如果使用编译[/LN](../../build/reference/ln-create-msil-module.md)，保存在模块和合并到编译通过包括对该模块的显式引用的程序集时创建的程序集密钥文件的名称[#using](../../preprocessor/hash-using-directive-cpp.md)，或使用链接时[/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。

您可以将加密信息传递到链接器使用[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)。 使用[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)如果需要部分签名的程序集。 请参阅[强名称程序集 （程序集签名） (C + + CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)有关为程序集签名的详细信息。

两者 **/KEYFILE**并 **/KEYCONTAINER**指定 （通过命令行选项或通过自定义特性），链接器将首先尝试用密钥容器。 如果成功，则使用密钥容器中的信息对程序集签名。 如果链接器没有找到密钥容器，它将尝试用 /KEYFILE 指定的文件。 如果成功，则使用密钥文件中的信息对程序集签名，并且将密钥信息安装到密钥容器中（类似于 sn -i），以便在下一次编译中，密钥容器选项将生效。

请注意，密钥文件可能仅包含公钥。

请参阅[创建和使用具有强名称程序集](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)有关为程序集签名的详细信息。

影响的程序集生成其他链接器选项有：

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 点击“命令行”  属性页。

1. 该选项键入**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
