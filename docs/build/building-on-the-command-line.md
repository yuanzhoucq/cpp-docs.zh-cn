---
title: "在命令行上生成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "builds [C++], 命令行"
  - "命令行 [C++], 生成于"
  - "命令行 [C++], 编译器"
  - "命令行生成 [C++]"
  - "编译源代码 [C++], 命令行"
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 在命令行上生成
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过使用包含在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的工具，可在命令行上生成 C 和 C\+\+ 应用程序。  每个版本的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 都安装了包括编译器、链接器和其他生成工具的命令行工具集，以及设置所需的生成环境的命令行文件。  默认情况下，这些工具都安装在 *drive*:\\Program Files \(x86\)\\Microsoft Visual Studio *version*\\VC\\bin\\ 中。  （计算机上的实际目录取决于系统、[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本以及所选的安装。）  
  
 若要正常工作，[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令行工具需要多个为安装自定义的环境变量。  安装 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 后，它将创建 vcvarsall.bat 命令文件，可运行该文件来设置所需的环境变量。  它还将创建启动“开发人员命令提示”窗口的快捷方式，在该窗口中这些变量已设置完毕。  这些环境变量特定于安装，并且可能因产品更新或升级而进行更改。  因此，建议使用 vcvarsall.bat 或“开发人员命令提示”快捷方式，而不是由你自行设置它们。  有关详细信息，请参阅[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
### 打开“开发人员命令提示”窗口  
  
1.  在 Windows 8“开始”屏幕上，输入 Visual Studio Tools。  请注意，随着你的键入搜索结果将相应变化，当**“Visual Studio Tools”**出现时，请选择它。  
  
     在早期版本的 Windows 上，选择**“开始”**，然后在搜索框中输入 Visual Studio Tools。  当**“Visual Studio Tools”**出现在搜索结果中时，请选择它。  
  
2.  在**“Visual Studio Tools”**文件夹中，打开适用于你的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本的**“开发人员命令提示”**。  
  
 若要在命令行上生成 C\/C\+\+ 项目，可使用这些 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令行工具：  
  
 [CL](../build/reference/compiling-a-c-cpp-program.md)  
 使用编译器 \(cl.exe\) 可编译源代码文件，并将其链接到应用、库和 DLL 中。  
  
 [Link](../build/reference/linking.md)  
 使用链接器 \(link.exe\) 可将已编译的对象文件和库链接到应用和 DLL 中。  
  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)  
 使用 MSBuild \(msbuild.exe\) 可生成 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 项目和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 解决方案。  这等效于在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 中运行**“生成”**项目或**“生成解决方案”**命令。  
  
 [DEVENV](../Topic/Devenv%20Command%20Line%20Switches.md)  
 将 DEVENV \(devenv.exe\) 与命令行开关（例如，**“\/Build”**或**“\/Clean”**）结合使用可在不显示 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE 的情况下执行某些生成命令。  
  
 [NMAKE](../build/nmake-reference.md)  
 使用 NMAKE \(nmake.exe\) 可自动执行使用传统的生成文件生成 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 项目的任务。  
  
 在命令行上生成时，通过启动 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 并在菜单栏上依次选择**“帮助”**、**“搜索”**，可获取有关警告、错误和消息的信息。  
  
## 本节内容  
 文档的此部分中的文章显示了如何在命令行上生成应用、介绍了如何自定义命令行生成环境以使用 64 位工具集并面向 x86、x64 和 ARM 平台，以及演示了如何使用命令行生成工具 MSBuild 和 NMAKE。  
  
 [演练：在命令行上编译本机 C\+\+ 程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
 提供显示了如何在命令行上创建和编译简单 C\+\+ 程序的示例。  
  
 [演练：在命令行上编译 C 程序](../Topic/Walkthrough:%20Compiling%20a%20C%20Program%20on%20the%20Command%20Line.md)  
 介绍了如何编译采用 C 编程语言编写的程序。  
  
 [演练：在命令行上编译 C\+\+\/CLI 程序](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
 介绍了如何创建和编译使用 .NET Framework 的 C\+\+\/CLI 程序。  
  
 [演练：在命令行上编译 C\+\+\/CX 程序](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
 介绍了如何创建和编译使用 Windows 运行时的 C\+\+\/CX 程序。  
  
 [为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
 介绍了如何启动“命令提示符”窗口，在该窗口中，已通过使用 32 位或 64 位工具集为面向 x86、x64 和 ARM 平台的命令行生成设置所需的环境变量。  
  
 [NMAKE 参考](../build/nmake-reference.md)  
 提供指向介绍了 Microsoft 程序维护实用工具 \(NMAKE.EXE\) 的文章的链接。  
  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)  
 提供指向探讨如何使用 MSBuild.EXE 的文章的链接。  
  
## 相关章节  
 [\/MD、\/MT、\/LD（使用运行时库）](../build/reference/md-mt-ld-use-run-time-library.md)  
 介绍了如何使用这些编译器选项来使用“Debug”或“Release”运行时库。  
  
 [C\/C\+\+ 编译器选项](../build/reference/compiler-options.md)  
 提供指向探讨 C 和 C\+\+ 编译器选项和 CL.exe 的文章的链接。  
  
 [链接器选项](../build/reference/linker-options.md)  
 提供指向探论链接器选项和 LINK.exe 的文章的链接。  
  
 [C\/C\+\+ 生成工具](../build/reference/c-cpp-build-tools.md)  
 提供指向 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中包括的 C\/C\+\+ 生成工具的链接。  
  
## 请参阅  
 [生成 C\/C\+\+ 程序](../build/building-c-cpp-programs.md)