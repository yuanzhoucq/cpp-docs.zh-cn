---
title: 在命令行上生成 C/c + + 代码 |Microsoft 文档
ms.custom: conceptual
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1e02ea59ffc5a4ece71d2790b2ebb6a953ed682
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="build-cc-code-on-the-command-line"></a>在命令行上生成 C/c + + 代码

可以通过使用 Visual Studio 中包含的工具来生成命令行上的 C 和 c + + 应用程序。

## <a name="how-to-get-the-command-line-tools"></a>如何获取命令行工具

当你选择其中一个 c + + 工作负荷在 Visual Studio 安装程序时，它会安装 Visual Studio*平台工具集*。 平台工具集已针对特定的 Visual Studio 版本，包括 C/c + + 编译器、 链接、 汇编程序，和其他生成工具，以及匹配的库的所有 C 和 c + + 工具。 你可以在命令行中，使用所有这些工具和它们还内部使用的 Visual Studio IDE。 有单独的 x86 承载和 x64 托管编译器和工具来生成代码，为 x86、 x64、 ARM 和 ARM64 目标。 每个组用于对特定的主机和目标生成结构的工具存储在其自己的目录。

若要正常工作，这些工具需要设置几个特定的环境变量。 这些用于将其添加到路径以及设置包括文件、 库文件和 SDK 的位置。 为了能够轻松地设置这些环境变量，则安装程序创建自定义*命令文件*，或批处理文件，在安装过程。 你可以在命令提示符窗口，以设置特定的主机和目标生成体系结构、 Windows SDK 版本、 目标平台和平台工具集来运行这些命令文件之一。 为方便起见，安装程序还将创建快捷方式在开始菜单 (或在 Windows 上的起始页 8.x)，开始通过使用这些命令文件，使所有必需的环境变量设置好可供使用的开发人员命令提示符窗口。

必需的环境变量是特定于你安装你选择，并可能因产品更新或升级已更改的生成体系结构。 因此，我们强烈建议你而不是自己 Windows 中设置环境变量使用的已安装的命令提示符快捷方式或命令文件之一。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。

命令行工具集、 命令文件和安装的命令提示符快捷方式取决于你计算机的处理器和在安装过程中选择的选项。 在最低限度上，安装的 32 位 x86 承载工具生成 32 位 x86 本机代码，并跨生成 64 位 x64 本机代码的工具。 如果你有 64 位 Windows，还会安装 64 位 x64 托管工具生成 64 位本机代码和跨生成 32 位本机代码的工具。 如果你选择安装可选的 c + + 通用 Windows 平台工具，会同时安装生成 ARM 代码的 32 位和 64 位本机工具。 其他工作负荷可能会安装其他工具。

## <a name="developer-command-prompt-shortcuts"></a>开发人员命令提示符快捷方式

开始菜单中的特定于版本的 Visual Studio 文件夹中安装的命令提示符快捷方式。 下面是基本的命令提示符快捷方式和它们支持的生成体系结构的列表：

- **开发人员命令提示**-设置要使用 32 位、 x86 本机工具来生成 32 位、 x86 本机代码的环境。
- **x86 本机工具命令提示**-设置要使用 32 位、 x86 本机工具来生成 32 位、 x86 本机代码的环境。
- **x64 本机工具命令提示**-设置环境以使用 64 位，x64 本机工具来生成 64 位，x64 本机代码。
- **x86_x64 兼容工具命令提示**-设置要使用 32 位、 x86 本机工具来生成 64 位，x64 本机代码的环境。
- **x64_x86 兼容工具命令提示**-设置环境以使用 64 位，x64 本机工具来生成 32 位、 x86 本机代码。

如果你设置一个，具体取决于你已安装的 Visual Studio 的版本和安装昵称情况下会有所不同的实际开始菜单文件夹名称和快捷名称。 例如，如果你有 Visual Studio 2017 年 1 安装，并且您已给定它安装别名的*预览*，名为开发人员命令提示符快捷方式**VS 2017 （预览版）的开发人员命令提示符**，名为的文件夹中**Visual Studio 2017**。

