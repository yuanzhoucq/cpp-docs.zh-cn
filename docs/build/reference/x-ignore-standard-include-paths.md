---
title: /X（忽略标准包含路径）
ms.date: 11/04/2016
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 615a53a7ad29527187072c3131f551a76bd18969
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421359"
---
# <a name="x-ignore-standard-include-paths"></a>/X（忽略标准包含路径）

禁止编译器在 PATH 和 INCLUDE 环境变量中指定的目录中的包含文件搜索。

## <a name="syntax"></a>语法

```
/X
```

## <a name="remarks"></a>备注

可以使用此选项与[/I （附加包含目录）](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) 选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击**预处理器**属性页。

1. 修改**忽略标准包含路径**属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>。

## <a name="example"></a>示例

在以下命令中，`/X`告知编译器忽略 PATH 和 INCLUDE 环境变量，指定的位置和`/I`指定在其中查找目录包含文件：

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>请参阅

[编译器选项](../../build/reference/compiler-options.md)<br/>
[设置编译器选项](../../build/reference/setting-compiler-options.md)
