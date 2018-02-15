---
title: "在命令行上生成 C/c + + 代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f613c20e0cab45a8eaa802c4c7ba0c6ac391357
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="build-cc-code-on-the-command-line"></a>在命令行上生成 C/c + + 代码

通过使用包含在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的工具，可在命令行上生成 C 和 C++ 应用程序。

当你选择一个中的 c + + 工作负载[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安装程序，它将安装一个工具集，包括 C/c + + 编译器，链接，和其他生成工具。 通过使用这些工具[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]IDE，并且它们还可在命令行。 有单独的 x86 承载和 x64 托管编译器和工具来生成适用于 x86、 x64 和 ARM 目标代码。 每个组用于对特定的主机和目标生成结构的工具存储在其自己的目录。 若要正常工作，这些工具需要多个特定的环境变量以将它们添加到路径并设置包括文件、 库文件和 SDK 位置。 要更加轻松地设置这些环境变量，请安装程序将在安装过程中创建自定义的命令文件，也称为批处理文件。 你可以设置特定的生成体系结构的命令提示符窗口中运行这些命令文件之一。 为方便起见，安装程序还将创建快捷方式在开始菜单 (或在 Windows 上的起始页 8.x)，开始通过使用这些命令文件，使所有必需的环境变量设置好可供使用的开发人员命令提示符窗口。 

必需的环境变量是特定于你安装你选择，并可能因产品更新或升级已更改的生成体系结构。 因此，我们强烈建议你而不是自己 Windows 中设置环境变量使用的已安装的命令提示符快捷方式或命令文件之一。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  

命令行工具集、 命令文件和安装的命令提示符快捷方式取决于你计算机的处理器和在安装过程中选择的选项。 在最低限度上，安装的 32 位 x86 承载工具生成 32 位 x86 本机代码，并跨生成 64 位 x64 本机代码的工具。 如果你有 64 位 Windows，还会安装 64 位 x64 托管工具生成 64 位本机代码和跨生成 32 位本机代码的工具。 如果你选择安装可选的 c + + 通用 Windows 平台工具，会同时安装生成 ARM 代码的 32 位和 64 位本机工具。 其他工作负荷可能会安装其他工具。

<a name="developer_command_prompt_shortcuts"></a>
## <a name="developer-command-prompt-shortcuts"></a>开发人员命令提示符快捷方式

命令提示符快捷方式安装在特定于版本的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]开始菜单中的文件夹。 下面是基本的命令提示符快捷方式和它们支持的生成体系结构的列表：

- **开发人员命令提示**设置环境以使用 32 位、 x86 本机工具来生成 32 位、 x86 本机代码。  
- **x86 本机工具命令提示**设置环境以使用 32 位、 x86 本机工具来生成 32 位、 x86 本机代码。  
- **x64 本机工具命令提示**设置环境以使用 64 位，x64 本机工具来生成 64 位，x64 本机代码。  
- **x86_x64 兼容工具命令提示**设置环境以使用 32 位、 x86 本机工具来生成 64 位，x64 本机代码。  
- **x64_x86 兼容工具命令提示**设置环境以使用 64 位，x64 本机工具来生成 32 位、 x86 本机代码。  

版本而异的实际开始菜单文件夹名称和快捷名称[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]已安装和安装如果你设置一个昵称。 例如，如果你有 Visual Studio 2017 年 1 安装，并且你已为它赋予 15.3 安装昵称，开发人员命令提示符快捷方式名为**VS 2017 (15.3) 的开发人员命令提示符**，名为的文件夹中**Visual Studio 2017**。 

