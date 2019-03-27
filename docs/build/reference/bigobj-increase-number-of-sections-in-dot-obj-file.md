---
title: /bigobj（增加 .Obj 文件中的节数）
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 46399dc0c1ff552b4fc963b686ac6aa6df8b6f71
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508710"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj（增加 .Obj 文件中的节数）

**/bigobj**增加的对象文件可以包含的部分数。

## <a name="syntax"></a>语法

> **/bigobj**

## <a name="remarks"></a>备注

默认情况下的对象文件可以保存最多 65279 (几乎 2 ^16) 可寻址节。 此限制适用的目标无论指定平台。 **/bigobj**增加到 4294967296 该地址容量 (2 ^32)。

大多数模块永远不会生成包含多个 65279 节的.obj 文件。 但是，计算机生成的代码或大量使用模板库的代码可能需要可以容纳更多的节的.obj 文件。 **/bigobj**因为计算机生成的 XAML 代码包含大量标头的通用 Windows 平台 (UWP) 项目的默认情况下启用。 如果禁用此选项在 UWP 应用项目，你的代码可能会生成编译器错误 C1128。

有关 PE COFF 对象文件格式的信息，请参阅[PE 格式](/windows/desktop/debug/pe-format)Windows 文档中。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **C/c + +** > **命令行**属性页。

1. 输入 **/bigobj**中的编译器选项**其他选项**框。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
