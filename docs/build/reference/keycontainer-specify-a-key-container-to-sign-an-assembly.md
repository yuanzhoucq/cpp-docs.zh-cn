---
title: /KEYCONTAINER（指定密钥容器以便为程序集签名）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
ms.openlocfilehash: cd7c5a9cb4456a7f5cce828dc3ae05d895b1d6c6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415625"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER（指定密钥容器以便为程序集签名）

```
/KEYCONTAINER:name
```

## <a name="arguments"></a>自变量

*name*<br/>
包含密钥的容器。 将字符串放置在双引号 ("") 如果包含空格。

## <a name="remarks"></a>备注

链接器通过将公钥插入到程序集清单并且用私钥签名最终程序集创建签名的程序集。 若要生成的密钥文件，请键入[sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename*在命令行。 **sn-i**安装到容器的密钥对。

如果使用编译[/LN](../../build/reference/ln-create-msil-module.md)，保存在模块和合并到编译通过包括对该模块的显式引用的程序集时创建的程序集密钥文件的名称[#using](../../preprocessor/hash-using-directive-cpp.md)，或使用链接时[/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)。

此外可以将加密信息传递给编译器[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)。 使用[/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)如果需要部分签名的程序集。 请参阅[强名称程序集 （程序集签名） (C + + CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)有关为程序集签名的详细信息。

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
