---
title: /bigobj（增加 .Obj 文件中的节数）
ms.date: 11/04/2016
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: a9685834fc3e1de246c9d9d60d206538b744ce3e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809855"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj（增加 .Obj 文件中的节数）

**/bigobj**增加的对象文件可以包含的部分数。

## <a name="syntax"></a>语法

```
/bigobj
```

## <a name="remarks"></a>备注

默认情况下的对象文件可以保存最多 65,536 (2 ^16) 可寻址节。 无论指定哪个目标平台都是如此。 **/bigobj**增加到 4294967296 该地址容量 (2 ^32)。

大多数模块永远不会将生成一个包含节数超过 65536 的.obj 文件。 但是，计算机生成的代码，或大量使用模板库的代码可能需要可以容纳更多的节的.obj 文件。 **/bigobj**因为计算机生成的 XAML 代码包含大量标头的通用 Windows 平台 (UWP) 项目的默认情况下启用。 如果禁用此选项在 UWP 应用项目您很可能会遇到编译器错误 C1128。

使用 Visual c + + 2005年之前提供的链接器无法读取使用生成的.obj 文件 **/bigobj**。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 点击“命令行”  属性页。

1. 在 **“附加选项”** 框中键入编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
