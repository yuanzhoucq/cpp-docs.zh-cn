---
title: 指定自定义生成工具
ms.date: 06/05/2018
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
helpviewer_keywords:
- build tools (C++), specifying
- custom build tools (C++), specifying
- builds (C++), custom build tools
ms.openlocfilehash: dbce226b34503a9e8e70b6f19d9aa0c68ef487f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314749"
---
# <a name="specify-custom-build-tools"></a>指定自定义生成工具

自定义生成工具向生成系统提供生成特定输入文件所需的信息。 自定义生成工具指定要运行的命令、由此命令生成的输入文件列表和输出文件列表以及该工具的可选描述。

若要了解自定义生成工具和自定义生成步骤的常规信息，请参阅[了解自定义生成步骤和生成事件](understanding-custom-build-steps-and-build-events.md)。

### <a name="to-specify-a-custom-build-tool"></a>指定自定义生成工具

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](working-with-project-properties.md)。

1. 选择“配置属性”以启用“配置”框。 在“配置”框中，选择要为其指定自定义生成工具的配置。

1. 在“解决方案资源管理器”中，选择自定义生成工具的输入文件。

   如果未显示“自定义生成工具”文件夹，则所选文件的文件扩展名与默认工具关联。 例如，.c 和 .cpp 文件的默认工具为编译器。 若要替代默认工具设置，请在“配置属性”节点中的“常规”文件夹内，选择“项目类型”中的“自定义生成工具”。 选择“应用”，然后会显示“自定义生成工具”节点。

1. 在“自定义生成工具”节点中的“常规”文件夹内，指定与自定义生成工具关联的属性：

   - 在“附加依赖项”中，指定除自定义工具已定义内容以外的任何附加文件（与自定义生成工具关联的文件被隐式视为对该工具的输入）。 自定义生成工具并不要求具备附加输入文件。 如果有多个附加输入，请以分号进行分隔。

      如果有“附加依赖项”文件的日期晚于输入文件日期，则运行自定义生成工具。 如果所有“附加依赖项”文件的日期都早于输入文件日期，且输入文件的日期早于“输出”属性文件日期，则不运行自定义生成工具。

      例如，假设你的自定义生成工具将 MyInput.x 作为输入并生成 MyInput.cpp，且这个 MyInput.x 包括头文件 MyHeader.h。 你可以将 MyHeader.h 指定为 MyInput.x 的输入依赖项，且生成系统会在它过期时（相对于 MyInput.x 或 MyHeader.h）生成 MyInput.cpp。

      输入依赖项还能确保自定义生成工具按所需的顺序运行。 在前面的示例中，假设 MyHeader.h 实际上是自定义生成工具的输出。 由于 MyHeader.h 是 MyInput.x 的依赖项，生成系统会先生成 Myheader.h，然后再在 MyInput.x 上运行自定义生成工具。

   - 在命令行中指定一个命令，就像在命令提示符处指定它一样。 指定有效的命令或批处理文件以及任何必需的输入或输出文件。 在批处理文件名称之前指定 call 批处理命令，确保执行所有后续命令。

      可使用 MSBuild 宏以符号形式指定多个输入和输出文件。 有关如何指定文件的位置或文件集的名称的信息，请参阅[用于常见宏生成命令和属性](reference/common-macros-for-build-commands-and-properties.md)。

      由于“%”字符已由 MSBuild 预留，如果指定环境变量，请将每个 % 转义字符替换为 %25 十六进制转义序列。 例如将 %WINDIR% 替换为 %25WINDIR%25。 MSBuild 在访问环境变量之前将每个 %25 序列替换为 % 字符。

   - 在“描述”中输入关于此自定义生成工具的描述性消息。 该消息会在生成系统处理此工具时打印至“输出”窗口。

   - 在“输出”中指定输出文件的名称。 此为必填项，如果此属性没有值，则不会运行自定义生成工具。 如果自定义生成工具有多个输出，请以分号分隔它们的文件名。

      输出文件的名称应与“命令行”属性中所指定的名称一致。 项目生成系统将查找该文件并检查文件日期。 如果输出文件的日期早于输入文件日期，或未找到输出文件，则运行自定义生成工具。 如果所有“附加依赖项”文件的日期都早于输入文件日期，且输入文件的日期早于“输出”属性中指定的文件日期，则不运行自定义生成工具。

如果希望在由自定义生成工具生成的输出文件上运行生成系统，则需要手动将其添加到项目。 自定义生成工具将在生成期间更新文件。

## <a name="example"></a>示例

假定希望在项目中包括名为 parser.l 的文件。 在可执行路径上有一个词法分析程序 lexer.exe。 你想使用它处理 parser.l 以生成基名称一样的 .c 文件 (parser.c)。

首先，将 parser.l 和 parser.c 添加到项目中。 如果文件尚不存在，请添加对文件的引用。 为 parser.l 创建一个自定义生成工具，并在“命令”属性中输入以下内容：

> **lexer %(FullPath) .\%(Filename).c**

此命令在 parser.l 上运行词法分析程序，并将 parser.c 输出到项目目录。

在“输出”属性中输入以下内容：

> **.\%(Filename).c**

在生成项目时，生成系统会比较 parser.l 和 parser.c 的时间戳。 如果 parser.l 的时间戳较新，或 parser.c 不存在，生成系统则运行“命令行”属性的值来更新 parser.c。 由于 parser.c 也已添加到项目，生成系统会编译 parser.c。

## <a name="see-also"></a>请参阅

[用于生成命令和属性的常用宏](reference/common-macros-for-build-commands-and-properties.md)<br>
[生成自定义项疑难解答](troubleshooting-build-customizations.md)
