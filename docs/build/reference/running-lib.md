---
title: 运行 LIB
description: 描述可与 node.js 一起使用的命令行选项。
ms.date: 09/25/2019
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- Lib
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
ms.openlocfilehash: 0d65c8d8b3b0cd28c7cccda25bfd9512321172f9
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685552"
---
# <a name="running-lib"></a>运行 LIB

可以使用各种命令行选项控制 LIB。

## <a name="lib-command-line"></a>LIB 命令行

若要运行 LIB，请键入命令 `lib`，然后键入要使用 LIB 执行的任务的选项和文件名。 LIB 还接受命令文件中的命令行输入，如下一节中所述。 LIB 不使用环境变量。

## <a name="lib-command-files"></a>LIB 命令文件

可以使用以下语法将命令行参数传递到命令文件中的 LIB：

> **LIB \@** <em>命令文件</em>

文件*命令-文件*是文本文件。 在 @ 符号（ **\@** ）和文件名之间不允许有空格或制表符。 *命令文件名*没有默认扩展名;您必须指定完整的文件名，包括任何扩展名。 不能使用通配符。 您可以使用文件名指定绝对路径或相对路径。

在命令文件中，可以通过空格或制表符分隔参数，就像在命令行上一样。 还可以用换行符分隔参数。 使用分号（ **;** ）标记注释。 LIB 忽略从分号到行尾的所有文本。

可以在命令文件中指定命令行的全部或部分，并且可以在 LIB 命令中使用多个命令文件。 LIB 接受命令文件输入，就如同在命令行的该位置中指定的一样。 命令文件不能嵌套。 LIB 会回显命令文件的内容，除非使用 **/nologo**选项。

## <a name="using-lib-options"></a>使用 LIB 选项

选项包括一个选项说明符，该说明符为短划线（ **-** ）或正斜杠（ **/** ），后跟选项的名称。 不能缩写选项名称。 某些选项采用一个自变量，在冒号（ **：** ）后指定。 选项规范内不允许有空格或制表符。 在命令行上使用一个或多个空格或制表符分隔选项规范。 选项名及其关键字或文件名参数不区分大小写，但用作参数的标识符区分大小写。 LIB 按命令行和命令文件中指定的顺序处理选项。 如果使用不同的参数重复选项，则将优先处理最后一个选项。

下列选项适用于所有 LIB 模式：

> **/ERRORREPORT** \[**无** &#124; **提示** &#124; **队列** &#124; **发送**]

如果 lib 在运行时失败，则可以使用 **/ERRORREPORT**向 Microsoft 发送有关这些内部错误的信息。

有关 **/ERRORREPORT**的详细信息，请参阅[/ERRORREPORT （报告内部编译器错误）](errorreport-report-internal-compiler-errors.md)。

> **/LINKREPRO：** _目录-路径_ \
> **/LINKREPROTARGET：** _文件名_

若要帮助 Microsoft 诊断 lib 崩溃和内部错误，可以使用[/LINKREPRO](linkrepro.md)选项。 它会生成*链接重现*，这是一组生成项目，可让 Microsoft 再现在库操作期间出现的问题。 可以将[/LINKREPROTARGET](linkreprotarget.md)选项与 **/LINKREPRO**选项一起使用。 当 lib 生成指定的文件时，它只生成链接重现项目。 有关详细信息，请参阅[如何使用 Microsoft C++工具集报告问题](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)。

> **/LTCG**

"LTCG" 代表*链接时间代码生成*。 此功能要求在编译器（[node.js）、](compiler-options.md)LIB 和链接器（[链接](linker-options.md)）之间进行协作，以便优化除任何组件自身可以执行的操作之外的代码。

对于 LIB， **/ltcg**选项指定 mage.exe 中的输入包含使用[/gl](gl-whole-program-optimization.md)编译器选项生成的对象文件。 如果 LIB 遇到此类输入，并且 **/ltcg**未指定，则在显示信息性消息后，它将在启用/ltcg 的情况下重新启动。 换言之，无需显式设置此选项，但它会提高生成性能，因为 LIB 无需重新启动。

在生成过程中，将从 LIB 输出发送到 LINK。 LINK 具有其自己的单独 **/ltcg**选项。 它用于执行各种优化，包括全程序优化和按配置优化（PGO）检测。 有关 LINK 选项的详细信息，请参阅[/ltcg](ltcg-link-time-code-generation.md)。

> **/MACHINE**

指定程序的目标平台。 通常，无需指定 **/MACHINE**。 LIB 从 .obj 文件中推断出计算机类型。 但是，在某些情况下，LIB 无法确定计算机类型并发出错误消息。 如果出现这种错误，请指定 **/MACHINE**。 在 **/EXTRACT**模式下，此选项仅用于验证。 在命令行中使用 `lib /?` 来查看可用的计算机类型。

> **/NOLOGO**

禁止显示 LIB 版权消息和版本号，并防止命令文件回显。

> **/VERBOSE**

显示有关会话进度的详细信息，包括正在添加的 .obj 文件的名称。 信息被发送到标准输出，并可重定向到文件。

> **/WX**[ **:NO**]

将警告视为错误。 有关详细信息，请参阅 [/WX（将链接器警告视为错误）](wx-treat-linker-warnings-as-errors.md)。

其他选项仅适用于特定的 LIB 模式。 描述每个模式部分介绍了这些选项。

## <a name="see-also"></a>请参阅

[LIB 引用](lib-reference.md)
