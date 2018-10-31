---
title: /DELAYSIGN（为程序集进行部分签名）
ms.date: 11/04/2016
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
ms.openlocfilehash: 233a41a3e55ff2726712541b0af9db1f5e55eb56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435615"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN（为程序集进行部分签名）

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>自变量

**不**<br/>
指定程序集不应进行部分签名。

## <a name="remarks"></a>备注

使用 **/DELAYSIGN**如果只想要将公钥放在程序集中。 默认值是 **/delaysign: no**。

**/DELAYSIGN**选项没有任何影响，除非用于[/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)或[/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)。

在请求完全签名的程序集时，编译器会对包含清单（程序集元数据）的文件进行哈希处理，并使用私钥对哈希进行签名。 产生的数字签名存储在包含清单的文件中。 程序集延迟签名时，链接器不会计算和文件中存储签名，而保留空间，以便可以稍后添加该签名。

例如，使用 **/DELAYSIGN**允许测试人员将程序集放在全局缓存中。 测试完成后，可以通过将私钥置于程序集的程序集进行完全签名。

请参阅[强名称程序集 （程序集签名） (C + + CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)并[延迟为程序集签名](/dotnet/framework/app-domains/delay-sign-assembly)有关为程序集签名的详细信息。

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