如果已安装[生成 Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931) （其中还介绍了 Visual Studio 2015 Update 3 编译器工具集），只有特定于体系结构的本机或跨工具开发人员命令提示安装选项以及不常规**开发人员命令提示**快捷方式。

<a name="developer_command_prompt"></a>
### <a name="to-open-a-developer-command-prompt-window"></a>若要打开开发人员命令提示符窗口

1. 在桌面上，打开 Windows**启动**菜单上，，然后进行滚动以查找并打开你的 Visual Studio 版本的文件夹，例如， **Visual Studio 2017**。 在 Visual Studio 的某些较旧版本，快捷方式是调用的子文件夹中**Visual Studio Tools**。

1. 在文件夹中，选择**开发人员命令提示**你的 Visual Studio 版本。 此快捷方式启动使用 32 位、 x86 本机工具的默认生成体系结构来生成 32 位、 x86 本机代码的开发人员命令提示符窗口。 如果你愿意非默认生成体系结构，选择一个本机或跨工具命令提示指定的主机和目标体系结构。

打开开发人员命令提示符窗口的速度更快方法是输入*开发人员命令提示*在桌面搜索框中，然后选择所需的结果。

## <a name="developer-command-files-and-locations"></a>开发人员命令文件和位置

如果想要在现有的命令提示符窗口中设置生成体系结构环境，你可以使用的命令文件之一 （批处理文件） 安装程序创建的设置所需的环境。 我们仅建议你执行此操作在新的命令提示符窗口，并且我们不建议你在同一命令窗口中的更高版本交换机环境。 这些文件的位置取决于你已安装的 Visual Studio 的版本和位置和命名您在安装过程所做的选择。 对于 Visual Studio 2017，64 位计算机上的典型的安装位置位于 \Program 文件 (x86) \Microsoft Visual Studio\2017\\*版本*，其中*版本*可能社区Professional、 Enterprise、 BuildTools 或你提供的另一个名称。 对于 Visual Studio 2015，典型的安装位置是位于 \Program Files (x86) \Microsoft Visual Studio 14.0。

主开发人员命令提示符命令文件，VsDevCmd.bat，位于 Common7\Tools 的安装目录的子目录中。 当未指定参数，这将设置环境的主机和目标生成将使用 32 位 x86 本机工具来生成 32 位 x86 体系结构代码。

其他命令文件都可以设置特定的生成体系结构，具体取决于处理器体系结构的 Visual Studio 工作负荷和已安装的选项。 在 Visual Studio 2017，这些磁盘位于 Visual Studio 安装目录的 VC\Auxiliary\Build 子目录中。 在 Visual Studio 2015 中，这些建议位于 VC、 VC\bin 或 VC\bin\\*体系结构*安装目录的子目录其中*体系结构*是本机之一或跨编译器选项。 这些命令文件设置默认参数，并调用 VsDevCmd.bat 设置指定的生成体系结构环境。 典型的安装可能包括这些命令文件：

|命令文件|主机和目标体系结构|
|---|---|
|**vcvars32.bat**| 使用 32 位 x86 本机工具来生成 32 位 x86 代码。|
|**vcvars64.bat**| 使用 64 位 x64 本机工具来生成 64 位 x64 代码。|
|**vcvarsx86_amd64.bat**| 使用 32 位 x86 本机跨工具来生成 64 位 x64 代码。|
|**vcvarsamd64_x86.bat**| 使用 64 位 x64 本机跨工具来生成 32 位 x86 代码。|
|**vcvarsx86_arm.bat**| 使用 32 位 x86 本机跨工具生成 ARM 代码。|
|**vcvarsamd64_arm.bat**| 使用 64 位 x64 本机跨工具来生成 ARM 代码。|
|**vcvarsall.bat**| 使用参数来指定主机和目标体系结构，以及 SDK 和平台选择。 有关支持的选项的列表，调用通过使用 **/帮助**参数。|

