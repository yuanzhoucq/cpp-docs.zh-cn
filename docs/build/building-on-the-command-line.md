---
title: 使用命令行-Visual Studio 中的 MSVC 工具集
description: 使用 MicrosoftC++从 Visual Studio IDE 外部命令行编译器工具链 （msvc） 编写。
ms.custom: conceptual
ms.date: 12/10/2018
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 21d1c9063a1d6dd154de8d2caca913ea3fd0ce37
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342158"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>使用命令行中的 MSVC 工具集

您可以生成 C 和C++使用 Visual Studio 中包含的工具在命令行上的应用程序。 此外可以将其作为独立包从下载的编译器工具集[Visual Studio 2017 生成工具](https://go.microsoft.com/fwlink/p/?linkid=875721)。

## <a name="how-to-use-the-command-line-tools"></a>如何使用命令行工具

当你选择的一个C++工作负荷在 Visual Studio 安装程序，它会安装 Visual Studio*平台工具集*。 平台工具集具有所有 C 和C++适用于特定的 Visual Studio 版本，包括 C 工具 /C++编译器、 链接器和组装器，其他生成工具，以及匹配的库。 可以使用所有这些工具在命令行中，并且它们还内部使用的 Visual Studio IDE。 有单独的 x86 承载和 x64 托管编译器和工具，用于构建代码的 x86、 x64、 ARM 和 ARM64 目标。 每个组的特定主机和目标生成体系结构工具存储在其自己的目录。

安装的编译器工具集取决于您计算机的处理器和在安装过程中选择的选项。 至少安装了 32 位 x86 承载的工具生成 32 位 x86 本机代码和跨生成 64 位 x64 本机代码的工具。 如果您有 64 位 Windows，还会安装的 64 位 x64 托管工具生成 64 位本机代码和跨生成 32 位本机代码的工具。 如果您选择安装可选的C++通用 Windows 平台工具，然后生成 ARM 代码的 32 位和 64 位本机工具还会安装。 其他工作负荷可能安装其他工具。

## <a name="environment-variables-and-developer-command-prompts"></a>环境变量和开发人员命令提示

若要正常工作，工具需要多个特定的环境变量设置。 这些用于将它们添加到路径以及设置包括文件、 库文件和 SDK 位置。 为了能够轻松地设置这些环境变量，安装程序创建自定义*命令文件*，或批处理文件，在安装过程中。 若要设置特定的主机和目标生成体系结构、 Windows SDK 版本中，目标平台和平台工具集的命令提示符窗口中，可以运行这些命令文件之一。 为方便起见，安装程序还在你开始通过使用这些命令文件，使所有必需的环境变量设置并可供使用的开发人员命令提示符窗口的开始菜单中创建快捷方式。

必需的环境变量是特定安装以及生成体系结构选择，并可能因产品更新或升级已更改。 因此，我们强烈建议而不是自己在 Windows 中设置环境变量使用已安装的命令提示符快捷方式或命令文件之一。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。

## <a name="developer_command_prompt_shortcuts"></a> 开发人员命令提示符快捷方式

在开始菜单中的特定于版本的 Visual Studio 文件夹中安装的命令提示符快捷方式。 下面是基本的命令提示符快捷方式和它们支持的生成体系结构的列表：

- **开发人员命令提示**-设置要使用 32 位、 x86 本机工具来生成 32 位、 x86 本机代码的环境。
- **x86 本机工具命令提示符**-设置要使用 32 位、 x86 本机工具来生成 32 位、 x86 本机代码的环境。
- **x64 本机工具命令提示符**-设置要使用 64 位 x64 本机工具来生成 64 位，x64 本机代码的环境。
- **x86_x64 兼容工具命令提示**-设置要使用 32 位、 x86 本机工具来生成 64 位，x64 本机代码的环境。
- **x64_x86 交叉工具命令提示**-设置要使用 64 位 x64 本机工具来生成 32 位、 x86 本机代码的环境。

如果你设置一个，具体取决于已安装的 Visual Studio 的版本和安装昵称会有所不同实际的开始菜单文件夹和快捷方式名称。 例如，如果已安装，Visual Studio 2017 并且您已给定其安装别名的*预览版*，名为开发人员命令提示符快捷方式**VS 2017 （预览版）的开发人员命令提示**，在名为的文件夹中**Visual Studio 2017**。

如果已安装[Visual Studio 2017 生成工具](https://go.microsoft.com/fwlink/p/?linkid=875721)（还包括 Visual Studio 2015 Update 3 编译器工具集） 时，只有特定于体系结构的本机或跨工具开发人员命令提示安装选项以及不常规**开发人员命令提示**快捷方式。

## <a name="developer_command_prompt"></a> 若要打开开发人员命令提示窗口

1. 在桌面上，打开 Windows**启动**菜单上，，然后进行滚动以查找并打开你的 Visual Studio 版本的文件夹，如**Visual Studio 2017**。 在某些较旧版本的 Visual Studio 中，快捷方式位于名为的子文件夹**Visual Studio Tools**。

1. 在文件夹中，选择**开发人员命令提示**你的 Visual Studio 版本。 此快捷方式启动使用默认的生成体系结构的 32 位、 x86 本机工具来生成 32 位、 x86 本机代码的开发人员命令提示符窗口。 如果需要非默认的生成体系结构，选择一个本机或跨工具命令提示指定的主机和目标体系结构。

若要打开开发人员命令提示窗口的实现更快方法是输入*开发人员命令提示*在桌面搜索框中，然后选择所需的结果。

## <a name="developer_command_file_locations"></a> 开发人员命令文件位置

如果想要在现有的命令提示符窗口中设置生成体系结构环境，可以使用安装程序创建命令文件 （批处理文件） 的一个设置所需的环境。 我们仅建议您执行此操作在新的命令提示符窗口中，并且我们不建议你在相同的命令窗口中的更高版本切换环境。 这些文件的位置取决于已安装的 Visual Studio 的版本和位置和命名在安装过程中所做的选择。 对于 Visual Studio 2017 中，在 64 位计算机上的典型安装位置位于 \Program 文件 (x86) \Microsoft Visual Studio\2017\\*edition*，其中*edition*可能是社区，专业版、 企业版、 BuildTools 或所提供的另一个名称。 对于 Visual Studio 2015，典型的安装位置是 \Program 文件 (x86) \Microsoft Visual Studio 14.0。

主要开发人员命令提示符的命令文件 VsDevCmd.bat，位于安装目录的 Common7\Tools 子目录中。 当未指定任何参数，这将设置环境和主机和目标构建体系结构使用 32 位 x86 本机工具来生成 32 位 x86 代码。

其他命令文件是可用于设置特定的生成体系结构，具体取决于处理器体系结构的 Visual Studio 工作负载和已安装的选项。 在 Visual Studio 2017 中，这些磁盘位于 Visual Studio 安装目录的 VC\Auxiliary\Build 子目录中。 在 Visual Studio 2015 中，这些建议位于 VC、 VC\bin 或 VC\bin\\*体系结构*子目录的安装目录，其中*体系结构*是一个本机或跨编译器选项。 这些命令文件设置默认参数，并调用 VsDevCmd.bat 设置指定的生成体系结构环境。 典型安装可能会包括这些命令的文件：

|命令文件|主机和目标体系结构|
|---|---|
|**vcvars32.bat**| 使用 32 位 x86 本机工具来生成 32 位 x86 代码。|
|**vcvars64.bat**| 使用 64 位 x64 本机工具来生成 64 位 x64 代码。|
|**vcvarsx86_amd64.bat**| 使用 32 位 x86 本机跨工具生成 64 位 x64 代码。|
|**vcvarsamd64_x86.bat**| 使用 64 位 x64 本机跨工具生成 32 位 x86 代码。|
|**vcvarsx86_arm.bat**| 使用 32 位 x86 本机跨工具生成 ARM 代码。|
|**vcvarsamd64_arm.bat**| 使用 64 位 x64 本机跨工具生成 ARM 代码。|
|**vcvarsall.bat**| 使用参数来指定主机和目标体系结构，以及 SDK 和平台选择。 有关支持的选项的列表，调用通过使用 **/help**参数。|

> [!CAUTION]
> Vcvarsall.bat 文件和其他 Visual Studio 命令文件而异计算机到计算机。 不要使用另一台计算机中的文件替换丢失或损坏的 vcvarsall.bat 文件。 重新运行 Visual Studio 安装程序以替换丢失的文件。
>
> vcvarsall.bat 文件在不同的版本中也会有所不同。 如果还具有 Visual Studio 的早期版本的计算机上安装 Visual Studio 的当前版本，不能运行 vcvarsall.bat 或另一个 Visual Studio 命令文件中的命令提示符窗口中的不同版本。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>使用现有的命令窗口中的开发人员工具

若要在现有命令窗口中指定特定生成体系结构的最简单方法是使用 vcvarsall.bat 文件。 您可以使用 vcvarsall.bat 设置环境变量以配置适用于本机 32 位或 64 位编译，或交叉编译到 x86、 x64 或 ARM 处理器; 在命令行若要面向 Microsoft Store、 通用 Windows 平台或 Windows 桌面平台;若要指定要使用; 的 Windows SDK并指定平台工具集版本。 如果未不提供任何参数，vcvarsall.bat 将配置环境变量的使用当前的 32 位本机编译器的 x86 Windows 桌面目标。 但是，您可以使用它来配置所有的本机或跨编译器工具。 如果指定的编译器配置，未安装或在生成计算机体系结构上不可用，显示一条错误消息。

### <a name="vcvarsall-syntax"></a>vcvarsall 语法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*architecture*<br/>
此可选参数指定要使用的主机和目标体系结构。 如果*体系结构*未指定，则使用默认生成环境。 支持以下参数：

|*architecture*|编译器|主机计算机体系结构|生成输出 （目标） 体系结构|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位本机|x86、x64|x86|
|**x86\_amd64**或**x86\_x64**|在 x86 x64 兼容|x86、x64|X64|
|**x86_arm**|x86 跨平台上的 ARM|x86、x64|ARM|
|**x86_arm64**|X86 跨平台上的 ARM64|x86、x64|ARM64|
|**amd64**或**x64**|x64 64 位本机|X64|X64|
|**amd64\_x86**或**x64\_x86**|在 x64 x86 兼容|X64|x86|
|**amd64\_arm**或**x64\_arm**|ARM 上 x64 兼容|X64|ARM|
|**amd64\_arm64**或**x64\_arm64**|在 x64 兼容 ARM64|X64|ARM64|

*platform_type*<br/>
此可选参数允许您指定**存储**或**uwp**作为平台类型。 默认情况下，环境设置为构建桌面或控制台应用程序。

*winsdk_version*<br/>
（可选） 指定要使用的 Windows SDK 的版本。 默认情况下，使用最新安装的 Windows SDK。 若要指定的 Windows SDK 版本，可以使用完整的 Windows 10 SDK 数字，如**10.0.10240.0**，或指定**8.1**若要使用 Windows 8.1 SDK。

*vcversion*<br/>
（可选） 指定要使用的 Visual Studio 编译器工具集。 默认情况下，环境设置为使用当前的 Visual Studio 2017 编译器工具集。 使用 **-vcvars_ver = 14.0**指定 Visual Studio 2015 编译器工具集。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>若要将现有的命令提示符窗口中的生成环境设置

1. 在命令提示符下，使用 CD 命令切换到 Visual Studio 安装目录。 然后，再次使用 CD 将更改为包含特定于配置的命令文件的子目录。 对于 Visual Studio 2017，这是 VC\Auxiliary\Build 子目录。 对于 Visual Studio 2015 中，使用 VC 子目录。

1. 适用于你首选的开发人员环境输入命令。 例如，若要使用最新的 Windows SDK 和 Visual Studio 2017 RTM 编译器工具集生成适用于 UWP 的 64 位平台上 ARM 代码，请使用此命令行：

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>创建你自己的命令提示符快捷方式

如果您打开一个现有的开发人员命令提示符快捷方式属性对话框，您可以看到使用的命令目标。 例如，为目标**x64 本机工具命令提示 VS 2017**快捷方式是类似的内容：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

特定于体系结构的批处理文件集*体系结构*参数并调用 vcvarsall.bat。 要传递给 vcvarsall.bat，或只是可以直接调用 vcvarsall.bat，可以将相同的其他选项传递到这些批处理文件。 若要指定参数的命令快捷方式，将其添加到双引号中的命令的末尾。 例如，若要设置生成 ARM 代码适用于 UWP 的 64 位平台上使用最新的 Windows SDK 和 Visual Studio 2017 RTM 编译器工具集的一种快捷方式，使用类似此命令目标中您的快捷方式：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

必须调整以反映你的 Visual Studio 安装目录的路径。

## <a name="command-line-tools"></a>命令行工具

若要生成 C /C++在命令行中，Visual Studio 项目提供了这些命令行工具：

[CL](reference/compiling-a-c-cpp-program.md)<br/>
使用编译器 (cl.exe) 可编译源代码文件，并将其链接到应用、库和 DLL 中。

[链接](reference/linking.md)<br/>
使用链接器 (link.exe) 可将已编译的对象文件和库链接到应用和 DLL 中。

[MSBuild](msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 和项目文件 (.vcxproj) 若要配置生成和间接调用该工具集。 这等同于运行**构建**项目或**生成解决方案**命令，在 Visual Studio IDE。 从命令行运行 MSBuild 是一个高级的方案，通常不建议。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
与命令行开关结合将 DEVENV (devenv.exe) — 例如， **/build**或 **/clean**— 执行某些生成命令而不会显示在 Visual Studio IDE。 一般情况下这是首选对使用 MSBuild，因为您可以让 Visual Studio 处理 MSBuild 的复杂性直接。

[NMAKE](reference/nmake-reference.md)<br/>
在 Windows 上使用 NMAKE (nmake.exe) 生成C++项目基于传统的生成文件。

在命令行上生成时，F1 命令不可用的即时帮助。 相反，您可以使用搜索引擎来获取有关警告、 错误和消息的信息，或者可以使用脱机帮助文件。 若要使用搜索范围[docs.microsoft.com](https://docs.microsoft.com/cpp/)，在页面顶部的搜索框中输入搜索字符串。

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
介绍如何启动但不包含必需的环境变量设置为命令行生成面向 x86、 x64 和 ARM 平台，通过使用 32 位或 64 位工具集的命令提示符窗口。

[NMAKE 参考](reference/nmake-reference.md)<br/>
提供指向介绍了 Microsoft 程序维护实用工具 (NMAKE.EXE) 的文章的链接。

[在命令行中的 MSBuildC++](msbuild-visual-cpp.md)<br/>
提供指向讨论如何使用命令行中的 msbuild.exe 的文章。

## <a name="related-sections"></a>相关章节

[/MD、/MT、/LD（使用运行时库）](reference/md-mt-ld-use-run-time-library.md)<br/>
介绍了如何使用这些编译器选项来使用“Debug”或“Release”运行时库。

[C /C++编译器选项](reference/compiler-options.md)<br/>
提供指向探讨 C 和 C++ 编译器选项和 CL.exe 的文章的链接。

[MSVC 链接器选项](reference/linker-options.md)<br/>
提供指向探论链接器选项和 LINK.exe 的文章的链接。

[其他 MSVC 生成工具](reference/c-cpp-build-tools.md)<br/>
提供链接到 C /C++生成 Visual Studio 中包含的工具。

## <a name="see-also"></a>请参阅

[项目和生成系统](projects-and-build-systems-cpp.md)