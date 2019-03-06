---
title: /DEF（指定模块定义文件）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: 4b6490186e2faf289844f7fb6b84f5a1c27b10a5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423496"
---
# <a name="def-specify-module-definition-file"></a>/DEF（指定模块定义文件）

```
/DEF:filename
```

## <a name="arguments"></a>自变量

*filename*<br/>
模块定义文件 (.def) 传递给链接器的名称。

## <a name="remarks"></a>备注

/DEF 选项将模块定义文件 (.def) 传递给链接器。 可以链接到指定只有一个.def 文件。 有关.def 文件的详细信息，请参阅[模块定义文件](../../build/reference/module-definition-dot-def-files.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**输入**属性页。

1. 修改**模块定义文件**属性。

若要指定.def 文件从开发环境中的，您应将其添加到项目，以及其他文件，然后指定 /DEF 选项的文件。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