> [!CAUTION]
> Vcvarsall.bat 文件和其他 Visual Studio 命令文件异计算机到计算机。 不要使用另一台计算机中的文件替换丢失或损坏的 vcvarsall.bat 文件。 重新运行 Visual Studio 安装程序，以替换丢失的文件。
>
> vcvarsall.bat 文件在不同的版本中也会有所不同。 如果还具有 Visual Studio 的早期版本的计算机上安装 Visual Studio 的当前版本，不能运行 vcvarsall.bat 或另一个 Visual Studio 命令文件在同一命令提示符窗口中的不同版本中。

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>在现有的命令窗口中使用的开发人员工具

在现有的命令窗口中指定特定生成体系结构的最简单方法是使用 vcvarsall.bat 文件。 你可以使用 vcvarsall.bat 设置环境变量以配置适用于本机的 32 位或 64 位编译，或为 x86、 x64 或 ARM 处理器的交叉编译命令行若要面向 Microsoft 应用商店，通用 Windows 平台上或 Windows 桌面平台;若要指定的 Windows SDK，可使用;并指定的平台工具集版本。 如果未不提供任何参数，vcvarsall.bat 将配置环境变量以供使用当前的 32 位本机编译器面向 x86 的 Windows 桌面目标。 但是，你可以使用它来配置任何本机或跨编译器工具。 如果指定的编译器配置，未安装或在你的生成计算机体系结构上不可用，将显示一条错误消息。

### <a name="vcvarsall-syntax"></a>vcvarsall 语法

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*体系结构*<br/>
此可选参数指定将使用主机和目标体系结构。 如果*体系结构*未指定，则使用默认生成环境。 支持这些自变量：

|*体系结构*|编译器|主机计算机体系结构|生成输出 （目标） 体系结构|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32 位本机|x86、x64|x86|
|**x86\_amd64**或**x86\_x64**|x86 跨平台上的 x64|x86、x64|X64|
|**x86_arm**|x86 跨平台上的 ARM|x86、x64|ARM|
|**x86_arm64**|X86 跨平台上的 ARM64|x86、x64|ARM64|
|**amd64**或**x64**|x64 64 位本机编译器|X64|X64|
|**amd64\_x86**或**x64\_x86**|x64 上的 x86 跨|X64|x86|
|**amd64\_arm**或**x64\_arm**|平台 x64 兼容上的 ARM|X64|ARM|
|**amd64\_arm64**或**x64\_arm64**|在 x64 兼容 ARM64|X64|ARM64|

*platform_type*<br/>
此可选参数允许你指定**存储**或**uwp**作为平台类型。 默认情况下，环境设置为生成桌面或控制台应用。

*winsdk_version*<br/>
（可选） 指定要使用的 Windows sdk 的版本。 默认情况下，使用最新安装的 Windows SDK。 若要指定的 Windows SDK 版本，可以使用完整的 Windows 10 SDK 数字，如**10.0.10240.0**，或指定**8.1**若要使用 Windows 8.1 SDK。

*vcversion*<br/>
（可选） 指定要使用 Visual Studio 编译器工具集。 默认情况下，环境设置为使用当前的 Visual Studio 2017 编译器工具集。 使用 **-vcvars_ver = 14.0**指定 Visual Studio 2015 编译器工具集。

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>若要将现有的命令提示符窗口中的生成环境设置

1. 在命令提示符下，使用 CD 命令更改为 Visual Studio 安装目录。 然后，再次使用 CD 更改为包含的配置特定命令文件的子目录。 对于 Visual Studio 自 2017 年 1，这是 VC\Auxiliary\Build 子目录。 对于 Visual Studio 2015 中，使用 VC 子目录。

1. 适用于你首选的开发人员环境输入命令。 例如，若要使用最新的 Windows SDK 和 Visual Studio 2017 RTM 编译器工具集生成适用于 UWP 在 64 位平台上 ARM 代码，请使用此命令行：

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>创建你自己的命令提示符快捷方式

如果您打开一个现有的开发人员命令提示符快捷方式的属性对话框，你可以看到使用的命令目标。 例如，针对**x64 本机工具命令提示的 VS 2017**快捷方式是类似于：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