如果已安装[生成 Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931)或[Visual c + + 2015年生成工具](http://landinghub.visualstudio.com/visual-cpp-build-tools)版本，可能仅有特定的本机或跨工具开发人员命令提示符选项。 

<a name="developer_command_prompt"></a>
## <a name="to-open-a-developer-command-prompt-window"></a>若要打开开发人员命令提示符窗口  
  
1.  在桌面上，打开 Windows**启动**菜单上，，然后进行滚动以查找并打开你的 Visual Studio 版本的文件夹，例如， **Visual Studio 2017**。 在 Visual Studio 的某些较旧版本，快捷方式是调用的子文件夹中**Visual Studio Tools**。  
  
2.  在文件夹中，选择**开发人员命令提示**你的 Visual Studio 版本。 此快捷方式启动使用 32 位、 x86 本机工具的默认生成体系结构来生成 32 位、 x86 本机代码的开发人员命令提示符窗口。 如果你愿意非默认生成体系结构，选择一个本机或跨工具命令提示指定的主机和目标体系结构。 

打开开发人员命令提示符窗口的速度更快方法是输入*开发人员命令提示*在桌面搜索框中，然后选择所需的结果。

<a name="developer_command_files"></a>
## <a name="developer-command-files-and-locations"></a>开发人员命令文件和位置

如果想要在现有的命令提示符窗口中设置生成体系结构环境，你可以使用安装程序创建命令文件之一。 这些文件的位置取决于的新版[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]你已安装，并且位置和名称选择在你安装过程中进行。 对于 Visual Studio 2017，64 位计算机上的典型的安装位置位于 \Program 文件 (x86) \Microsoft Visual Studio\2017\\*版本*，其中*版本*可能社区Professional、 Enterprise、 BuildTools 或你提供的另一个名称。 对于 Visual Studio 2015，典型的安装位置是位于 \Program Files (x86) \Microsoft Visual Studio 14.0。 

主开发人员命令提示符命令文件，VsDevCmd.bat，位于 Common7\Tools 的安装目录的子目录中。 如果不指定任何参数，这将设置的环境和版本的体系结构使用 32 位 x86 本机工具来生成 32 位 x86 代码。

其他命令文件是可用于设置特定的生成体系结构，具体取决于处理器体系结构和[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]工作负荷和已安装的选项。 在 Visual Studio 2017，这些位于的 VC\Auxiliary\Build 子目录[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安装目录。 在 Visual Studio 2015 中，这些建议位于 VC、 VC\bin 或 VC\bin\\*体系结构*安装目录的子目录其中*体系结构*程序的本机或跨编译器选项。 这些命令文件设置参数和调用 VsDevCmd.bat 设置指定的生成体系结构环境。 典型的安装可能包括这些命令文件：

- **vcvars32.bat**使用 32 位 x86 本机工具来生成 32 位 x86 代码。  
- **vcvars64.bat**使用 64 位 x64 本机工具来生成 64 位 x64 代码。  
- **vcvarsx86_amd64.bat**使用 32 位 x86 本机跨工具来生成 64 位 x64 代码。  
- **vcvarsamd64_x86.bat**使用 64 位 x64 本机跨工具来生成 32 位 x86 代码。  
- **vcvarsx86_arm.bat**使用 32 位 x86 本机跨工具生成 ARM 代码。  
- **vcvarsamd64_arm.bat**使用 64 位 x64 本机跨工具生成 ARM 代码。  
- **vcvarsall.bat**使用参数来指定主机和目标体系结构，以及 SDK 和平台选择。 使用调用`/help`参数有关的选项列表。  

> [!CAUTION]
>  Vcvarsall.bat 文件和其他命令文件异计算机到计算机。 不要使用另一台计算机中的文件替换丢失或损坏的 vcvarsall.bat 文件。 重新运行[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]安装程序，以替换丢失的文件。  
>   
> vcvarsall.bat 文件在不同的版本中也会有所不同。 如果还了 Visual c + + 的早期版本的计算机上安装 Visual c + + 的当前版本，不能运行 vcvarsall.bat 或另一个命令文件在同一命令提示符窗口中的不同版本中。  
 
在现有的命令窗口中指定特定生成体系结构的最简单方法是使用 vcvarsall.bat 文件。 你可以使用 vcvarsall.bat 设置环境变量以配置适用于本机的 32 位或 64 位编译，或为 x86、 x64 或 ARM 处理器的交叉编译命令行若要面向 Microsoft 应用商店，通用 Windows 平台上或 Windows 桌面平台;若要指定的 Windows SDK，可使用;并指定的平台工具集版本。 如果未不提供任何参数，vcvarsall.bat 将配置环境变量以供使用当前的 32 位本机编译器面向 x86 的 Windows 桌面目标。 但是，你可以使用它来配置任何本机或跨编译器工具。 如果指定的编译器配置，未安装或在你的生成计算机体系结构上不可用，将显示一条错误消息。 下表显示支持的体系结构自变量：  
  
|Vcvarsall.bat 体系结构自变量|编译器|主机计算机体系结构|生成输出体系结构|  
|----------------------------|--------------|----------------------------------|-------------------------------|  
|x86|x86 32 位本机|x86、x64|x86|  
|x86\_amd64 or x86\_x64|x86 跨平台上的 x64|x86、x64|x64|  
|x86_arm|x86 跨平台上的 ARM|x86、x64|ARM|  
|amd64 或 x64|x64 64 位本机编译器|x64|x64|  
|amd64\_x86 或 x64\_x86|x64 上的 x86 跨|x64|x86|  
|amd64\_arm 或 x64\_arm|平台 x64 兼容上的 ARM|x64|ARM|  
  
你可以使用**存储**或**uwp**选项以指定的平台类型，还是两者皆未指定桌面应用程序。 若要指定的 Windows SDK 版本，可以使用一个完整的 Windows 10 SDK 数字，如 10.0.10240.0，或指定 8.1 若要使用 Windows 8.1 SDK。 使用 14.0 指定 Visual Studio 2015 编译器工具集;默认情况下，环境设置为使用 Visual Studio 2017 编译器工具集。

<a name="vcvarsall"></a>
## <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>若要将现有的命令提示符窗口中的生成环境设置  
  
1.  在命令提示符下，使用 CD 命令更改为 Visual Studio 安装目录。 然后，再次使用 CD 更改为包含的配置特定命令文件的子目录。 对于 Visual Studio 自 2017 年 1，这是 VC\Auxiliary\Build 子目录。 对于 Visual Studio 2015 中，使用 VC 子目录。  
  
1.  若要配置此命令提示符窗口，以使用 32 位工具来生成适用于 x86 代码平台，在命令提示符下输入：  
  
     `vcvarsall`  

1.  若要配置此命令提示符窗口，以使用 32 位工具来生成代码 x64 平台上的，在命令提示符下输入：  
  
     `vcvarsall x86_amd64`  
  
1.  若要配置此命令提示符窗口，以使用 32 位工具来生成适用于 ARM 平台上，在命令提示符下，代码输入：  
  
     `vcvarsall x86_arm`  
  
1.  若要配置此命令提示符窗口，以使用 64 位工具来生成代码 x64 平台上的，在命令提示符下输入：  
  
     `vcvarsall amd64`  
  
1.  若要配置此命令提示符窗口，以使用 64 位工具来生成适用于 x86 代码平台，在命令提示符下输入：  
  
     `vcvarsall amd64_x86`  
  
1.  若要配置此命令提示符窗口，以使用 64 位工具来生成适用于 ARM 平台上，在命令提示符下，代码输入：  
  
     `vcvarsall amd64_arm`  

命令文件将路径的必需的环境变量设置为生成工具、 库和标头。 你现在可以使用此命令提示符窗口运行命令行编译器和工具。  
  
如果你使用[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)为命令行生成设置由 vcvarsall.bat 或其他命令文件的环境不会影响生成，除非还指定**/useenv**选项。  

## <a name="command-line-tools"></a>命令行工具
  
若要在命令行上生成 C/c + + 项目，你可以使用这些 Visual c + + 命令行工具：  
  
[CL](../build/reference/compiling-a-c-cpp-program.md)  
使用编译器 (cl.exe) 可编译源代码文件，并将其链接到应用、库和 DLL 中。  
  
[Link](../build/reference/linking.md)  
使用链接器 (link.exe) 可将已编译的对象文件和库链接到应用和 DLL 中。  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
使用 MSBuild (msbuild.exe) 生成 Visual c + + 项目和[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]解决方案。 这相当于运行**生成**项目或**生成解决方案**命令[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]IDE。  
  
[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)  
将 DEVENV (devenv.exe) 与命令行开关结合-例如， **/内部**或**/清理**-执行某些生成命令而不显示[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]IDE。  
  
[NMAKE](../build/nmake-reference.md)  
使用 NMAKE (nmake.exe) 可自动执行使用传统的生成文件生成 Visual c + + 项目的任务。  
  
在命令行上生成时，你可以获取有关警告、 错误和消息信息。 启动[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，然后在菜单栏上，选择**帮助**，**搜索**。  
  
## <a name="in-this-section"></a>本节内容  

文档的此部分中的文章显示了如何在命令行上生成应用、介绍了如何自定义命令行生成环境以使用 64 位工具集并面向 x86、x64 和 ARM 平台，以及演示了如何使用命令行生成工具 MSBuild 和 NMAKE。  
  
[演练：在命令行上编译本机 C++ 程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
提供显示了如何在命令行上创建和编译简单 C++ 程序的示例。  
  
[演练： 编译 C 程序命令行上](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
介绍了如何编译采用 C 编程语言编写的程序。  
  
[演练：在命令行上编译 C++/CLI 程序](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
介绍了如何创建和编译使用 .NET Framework 的 C++/CLI 程序。  
  
[演练：在命令行上编译 C++/CX 程序](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
介绍了如何创建和编译使用 Windows 运行时的 C++/CX 程序。  
  
[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
描述如何启动但不包含必需的环境变量设置为命令行生成面向 x86、 x64 和 ARM 平台，通过使用 32 位或 64 位工具集的命令提示符窗口。  
  
[NMAKE 参考](../build/nmake-reference.md)  
提供指向介绍了 Microsoft 程序维护实用工具 (NMAKE.EXE) 的文章的链接。  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
提供指向探讨如何使用 MSBuild.EXE 的文章的链接。  
  
## <a name="related-sections"></a>相关章节  

[/MD、/MT、/LD（使用运行时库）](../build/reference/md-mt-ld-use-run-time-library.md)  
介绍了如何使用这些编译器选项来使用“Debug”或“Release”运行时库。  
  
[C/c + + 编译器选项](../build/reference/compiler-options.md)  
提供指向探讨 C 和 C++ 编译器选项和 CL.exe 的文章的链接。  
  
[链接器选项](../build/reference/linker-options.md)  
提供指向探论链接器选项和 LINK.exe 的文章的链接。  
  
[C/C++ 生成工具](../build/reference/c-cpp-build-tools.md)  
提供指向 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中包括的 C/C++ 生成工具的链接。  
  
## <a name="see-also"></a>请参阅  

[生成 C/C++ 程序](../build/building-c-cpp-programs.md)