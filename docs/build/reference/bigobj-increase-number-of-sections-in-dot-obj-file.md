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
ms.openlocfilehash: 30c02c72496e3bb91da3b39e1870f1dc5a2c040a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493103"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj（增加 .Obj 文件中的节数）

**/bigobj**增加了对象文件可包含的节数。

## <a name="syntax"></a>语法

> **/bigobj**

## <a name="remarks"></a>备注

默认情况下, 对象文件最多可以包含 65279 (将近 2 ^ 16) 可寻址部分。 无论指定哪个目标平台, 此限制都适用。 **/bigobj**将该地址容量增加到 4294967296 (2 ^ 32)。

大多数模块不会生成包含65279多个节的 .obj 文件。 不过, 计算机生成的代码或大量使用模板库的代码可能需要可以容纳更多部分的 .obj 文件。 默认情况下, 通用 Windows 平台 (UWP) 项目上启用 **/bigobj** , 因为计算机生成的 XAML 代码包含大量的标头。 如果在 UWP 应用项目上禁用此选项, 则代码可能会生成编译器错误 C1128。

有关 PE-COFF 对象文件格式的信息, 请参阅 Windows 文档中的[Pe 格式](/windows/win32/debug/pe-format)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 在 "**附加选项**" 框中输入 **/bigobj**编译器选项。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
