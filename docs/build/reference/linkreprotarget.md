---
title: /LINKREPROTARGET （链接重现文件名）
description: 链接器或库工具选项，用于设置链接重现的目标文件名。
ms.date: 09/24/2019
f1_keywords:
- /LINKREPROTARGET
helpviewer_keywords:
- LINKREPROTARGET linker option
- /LINKREPROTARGET linker option
- -LINKREPROTARGET linker option
- linker repro reporting
ms.openlocfilehash: 4912e8bc64d31e3ecc97ea25783c7329e7d7861c
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686904"
---
# <a name="linkreprotarget-link-repro-file-name"></a>/LINKREPROTARGET （链接重现文件名）

仅当目标具有指定文件名时，通知链接器或库工具生成链接重现。

## <a name="syntax"></a>语法

> **/LINKREPROTARGET：** _文件名_

### <a name="arguments"></a>参数

**/LINKREPROTARGET：** _文件名_\
要筛选的目标文件名。 仅当指定的文件为输出目标时才会生成链接重现。 包含空格的文件名必须用双引号引起来。 文件名应包括基名称和扩展名，而不是路径。

## <a name="remarks"></a>备注

**/LINKREPROTARGET**选项用于指定要为其生成*链接重现*的目标文件名。 链接重现是一组生成项目，可让 Microsoft 再现链接时或库操作期间发生的问题。 当你指定[/LINKREPRO](linkrepro.md)选项时，或在命令行生成环境中设置 @no__t 1 环境变量时，链接器或库工具会生成一个链接重现。

在多次调用链接器或库工具的复杂生成中， **/LINKREPROTARGET**选项非常有用。 它允许为链接重现指定特定目标，如 "*问题 .dll*"。 仅当工具生成特定文件时，它才允许生成链接重现。

有关如何以及何时创建链接重现的详细信息，请参阅[如何使用 Microsoft C++工具集报告问题](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)的[链接重现](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros)部分。

必须设置 **/LINKREPRO**和[/Out](out-output-file-name.md)选项， **/LINKREPROTARGET**选项才能生效。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**"  > **链接器**@no__t "**命令行**" 属性页。

1. 在 "**附加选项**" 框中输入 **/LINKREPROTARGET：** _文件名_选项。 选择**确定**以应用更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)\
[MSVC 链接器选项](linker-options.md)\
[/LINKREPRO](linkrepro.md)