特定于体系结构的批处理文件集*体系结构*参数并调用 vcvarsall.bat。 可以将相同的其他选项传递给这些批处理文件中，如将传递给 vcvarsall.bat，或只是可以直接调用 vcvarsall.bat 中。 若要指定参数的命令快捷方式，请将它们添加到双引号中的命令的末尾。 例如，若要设置的快捷方式，若要生成 ARM 代码适用于 UWP 在 64 位平台上使用最新的 Windows SDK 和 Visual Studio 2017 RTM 编译器工具集，使用类似此命令目标中，在您的快捷方式：

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

你必须调整以反映你的 Visual Studio 安装目录的路径。

## <a name="command-line-tools"></a>命令行工具

若要在命令行上生成 C/c + + 项目，Visual Studio 可以提供这些命令行工具：

[CL](../build/reference/compiling-a-c-cpp-program.md)<br/>
使用编译器 (cl.exe) 可编译源代码文件，并将其链接到应用、库和 DLL 中。

[链接](../build/reference/linking.md)<br/>
使用链接器 (link.exe) 可将已编译的对象文件和库链接到应用和 DLL 中。

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
使用 MSBuild (msbuild.exe) 生成 Visual c + + 项目和 Visual Studio 解决方案。 这相当于运行**生成**项目或**生成解决方案**命令在 Visual Studio IDE 中。

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
将 DEVENV (devenv.exe) 与命令行开关结合-例如， **/内部**或 **/清理**-执行某些生成命令而不显示 Visual Studio IDE。

[NMAKE](../build/nmake-reference.md)<br/>
使用 NMAKE (nmake.exe) 可自动执行使用传统的生成文件生成 Visual c + + 项目的任务。

在命令行上生成时，F1 命令不可用的即时帮助。 相反，你可以使用搜索引擎以获取有关警告、 错误和消息的信息，或者可以使用脱机帮助文件。 若要使用搜索范围[docs.microsoft.com](https://docs.microsoft.com/cpp/)，在页面顶部的搜索框中输入搜索字符串。

## <a name="in-this-section"></a>本节内容

文档的此部分中的文章显示了如何在命令行上生成应用、介绍了如何自定义命令行生成环境以使用 64 位工具集并面向 x86、x64 和 ARM 平台，以及演示了如何使用命令行生成工具 MSBuild 和 NMAKE。

[演练：在命令行上编译本机 C++ 程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
提供显示了如何在命令行上创建和编译简单 C++ 程序的示例。

[演练： 编译 C 程序命令行上](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
介绍了如何编译采用 C 编程语言编写的程序。

[演练：在命令行上编译 C++/CLI 程序](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
介绍了如何创建和编译使用 .NET Framework 的 C++/CLI 程序。

[演练：在命令行上编译 C++/CX 程序](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
介绍了如何创建和编译使用 Windows 运行时的 C++/CX 程序。

[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
描述如何启动但不包含必需的环境变量设置为命令行生成面向 x86、 x64 和 ARM 平台，通过使用 32 位或 64 位工具集的命令提示符窗口。

[NMAKE 参考](../build/nmake-reference.md)<br/>
提供指向介绍了 Microsoft 程序维护实用工具 (NMAKE.EXE) 的文章的链接。

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
提供指向探讨如何使用 MSBuild.EXE 的文章的链接。

## <a name="related-sections"></a>相关章节

[/MD、/MT、/LD（使用运行时库）](../build/reference/md-mt-ld-use-run-time-library.md)<br/>
介绍了如何使用这些编译器选项来使用“Debug”或“Release”运行时库。

[C/c + + 编译器选项](../build/reference/compiler-options.md)<br/>
提供指向探讨 C 和 C++ 编译器选项和 CL.exe 的文章的链接。

[链接器选项](../build/reference/linker-options.md)<br/>
提供指向探论链接器选项和 LINK.exe 的文章的链接。

[C/C++ 生成工具](../build/reference/c-cpp-build-tools.md)<br/>
提供指向 C/c + + 生成 Visual Studio 中包含的工具。

## <a name="see-also"></a>请参阅

[生成 C/C++ 程序](../build/building-c-cpp-programs.md)