---
title: /ASSEMBLYMODULE（向程序集添加 MSIL 模块）
ms.date: 11/04/2016
f1_keywords:
- /assemblymodule
- VC.Project.VCLinkerTool.AddModuleNamesToAssembly
helpviewer_keywords:
- ASSEMBLYMODULE linker option
- assemblies [C++], adding modules to
- assemblies [C++]
- /ASSEMBLYMODULE linker option
- -ASSEMBLYMODULE linker option
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
ms.openlocfilehash: 728e8a84ff8d1afac99f99dbb975c7fd9360bcc1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57815250"
---
# <a name="assemblymodule-add-a-msil-module-to-the-assembly"></a>/ASSEMBLYMODULE（向程序集添加 MSIL 模块）

```
/ASSEMBLYMODULE:filename
```

## <a name="arguments"></a>自变量

*filename*<br/>
想要包括在此程序集中的模块。

## <a name="remarks"></a>备注

/ASSEMBLYMODULE 选项允许您添加的模块引用的程序集。 模块中的类型信息将不能添加模块引用的程序集。 但是，在模块中的类型信息将可供引用的程序集的任何程序。

使用[#using](../../preprocessor/hash-using-directive-cpp.md)添加模块引用的程序集，并使模块的类型信息提供给程序集。

例如，考虑以下情况：

1. 创建的模块[/LN](ln-create-msil-module.md)。

1. 使用不同的项目中 /ASSEMBLYMODULE 将创建一个程序集在当前编译中包含该模块。 此项目将引用的模块`#using`。

1. 任何引用此程序集的项目现在还可以使用的模块中的类型。

影响的程序集生成其他链接器选项有：

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

MSVC 链接器接受.netmodule 文件作为输入，链接器生成的输出文件将程序集或.netmodule 上的任何链接器输入的.netmodule 没有运行时依赖性。  有关详细信息，请参阅 [用作链接器输入的 .netmodule 文件](netmodule-files-as-linker-input.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**输入**属性页。

1. 修改**将模块添加到程序集**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
