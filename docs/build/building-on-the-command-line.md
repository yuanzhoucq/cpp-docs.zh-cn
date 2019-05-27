---
title: 通过命令行使用 MSVC 工具集 - Visual Studio
description: 通过 Visual Studio IDE 外部的命令行使用 Microsoft C++ 编译器工具链 (MSVC)。
ms.custom: conceptual
ms.date: 05/16/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 97626455ace0d3ad47b9011594e82c144d7ea27d
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837118"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>通过命令行使用 MSVC 工具集

使用包含在 Visual Studio 中的工具，可在命令行上生成 C 和 C++ 应用程序。 此外，还可从 [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/)页面下载编译器工具集作为独立包。 它是“Visual Studio 生成工具”包的一部分；可选择仅下载 C++ 开发所需的工具。

## <a name="how-to-use-the-command-line-tools"></a>如何使用命令行工具

在 Visual Studio 安装程序中选择一个 C++ 工作负载时，它会安装 Visual Studio 平台工具集。 平台工具集具有用于特定 Visual Studio 版本的所有 C 和 C++ 工具，包括 C/C++ 编译器、链接器、汇编程序、其他生成工具以及匹配库。 可在命令行中使用所有这些工具，Visual Studio IDE 在内部也使用这些工具。 可使用单独的 x86 托管和 x64 托管的编译器和工具来生成 x86、x64、ARM 和 ARM64 目标代码。 用于特定主机和目标生成体系结构的每组工具都存储在其自己的目录中。

安装的编译器工具集取决于计算机处理器和安装期间选择的选项。 至少需安装 32 位 x86 托管的工具（用于生成 32 位 x86 本机代码）和兼容工具（用于生成 64 位 x64 本机代码）。 如果使用的是 64 位 Windows，则还需安装用于生成 64 位本机代码的 64 位 x64 托管工具和用于生成 32 位本机代码的兼容工具。 如果选择安装可选的 C++ 通用 Windows 平台工具，则还需安装用于生成 ARM 代码的 32 位和 64 位本机工具。 其他工作负载可能需安装其他工具。

## <a name="environment-variables-and-developer-command-prompts"></a>环境变量和开发人员命令提示符

需要设置几个特定的环境变量，这些工具才能正常运行。 这些变量用于将它们添加到路径和设置中，包括文件、库文件和 SDK 位置。 为了便于设置这些环境变量，安装程序会在安装期间创建自定义的命令文件或批处理文件。 可在命令提示符窗口中运行其中一个命令文件，以设置特定的主机和目标生成体系结构、Windows SDK 版本、目标平台和平台工具集。 为方便起见，安装程序还会在“开始”菜单中创建快捷方式，以使用这些命令文件启动开发人员命令提示符窗口，以便设置所有必需的环境变量并准备就绪以备使用。

