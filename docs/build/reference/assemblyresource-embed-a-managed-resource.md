---
title: /ASSEMBLYRESOURCE（嵌入托管资源）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: c18a014ca645cceb3196fb7efefd227e96f8e1fa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416211"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE（嵌入托管资源）

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>参数

*filename*<br/>
你想要在此程序集中嵌入托管的资源。

*name*<br/>
可选。 资源; 的逻辑名称用来加载资源的名称。 默认值是文件的名称。

或者，可以指定是否该文件应为私有程序集清单中。 默认情况下*名称*在程序集是公共的。

## <a name="remarks"></a>备注

/ASSEMBLYRESOURCE 选项用于在程序集中嵌入资源。

资源是在公共程序集时使用链接器创建的。 链接器不允许你重命名的程序集中的资源。

如果*文件名*是.NET Framework 创建的资源 (.resources) 文件的示例中，通过[资源文件生成器 (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator)或在开发环境中，则可以使用来访问中的成员**System.Resources**命名空间 (请参阅[System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager)有关详细信息)。 对于所有其他资源，请使用**GetManifestResource** \*中的方法**不过 System.Reflection.Assembly**类，以在运行时访问资源。

影响的程序集生成其他链接器选项有：

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**输入**属性页。

1. 修改**嵌入托管资源文件**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

1. 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
