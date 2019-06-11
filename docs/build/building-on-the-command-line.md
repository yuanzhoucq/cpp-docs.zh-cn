---
title: 使用 MicrosoftC++从命令行工具集
description: 通过 Visual Studio IDE 外部的命令行使用 Microsoft C++ 编译器工具链 (MSVC)。
ms.custom: conceptual
ms.date: 06/06/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: b5e9bf266d79ee86cae84535641a52c7c52be391
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821134"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>使用 MicrosoftC++从命令行工具集

使用包含在 Visual Studio 中的工具，可在命令行上生成 C 和 C++ 应用程序。 Microsoft C++ (MSVC) 编译器工具集也是从独立包作为可下载[Visual Studio 下载](https://visualstudio.microsoft.com/downloads/)页。 它的一部分**用于 Visual Studio 生成工具**包。 您可以选择下载所需的工具C++开发。

## <a name="how-to-use-the-command-line-tools"></a>如何使用命令行工具

在 Visual Studio 安装程序中选择一个 C++ 工作负载时，它会安装 Visual Studio 平台工具集  。 平台工具集具有所有 C 和C++针对特定的 Visual Studio 版本的工具。 这些工具包括 C /C++编译器、 链接器和组装器，其他生成工具和匹配的库。 您可以在命令行中使用所有这些工具。 它们还用于在内部由 Visual Studio IDE。 有单独的 x86 承载和 x64 托管编译器和工具，用于构建 x86、 x64、 ARM 和 ARM64 目标代码。 用于特定主机和目标生成体系结构的每组工具都存储在其自己的目录中。

需要设置几个特定的环境变量，这些工具才能正常运行。 使用这些变量添加到路径，以及设置的工具包括文件、 库文件和 SDK 位置。 为了便于设置这些环境变量，安装程序会在安装期间创建自定义的命令文件或批处理文件  。 您可以运行这些命令文件以设置特定的主机和目标生成体系结构、 Windows SDK 版本和平台工具集之一。 为方便起见，安装程序还在开始菜单中创建快捷方式。 快捷方式的主机和目标的特定组合使用这些命令文件来启动开发人员命令提示符窗口。 这些快捷方式确保所有必需的环境变量设置并可供使用。

必需的环境变量是特定安装以及您选择的生成体系结构。 它们还可能因产品更新或升级更改。 这就是为什么我们建议你使用已安装的命令提示符快捷方式或命令文件，而不是自行设置环境变量。 有关详细信息，请参阅[设置为命令行生成的路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。

工具集、 命令文件和安装的快捷方式取决于您计算机的处理器和在安装期间选择的选项。 始终安装 x86 承载的工具和跨工具，可构建 x86 和 x64 代码。 如果您有 64 位 Windows，还会安装 x64 托管工具和跨工具，可构建 x86 和 x64 代码。 如果您选择的可选C++通用 Windows 平台工具，然后生成 ARM 和 ARM64 代码的 x86 和 x64 工具还会安装。 其他工作负载可能需安装其他工具。

## <a name="developer_command_prompt_shortcuts"></a> 开发人员命令提示符快捷方式

命令提示符快捷方式安装在“开始”菜单中特定于版本的 Visual Studio 文件夹中。 以下是基本命令提示符快捷方式列表以及它们支持的生成体系结构：

- **开发人员命令提示符** - 将环境设置为使用 32 位 x86 本机工具生成 32 位 x86 本机代码。
- **x86 本机工具命令提示符** - 将环境设置为使用 32 位 x86 本机工具生成 32 位 x86 本机代码。
- **x64 本机工具命令提示符** - 将环境设置为使用 64 位 x64 本机工具生成 64 位 x64 本机代码。
- **x86_x64 兼容工具命令提示符** - 将环境设置为使用 64 位 x64 本机工具生成 32 位 x86 本机代码。
- **x64_x86 兼容工具命令提示符** - 将环境设置为使用 64 位 x64 本机工具生成 32 位 x86 本机代码。

::: moniker range=">= vs-2019"

开始菜单文件夹和快捷方式名称会有所不同，具体取决于安装的 Visual Studio 版本。 如果你设置一个，它们也依赖于在安装**昵称**。 例如，假设你已安装 Visual Studio 2019，并且您命名的别名*最新*。 名为开发人员命令提示符快捷方式**VS 2019 （最新版本） 的开发人员命令提示符**，在名为的文件夹**Visual Studio 2019**。

::: moniker-end
::: moniker range="= vs-2017"

开始菜单文件夹和快捷方式名称会有所不同，具体取决于安装的 Visual Studio 版本。 如果你设置一个，它们也依赖于在安装**昵称**。 例如，假设安装 Visual Studio 2017 中，并且你为其指定的昵称*最新*。 名为开发人员命令提示符快捷方式**VS 2017 （最新版本） 的开发人员命令提示**，在名为的文件夹**Visual Studio 2017**。

::: moniker-end
::: moniker range="< vs-2017"

开始菜单文件夹和快捷方式名称会有所不同，具体取决于安装的 Visual Studio 版本。 例如，假定您安装了 Visual Studio 2015。 名为开发人员命令提示符快捷方式**VS 2015 开发人员命令提示**。

::: moniker-end

## <a name="developer_command_prompt"></a> 打开“开发人员命令提示”窗口

1. 在桌面上，打开 Windows“开始”菜单，然后滚动查找并打开 Visual Studio 版本的文件夹，例如“Visual Studio 2019”   。

1. 在该文件夹中，为 Visual Studio 版本选择“开发人员命令提示符”  。 此快捷方式启动开发人员命令提示符窗口，该窗口使用 32 位 x86 本机工具的默认生成体系结构来生成 32 位 x86 本机代码。 如果你喜欢非默认的生成体系结构，请选择本机或兼容工具命令提示符之一，以指定主机和目标体系结构。

对于更快捷的方法来打开开发人员命令提示，输入*开发人员命令提示*桌面搜索框中。 然后，选择所需的结果。

## <a name="developer_command_file_locations"></a> 开发人员命令文件位置

如果想要在现有的命令提示符窗口中设置生成环境，可以使用安装程序创建命令文件之一。 我们建议在新的命令提示符窗口中设置的环境。 我们不建议在同一个命令窗口中的更高版本切换环境。

::: moniker range=">= vs-2019"

命令文件位置取决于版本的 Visual Studio 安装，以及在安装过程中所做的选择。 对于 Visual Studio 2019，64 位系统上的典型安装位置是在\\Program Files (x86)\\Microsoft Visual Studio\\2019年\\*edition*。 *Edition*可能是 Community、 Professional、 Enterprise、 BuildTools 或你提供的另一个别名。

::: moniker-end
::: moniker range="= vs-2017"

命令文件位置取决于版本的 Visual Studio 安装，以及在安装过程中所做的选择。 对于 Visual Studio 2017 中，在 64 位系统上的典型安装位置是在\\Program Files (x86)\\Microsoft Visual Studio\\2017年\\*edition*。 *Edition*可能是 Community、 Professional、 Enterprise、 BuildTools 或你提供的另一个别名。

::: moniker-end
::: moniker range="< vs-2017"

命令文件位置取决于 Visual Studio 版本和安装目录。 对于 Visual Studio 2015 中，典型安装位置是在\\Program Files (x86)\\Microsoft Visual Studio 14.0。

::: moniker-end

主要开发人员命令提示符的命令文件 VsDevCmd.bat，位于 Common7\\Tools 子目录。 当未不指定任何参数时，它会设置环境以使用 x86 本机工具来生成 32 位 x86 代码。

::: moniker range=">= vs-2017"

更多命令文件是可用于设置特定的生成体系结构。 可用的命令文件取决于 Visual Studio 工作负载和已安装的选项。 在 Visual Studio 2017 和 Visual Studio 2019 中，您会发现它们中 VC\\辅助\\生成子目录。

::: moniker-end
::: moniker range="< vs-2017"

更多命令文件是可用于设置特定的生成体系结构。 可用的命令文件取决于 Visual Studio 工作负载和已安装的选项。 在 Visual Studio 2015 中，它们位于 VC，VC\\bin 或 VC\\bin\\*体系结构*子目录，其中*体系结构*是一个本机或跨编译器选项。

::: moniker-end

这些命令文件设置默认参数并调用 VsDevCmd.bat 以设置指定的生成体系结构环境。 典型安装可能包括以下命令文件：

|命令文件|主机和目标体系结构|
|---|---|
|**vcvars32.bat**| 使用 32 位 x86 本机工具生成 32 位 x86 代码。|
|**vcvars64.bat**| 使用 64 位 x64 本机工具生成 64 位 x64 代码。|
|**vcvarsx86_amd64.bat**| 使用 32 位 x86 本机兼容工具生成 64 位 x64 代码。|
|**vcvarsamd64_x86.bat**| 使用 64 位 x64 本机兼容工具生成 32 位 x86 代码。|
|**vcvarsx86_arm.bat**| 使用 32 位 x86 本机兼容工具生成 ARM 代码。|
|**vcvarsamd64_arm.bat**| 使用 64 位 x64 本机兼容工具生成 ARM 代码。|
|**vcvarsall.bat**| 使用参数来指定主机和目标体系结构、 Windows SDK 和平台选择。 有关支持的选项列表，请使用“/help”参数进行调用  。|

> [!CAUTION]
> vcvarsall.bat 文件和其他 Visual Studio 命令文件可能因计算机不同而有差异。 不要使用另一台计算机中的文件替换丢失或损坏的 vcvarsall.bat 文件。 重新运行 Visual Studio 安装程序以替换丢失的文件。
>
> vcvarsall.bat 文件在不同的版本中也会有所不同。 如果安装了当前版本 Visual Studio 的计算机上也安装了 Visual Studio 的早期版本，则不要在同一命令提示符窗口中运行不同版本的 vcvarsall.bat 或其他 Visual Studio 命令文件。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在现有命令窗口中使用开发人员工具

在现有命令窗口中指定特定生成体系结构的最简单方法是使用 vcvarsall.bat 文件。 使用 vcvarsall.bat 设置环境变量以配置适用于本机 32 位或 64 位编译命令行。 参数可以指定交叉编译到 x86、 x64、 ARM、 或 ARM64 处理器。 可以针对 Microsoft Store、 通用 Windows 平台或 Windows 桌面平台。 您甚至可以指定哪些 Windows SDK，若要使用，并选择平台工具集版本。

当使用不带任何参数，vcvarsall.bat 将配置为 32 位 Windows 桌面目标使用当前的 x86 本机编译器的环境变量。 您可以添加参数以配置要使用任何本机或跨编译器工具的环境。 如果指定的配置，未安装，vcvarsall.bat 将显示一条错误消息或在计算机上可用。

### <a name="vcvarsall-syntax"></a>vcvarsall 语法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

architecture <br/>
此可选参数指定要使用的主机和目标体系结构。 如果*体系结构*未指定，则使用默认生成环境。 支持以下参数：

|architecture |编译器|主机计算机体系结构|生成输出（目标）体系结构|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位本机|x86、x64|x86|
|**x86\_amd64** 或 **x86\_x64**|x86 跨平台上的 x64|x86、x64|X64|
|**x86_arm**|x86 跨平台上的 ARM|x86、x64|ARM|
|**x86_arm64**|x86 跨平台上的 ARM64|x86、x64|ARM64|
|“amd64”或“x64”  |x64 64 位本机编译器|X64|X64|
|**amd64\_x86** 或 **x64\_x86**|x64 跨平台上的 x86|X64|x86|
|**amd64\_arm** 或 **x64\_arm**|x64 跨平台上的 ARM|X64|ARM|
|**amd64\_arm64** 或 **x64\_arm64**|x64 跨平台上的 ARM64|X64|ARM64|

platform_type <br/>
可选择使用此参数指定“store”或“uwp”作为平台类型   。 默认情况下，环境设置为生成桌面或控制台应用。

winsdk_version <br/>
（可选）指定要使用的 Windows SDK 的版本。 默认情况下，使用最新安装的 Windows SDK。 若要指定 Windows SDK 版本，可使用完整的 Windows 10 SDK 编号，例如“10.0.10240.0”，或指定“8.1”以使用 Windows 8.1 SDK   。

vcversion <br/>
（可选）指定要使用的 Visual Studio 编译器工具集。 默认情况下，环境设置为使用当前的 Visual Studio 编译器工具集。

::: moniker range=">= vs-2019"

使用 **-vcvars_ver = 14.2 x.yyyyy**来指定特定版本的 Visual Studio 2019 编译器工具集。

使用 **-vcvars_ver = 14.16**指定 Visual Studio 2017 编译器工具集的最新版本。

::: moniker-end
::: moniker range="= vs-2017"

使用 **-vcvars_ver = 14.16**指定 Visual Studio 2017 编译器工具集的最新版本。

使用 **-vcvars_ver = 14.1 x.yyyyy**来指定特定版本的 Visual Studio 2017 编译器工具集。

::: moniker-end

使用 **-vcvars_ver = 14.0**指定 Visual Studio 2015 编译器工具集。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>在现有命令提示符窗口中设置生成环境

1. 在命令提示符处，使用 CD 命令更改为 Visual Studio 安装目录。 然后，再次使用 CD 更改为包含特定于配置的命令文件的子目录。 Visual Studio 2019 和 Visual Studio 2017，请使用*VC\\辅助\\生成*子目录。 对于 Visual Studio 2015 中，使用*VC*子目录。

1. 输入用于首选开发人员环境的命令。 例如，若要使用的最新 Windows SDK 和 Visual Studio 编译器工具集的 64 位平台上构建适用于 UWP 的 ARM 代码使用此命令行：

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>创建自己的命令提示符快捷方式

::: moniker range=">= vs-2019"

打开开发人员命令提示符快捷方式，若要查看使用的命令目标属性对话框。 例如，“VS 2019 的 x64 本机工具命令提示符”快捷方式的目标如以下所示  ：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

打开开发人员命令提示符快捷方式，若要查看使用的命令目标属性对话框。 例如，为目标**x64 本机工具命令提示 VS 2017**快捷方式是类似的内容：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

打开开发人员命令提示符快捷方式，若要查看使用的命令目标属性对话框。 例如，为目标**VS2015 x64 本机工具命令提示符**快捷方式是类似的内容：

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64`

::: moniker-end

特定于体系结构的批处理文件设置“architecture”参数并调用 vcvarsall.bat  。 要传递给 vcvarsall.bat，或只是可以直接调用 vcvarsall.bat，可以将相同的选项传递到这些批处理文件。 若要为自己的命令快捷方式指定参数，请用双引号将其添加到命令末尾。 例如，下面是使用最新的 Windows SDK 的 64 位平台上构建适用于 UWP 的 ARM 代码的快捷方式。 若要使用早期的编译器工具集，指定的版本号。 在快捷方式中使用类似此命令目标的内容：

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.16"`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.0"`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64 -vcvars_ver=12.0`

::: moniker-end

调整以反映你的 Visual Studio 安装目录的路径。 vcvarsall.bat 文件包含有关特定版本号的其他信息。

## <a name="command-line-tools"></a>命令行工具

若要生成 C /C++在命令提示符下，Visual Studio 项目提供了这些命令行工具：

[CL](reference/compiling-a-c-cpp-program.md)<br/>
使用编译器 (cl.exe) 可编译源代码文件，并将其链接到应用、库和 DLL 中。

[链接](reference/linking.md)<br/>
使用链接器 (link.exe) 可将已编译的对象文件和库链接到应用和 DLL 中。

[MSBuild](msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 和项目文件 (.vcxproj) 配置生成并间接调用该工具集。 它等同于运行**构建**项目或**生成解决方案**命令，在 Visual Studio IDE。 从命令行运行 MSBuild 是一种高级的方案，通常不建议。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
将 DEVENV (devenv.exe) 如组合使用命令行开关 **/build**或 **/clean**执行某些生成命令而不会显示在 Visual Studio IDE。 一般情况下，DEVENV 优于 MSBuild 直接使用，因为您可以让 Visual Studio 处理 MSBuild 的复杂性。

[NMAKE](reference/nmake-reference.md)<br/>
在 Windows 上使用 NMAKE (nmake.exe) 基于传统的生成文件生成 C++ 项目。

在命令行上生成时，F1 命令不适用于即时帮助。 相反，可使用搜索引擎获取有关警告、错误和消息的信息，也可以使用脱机帮助文件。 若要使用搜索范围[docs.microsoft.com](https://docs.microsoft.com/cpp/)，在页面顶部使用搜索框中。

## <a name="in-this-section"></a>本节内容

这些文章介绍如何在命令行上生成应用，并介绍如何自定义命令行构建环境。 一些显示如何使用 64 位工具集，以及面向 x86、 x64、 ARM，和 ARM64 平台。 它们还描述了使用命令行生成工具 MSBuild 和 NMAKE。

[演练：在命令行上编译本机 C++ 程序](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供了一个示例演示如何创建和编译的C++命令行上的程序。

[演练：在命令行上编译 C 程序](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
介绍了如何编译采用 C 编程语言编写的程序。

[演练：在命令行上编译 C++/CLI 程序](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
介绍了如何创建和编译使用 .NET Framework 的 C++/CLI 程序。

[演练：在命令行上编译 C++/CX 程序](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
介绍了如何创建和编译使用 Windows 运行时的 C++/CX 程序。

[为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
如何设置环境变量以使用为目标 x86、 x64、 ARM，32 位或 64 位工具集和 ARM64 平台。

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
