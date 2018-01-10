---
title: "指定自定义生成工具 |Microsoft 文档"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCustomBuildTool.CustomBuildToolBeforeTargets
- VC.Project.VCCustomBuildTool.Outputs
- VC.Project.VCCustomBuildTool.Command
- VC.Project.VCCustomBuildTool.CommandLine
- VC.Project.VCCustomBuildTool.AdditionalDependencies
- VC.Project.VCCustomBuildTool.Message
- VC.Project.VCCustomBuildTool.CustomBuildToolAfterTargets
- VC.Project.VCCustomBuildTool.Description
- VC.Project.VCCustomBuildTool.AdditionalInputs
dev_langs: C++
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4edd3b1fdb2b6d09be6f5fcd9a6c9d08ba7a6994
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="specify-custom-build-tools"></a>指定自定义生成工具

A*自定义生成工具*生成系统提供它需要生成特定的输入的文件的信息。 自定义生成工具指定要运行的命令、 的输入文件的列表、 的命令，生成的输出文件的列表以及该工具的可选描述。

有关自定义生成工具和自定义生成步骤的常规信息，请参阅[了解自定义生成步骤和生成事件](../ide/understanding-custom-build-steps-and-build-events.md)。

### <a name="to-specify-a-custom-build-tool"></a>若要指定自定义生成工具

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../ide/working-with-project-properties.md)。

1. 选择**配置属性**启用**配置**框。 在**配置**框中，选择你想要指定自定义生成工具的配置。

1. 在**解决方案资源管理器**，选择自定义生成工具的输入的文件。

   如果**自定义生成工具**文件夹未出现，则您选择的文件的文件扩展名是与一个默认的工具相关联。 例如，.c 和.cpp 文件的默认工具是编译器。 若要在中重写默认工具设置，**配置属性**节点，请在**常规**文件夹，请在**项类型**属性，选择**自定义生成工具**。 选择**应用**和**自定义生成工具**节点是否显示。

1. 在**自定义生成工具**节点，请在**常规**文件夹中，指定与自定义关联的属性生成工具：

   - 在**附加依赖项**，除了指定任何其他文件是为其定义的自定义生成工具 （与自定义生成工具关联的文件被隐式认为该工具的输入）。 其他输入文件不是必需的自定义生成工具。 如果你有多个附加输入，请用分号分隔它们。

      如果**附加依赖项**文件的日期是否晚于输入文件，然后运行自定义生成工具。 如果所有的**附加依赖项**文件都早于输入文件，而输入的文件日期早于**输出**属性文件，然后自定义生成工具不会运行。

      例如，假设你已自定义生成工具，它接受 MyInput.x 作为输入并生成 MyInput.cpp，和 MyInput.x 包括头文件中，MyHeader.h。 你可以为输入到 MyInput.x，依赖项指定 MyHeader.h 并生成系统将生成 MyInput.cpp，相对于 MyInput.x 或 MyHeader.h 过期时。

      输入的依赖关系还可以确保你的自定义生成工具运行所需的顺序。 在前面的示例中，假设 MyHeader.h 是实际的自定义生成工具的输出。 由于 MyHeader.h 是 MyInput.x 的依赖项，生成系统也将首先生成 MyInput.x 上运行的自定义生成工具之前 Myheader.h。

   - 在**命令行**，指定的命令，就像已在命令提示符下指定它。 请指定有效的命令或批处理文件，任何必需的输入或输出文件。 指定**调用**批处理的批处理文件的名称前的命令，以确保执行所有后续命令。

      可以使用 MSBuild 宏以符号方式指定多个输入和输出文件。 有关如何指定的文件，位置或文件集的名称的信息，请参阅[用于生成命令和属性的公共宏](../ide/common-macros-for-build-commands-and-properties.md)。

      因为 %字符保留了 MSBuild，如果你指定的环境变量将每个 **%** 用字符转义**%25**十六进制转义序列。 例如，对于替换**%WINDIR%**与**%25WINDIR %25**。 MSBuild 替换每个**%25**序列与 **%** 字符访问环境变量之前。

   - 在**说明**，输入有关此自定义生成工具的描述性消息。 将消息输出到**输出**窗口时生成系统处理此工具。

   - 在**输出**，指定输出文件的名称。 这是所需的项;如果此属性的值，没有自定义生成工具将无法运行。 如果自定义生成工具有多个输出，请使用分号分隔文件的名称。

      如中指定输出文件的名称应相同**命令行**属性。 项目生成系统将查找该文件，并检查其日期。 如果输出文件的版本高于输入文件，或如果找不到输出文件，运行的自定义生成工具。 如果所有的**附加依赖项**文件都早于输入文件，而输入的文件中指定的文件之前**输出**属性，自定义生成工具不运行。

如果你想为使用自定义生成工具所生成的输出文件生成系统，你必须手动将其添加到项目中。 自定义生成工具将在生成期间更新的文件。

## <a name="example"></a>示例

假定你想要包括名为 parser.l 项目中的文件。 具有词法分析器中， **lexer.exe**，你可执行文件的路径上。 你想要使用它来处理 parser.l 生成.c 文件具有相同的基名称 (parser.c)。

首先，将 parser.l 和 parser.c 添加到项目中。 如果文件尚不存在，添加对文件的引用。 创建 parser.l 一个自定义生成工具和输入中的以下**命令**属性：

> **词法分析器 %(FullPath)。\%（文件名）.c**

此命令在 parser.l 上运行词法分析器，并输出 parser.c 到项目目录。

在**输出**属性，请输入以下命令：

> **.\%（文件名）.c**

当生成项目时，生成系统会比较 parser.l 和 parser.c 的时间戳。 如果 parser.l 为较新，或如果 parser.c 不存在，生成系统运行的值**命令行**属性以便为 parser.c 最新。 由于 parser.c 也已添加到项目，生成系统进行编译 parser.c。

## <a name="see-also"></a>请参阅

[用于生成命令和属性的常用宏](../ide/common-macros-for-build-commands-and-properties.md)  
[生成自定义项疑难解答](../ide/troubleshooting-build-customizations.md)  