所需的环境变量特定于安装和选择的生成体系结构，并且可能会因产品更新或升级而进行更改。 因此，强烈建议使用已安装的命令提示符快捷方式或命令文件之一，而不是自己在 Windows 中设置环境变量。 有关详细信息，请参阅 [为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="developer_command_prompt_shortcuts"></a> 开发人员命令提示符快捷方式

命令提示符快捷方式安装在“开始”菜单中特定于版本的 Visual Studio 文件夹中。 以下是基本命令提示符快捷方式列表以及它们支持的生成体系结构：

- **开发人员命令提示符** - 将环境设置为使用 32 位 x86 本机工具生成 32 位 x86 本机代码。
- **x86 本机工具命令提示符** - 将环境设置为使用 32 位 x86 本机工具生成 32 位 x86 本机代码。
- **x64 本机工具命令提示符** - 将环境设置为使用 64 位 x64 本机工具生成 64 位 x64 本机代码。
- **x86_x64 兼容工具命令提示符** - 将环境设置为使用 64 位 x64 本机工具生成 32 位 x86 本机代码。
- **x64_x86 兼容工具命令提示符** - 将环境设置为使用 64 位 x64 本机工具生成 32 位 x86 本机代码。

实际的“开始”菜单文件夹和快捷方式名称取决于安装的 Visual Studio 版本，以及安装时的安装名称。 例如，如果你安装了 Visual Studio 2019，并且已经为其提供了安装名称 Preview，那么在名为“Visual Studio 2019”的文件夹中，开发人员命令提示符快捷方式将被命名为“VS 2019 的开发人员命令提示符”。

## <a name="developer_command_prompt"></a> 打开“开发人员命令提示”窗口

1. 在桌面上，打开 Windows“开始”菜单，然后滚动查找并打开 Visual Studio 版本的文件夹，例如“Visual Studio 2019”。 在某些旧版本的 Visual Studio 中，快捷方式位于名为“Visual Studio Tools”的子文件夹中。

1. 在该文件夹中，为 Visual Studio 版本选择“开发人员命令提示符”。 此快捷方式启动开发人员命令提示符窗口，该窗口使用 32 位 x86 本机工具的默认生成体系结构来生成 32 位 x86 本机代码。 如果你喜欢非默认的生成体系结构，请选择本机或兼容工具命令提示符之一，以指定主机和目标体系结构。

打开“开发人员命令提示符”窗口的更快方法是在桌面搜索框中输入“开发人员命令提示符”，然后选择所需的结果。

## <a name="developer_command_file_locations"></a> 开发人员命令文件位置

如果想要在现有命令提示符窗口中设置生成体系结构环境，则可以使用安装程序创建的命令文件之一（批处理文件）来设置所需的环境。 建议在新的命令提示符窗口中执行此操作，不建议稍后在同一命令窗口中切换环境。 这些文件的位置取决于安装的 Visual Studio 的版本，以及在安装期间选择的位置和命名。 对于 Visual Studio 2019，64 位计算机上的典型安装位置位于 \Program Files (x86)\Microsoft Visual Studio\2019\*，其中“edition”可能是 Community、Professional、Enterprise、BuildTools 或你提供的其他名称。 Visual Studio 2017 的位置与此类似。 对于 Visual Studio 2015，典型安装位置位于 \Program Files (x86)\Microsoft Visual Studio 14.0 中。

主开发人员命令提示符命令文件 (VsDevCmd.bat) 位于安装目录的 Common7\Tools 子目录中。 如果未指定任何参数，则会将环境、主机和目标生成体系结构设置为使用 32 位 x86 本机工具生成 32 位 x86 代码。

根据处理器体系结构、Visual Studio 工作负载和已安装的选项，还可以使用其他命令文件来设置特定的生成体系结构。 在 Visual Studio 2017 和 Visual Studio 2019 中，它们位于 Visual Studio 安装目录的 VC\Auxiliary\Build 子目录中。 在 Visual Studio 2015 中，位于安装目录的 VC、VC\bin 或 VC\bin\\ 子目录中，其中“architectures”是本机或兼容编译器选项。 这些命令文件设置默认参数并调用 VsDevCmd.bat 以设置指定的生成体系结构环境。 典型安装可能包括以下命令文件：

|命令文件|主机和目标体系结构|
|---|---|
|**vcvars32.bat**| 使用 32 位 x86 本机工具生成 32 位 x86 代码。|
|**vcvars64.bat**| 使用 64 位 x64 本机工具生成 64 位 x64 代码。|
|**vcvarsx86_amd64.bat**| 使用 32 位 x86 本机兼容工具生成 64 位 x64 代码。|
|**vcvarsamd64_x86.bat**| 使用 64 位 x64 本机兼容工具生成 32 位 x86 代码。|
|**vcvarsx86_arm.bat**| 使用 32 位 x86 本机兼容工具生成 ARM 代码。|
|**vcvarsamd64_arm.bat**| 使用 64 位 x64 本机兼容工具生成 ARM 代码。|
|**vcvarsall.bat**| 使用参数指定主机和目标体系结构，以及 SDK 和平台选项。 有关支持的选项列表，请使用“/help”参数进行调用。|

> [!CAUTION]
> vcvarsall.bat 文件和其他 Visual Studio 命令文件可能因计算机不同而有差异。 不要使用另一台计算机中的文件替换丢失或损坏的 vcvarsall.bat 文件。 重新运行 Visual Studio 安装程序以替换丢失的文件。
>
> vcvarsall.bat 文件在不同的版本中也会有所不同。 如果安装了当前版本 Visual Studio 的计算机上也安装了 Visual Studio 的早期版本，则不要在同一命令提示符窗口中运行不同版本的 vcvarsall.bat 或其他 Visual Studio 命令文件。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在现有命令窗口中使用开发人员工具

在现有命令窗口中指定特定生成体系结构的最简单方法是使用 vcvarsall.bat 文件。 可使用 vcvarsall.bat 通过设置环境变量来实现以下操作：配置用于本机 32 位或 64 位编译或者用于 x86、x64 或 ARM 处理器的兼容编译的命令行；以 Microsoft Store、通用 Windows 平台或 Windows 桌面平台为目标；指定要使用的 Windows SDK；以及指定平台工具集版本。 如果未提供任何参数，vcvarsall.bat 将配置环境变量以使用当前面向 x86 Windows 桌面版的 32 位本机编译器。 但是，你可以使用该编译器来配置任何本机工具或兼容编译器工具。 如果指定的编译器配置在生成计算机体系结构上未安装或不可用，则会显示一条错误消息。

### <a name="vcvarsall-syntax"></a>vcvarsall 语法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=**_vcversion_]

architecture<br/>
此可选参数指定要使用的主机和目标体系结构。 如果未指定体系结构，则使用默认生成环境。 支持以下参数：

|architecture|编译器|主机计算机体系结构|生成输出（目标）体系结构|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位本机|x86、x64|x86|
|**x86\_amd64** 或 **x86\_x64**|x86 跨平台上的 x64|x86、x64|X64|
|**x86_arm**|x86 跨平台上的 ARM|x86、x64|ARM|
|**x86_arm64**|x86 跨平台上的 ARM64|x86、x64|ARM64|
|“amd64”或“x64”|x64 64 位本机编译器|X64|X64|
|**amd64\_x86** 或 **x64\_x86**|x64 跨平台上的 x86|X64|x86|
|**amd64\_arm** 或 **x64\_arm**|x64 跨平台上的 ARM|X64|ARM|
|**amd64\_arm64** 或 **x64\_arm64**|x64 跨平台上的 ARM64|X64|ARM64|

platform_type<br/>
可选择使用此参数指定“store”或“uwp”作为平台类型。 默认情况下，环境设置为生成桌面或控制台应用。

winsdk_version<br/>
（可选）指定要使用的 Windows SDK 的版本。 默认情况下，使用最新安装的 Windows SDK。 若要指定 Windows SDK 版本，可使用完整的 Windows 10 SDK 编号，例如“10.0.10240.0”，或指定“8.1”以使用 Windows 8.1 SDK。

vcversion<br/>
（可选）指定要使用的 Visual Studio 编译器工具集。 默认情况下，环境设置为使用当前的 Visual Studio 编译器工具集。 可使用“-vcvars_ver=14.0”指定 Visual Studio 2015 编译器工具集，或使用“-vcvars_ver=15.0”指定 Visual Studio 2017 编译器工具集。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>在现有命令提示符窗口中设置生成环境

1. 在命令提示符处，使用 CD 命令更改为 Visual Studio 安装目录。 然后，再次使用 CD 更改为包含特定于配置的命令文件的子目录。 对于 Visual Studio 2017 和 Visual Studio 2019，这是 VC\Auxiliary\Build 子目录。 对于 Visual Studio 2015，请使用 VC 子目录。

1. 输入用于首选开发人员环境的命令。 例如，若要使用最新的 Windows SDK 和 Visual Studio 2019 编译器工具集在 64 位平台上为 UWP 生成 ARM 代码，请使用以下命令行：

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>创建自己的命令提示符快捷方式

如果打开现有开发人员命令提示符快捷方式之一的“属性”对话框，则可以看到使用的命令目标。 例如，“VS 2019 的 x64 本机工具命令提示符”快捷方式的目标如以下所示：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

特定于体系结构的批处理文件设置“architecture”参数并调用 vcvarsall.bat。 可以将相同的附加选项传递给这些批处理文件，就像传递给 vcvarsall.bat 一样，或者可以直接调用 vcvarsall.bat。 若要为自己的命令快捷方式指定参数，请用双引号将其添加到命令末尾。 例如，要使用最新的 Windows SDK 和早于当前版本的编译器工具集，在 64 位平台上为 UWP 生成 ARM 代码的快捷方式，需要指定版本号。 在快捷方式中使用类似此命令目标的内容：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=15.0"`

必须调整路径以反映 Visual Studio 安装目录。 vcvarsall.bat 文件包含有关特定版本号的其他信息。

## <a name="command-line-tools"></a>命令行工具

若要在命令行上生成 C/C++ 项目，可使用 Visual Studio 提供的以下命令行工具：

[CL](reference/compiling-a-c-cpp-program.md)<br/>
使用编译器 (cl.exe) 可编译源代码文件，并将其链接到应用、库和 DLL 中。

[链接](reference/linking.md)<br/>
使用链接器 (link.exe) 可将已编译的对象文件和库链接到应用和 DLL 中。

[MSBuild](msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 和项目文件 (.vcxproj) 配置生成并间接调用该工具集。 这相当于在 Visual Studio IDE 中运行“生成”项目或“生成解决方案”命令。 从命令行运行 MSBuild 是一种高级方案，通常不建议使用。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
将 DEVENV (devenv.exe) 与命令行开关（例如，“/Build”或“/Clean”）结合使用可在不显示 Visual Studio IDE 的情况下执行某些生成命令。 一般来说，这比直接使用 msbuild 要好，因为可以让 Visual Studio 处理 msbuild 的复杂操作。

[NMAKE](reference/nmake-reference.md)<br/>
在 Windows 上使用 NMAKE (nmake.exe) 基于传统的生成文件生成 C++ 项目。

在命令行上生成时，F1 命令不可用于即时帮助。 相反，可使用搜索引擎获取有关警告、错误和消息的信息，也可以使用脱机帮助文件。 若要在 [docs.microsoft.com](https://docs.microsoft.com/cpp/) 中使用搜索，请在页面顶部的搜索框中输入搜索字符串。

## <a name="in-this-section"></a>本节内容

文档的此部分中的文章显示了如何在命令行上生成应用、介绍了如何自定义命令行生成环境以使用 64 位工具集并面向 x86、x64 和 ARM 平台，以及演示了如何使用命令行生成工具 MSBuild 和 NMAKE。

[演练：在命令行上编译本机 C++ 程序](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供显示了如何在命令行上创建和编译简单 C++ 程序的示例。

[演练：在命令行上编译 C 程序](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
介绍了如何编译采用 C 编程语言编写的程序。

[演练：在命令行上编译 C++/CLI 程序](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
介绍了如何创建和编译使用 .NET Framework 的 C++/CLI 程序。

[演练：在命令行上编译 C++/CX 程序](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
介绍了如何创建和编译使用 Windows 运行时的 C++/CX 程序。

[为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
介绍了如何启动“命令提示符”窗口，在该窗口中，已通过使用 32 位或 64 位工具集为面向 x86、x64 和 ARM 平台的命令行生成设置所需的环境变量。

[NMAKE 参考](reference/nmake-reference.md)<br/>
提供指向介绍了 Microsoft 程序维护实用工具 (NMAKE.EXE) 的文章的链接。

[命令行上的 MSBuild - C++](msbuild-visual-cpp.md)<br/>
提供指向探讨如何从命令行使用 msbuild.exe 的文章的链接。

## <a name="related-sections"></a>相关章节

[/MD、/MT、/LD（使用运行时库）](reference/md-mt-ld-use-run-time-library.md)<br/>
介绍了如何使用这些编译器选项来使用“Debug”或“Release”运行时库。

[C/C++ 编译器选项](reference/compiler-options.md)<br/>
提供指向探讨 C 和 C++ 编译器选项和 CL.exe 的文章的链接。

[MSVC 链接器选项](reference/linker-options.md)<br/>
提供指向探论链接器选项和 LINK.exe 的文章的链接。

[其他 MSVC 生成工具](reference/c-cpp-build-tools.md)<br/>
提供指向 Visual Studio 中包括的 C/C++ 生成工具的链接。

## <a name="see-also"></a>请参阅

[项目和生成系统](projects-and-build-systems-cpp.md)