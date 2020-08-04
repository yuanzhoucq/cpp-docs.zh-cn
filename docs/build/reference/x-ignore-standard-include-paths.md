---
title: /X（忽略标准包含路径）
ms.date: 07/31/2020
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 652feeb200b7106aaca1ed7264f1e25c088a3dab
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520403"
---
# <a name="x-ignore-standard-include-paths"></a>`/X`（忽略标准包含路径）

阻止编译器在路径中指定的目录中搜索包含文件，并包括环境变量。

## <a name="syntax"></a>语法

> **`/X`**

## <a name="remarks"></a>备注

可以将此选项与 " [ `/I` （附加包含目录）](i-additional-include-directories.md) " 选项一起使用，以指定标准包含文件的备用路径。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**" "  >  **c/c + +**  >  **预处理器**" 属性页。

1. 修改 "**忽略标准包含路径**" 属性。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>。

## <a name="example"></a>示例

在下面的命令中， **`/X`** 通知编译器忽略由路径指定的位置并包含环境变量，并 **`/I`** 指定要在其中查找包含文件的目录：

```cmd
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
