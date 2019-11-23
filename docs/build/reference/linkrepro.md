---
title: /LINKREPRO（链接重现目录名称）
description: 链接器或库工具选项，用于设置链接重现的目录。
ms.date: 09/24/2019
f1_keywords:
- /LINKREPRO
helpviewer_keywords:
- LINKREPRO linker option
- /LINKREPRO linker option
- -LINKREPRO linker option
- linker repro reporting
ms.openlocfilehash: d81fb529cdbb0741c6dff58032dad97df89b4d4f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686916"
---
# <a name="linkrepro-link-repro-directory-name"></a>/LINKREPRO（链接重现目录名称）

通知链接器或库工具在指定的目录中生成链接重现。

## <a name="syntax"></a>语法

> **/LINKREPRO：** _目录名称_

### <a name="arguments"></a>参数

**/LINKREPRO：** _目录名_\
要在其中存储链接重现的用户指定目录。 包含空格的目录名称必须用双引号引起来。

## <a name="remarks"></a>备注

**/LINKREPRO**选项用于创建*链接重现*。 这是一组生成项目，可让 Microsoft 再现链接时或库操作期间发生的问题。 这对于一些问题（例如，涉及链接时间代码生成（LTCG）的后端故障、LNK1000 链接器错误或链接器崩溃）非常有用。 当你指定 **/LINKREPRO**链接器选项时，或在命令行生成环境中设置 `link_repro` 环境变量时，该工具将生成一个链接重现。 有关详细信息，请参阅[如何使用 Microsoft C++工具集报告问题](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)的[链接重现](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros)部分。

**/LINKREPRO**链接器选项和 `link_repro` 环境变量都需要为链接重现指定输出目录。 在命令行或 IDE 中，使用 **/LINKREPRO：** _directory-name_选项指定目录。 指定的_目录名称_可能是绝对路径或相对路径，但该目录必须存在。 命令行选项将覆盖 `link_repro` 环境变量中设置的任何目录值。

有关如何将链接重现生成限制为特定目标文件名的信息，请参阅[/LINKREPROTARGET](linkreprotarget.md)选项。 此选项可用于指定要为其生成链接重现的特定目标。 它在多次调用链接器或库工具的复杂版本中非常有用。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” **“链接器”** “命令行”属性页 >  > 。

1. 在 "**附加选项**" 框中输入 **/LINKREPRO：** _目录名称_选项。 指定的_目录名称_值必须存在。 选择“确定”应用更改。

生成链接重现后，再次打开此属性页可从生成中删除 **/LINKREPRO**选项。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 链接器引用](linking.md)\
[MSVC 链接器选项](linker-options.md)\
[/LINKREPROTARGET](linkreprotarget.md)
