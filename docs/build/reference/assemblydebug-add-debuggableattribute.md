---
title: /ASSEMBLYDEBUG（添加 DebuggableAttribute）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AssemblyDebug
- /ASSEMBLYDEBUG
helpviewer_keywords:
- /ASSEMBLYDEBUG linker option
- -ASSEMBLYDEBUG linker option
- ASSEMBLYDEBUG linker option
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
ms.openlocfilehash: b9899ea76b7a23a0d09442fca01e7d968c5e8aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273087"
---
# <a name="assemblydebug-add-debuggableattribute"></a>/ASSEMBLYDEBUG（添加 DebuggableAttribute）

```
/ASSEMBLYDEBUG[:DISABLE]
```

/ASSEMBLYDEBUG 发出**DebuggableAttribute**具有调试信息跟踪，并禁用 JIT 优化属性。 这是与源中指定以下属性：

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

/Assemblydebug: disable 发出**DebuggableAttribute**属性但禁用调试信息跟踪，启用 JIT 优化。 这是与源中指定以下属性：

```
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE
```

默认值是不发出**DebuggableAttribute**属性。

此外可以直接在源代码中的程序集添加 DebuggableAttribute。 例如，应用于对象的

```
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG
```

## <a name="remarks"></a>备注

需要显式指定的托管的映像可调试它。 使用[/Zi](z7-zi-zi-debug-information-format.md)单独是不够的。

影响的程序集生成其他链接器选项有：

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**调试**属性页。

1. 修改**可调试的程序集**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
