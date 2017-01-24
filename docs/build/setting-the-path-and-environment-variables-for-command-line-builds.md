---
title: "为命令行生成设置路径和环境变量 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "include"
  - "Lib"
  - "Path"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器 [C++], 环境变量"
  - "编译源代码 [C++], 从命令行"
  - "环境变量 [C++]"
  - "环境变量 [C++], CL 编译器"
  - "INCLUDE 保留字"
  - "LIB 环境变量"
  - "LINK 工具 [C++], 环境变量"
  - "LINK 工具 [C++], 路径"
  - "PATH 保留字"
  - "VCVARS32.bat 文件"
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
caps.latest.revision: 17
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 为命令行生成设置路径和环境变量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令行生成工具需要多个为安装自定义的环境变量。  安装 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 后，它将创建可设置所需环境变量的命令文件，然后创建可启动“命令提示符”窗口的快捷方式，在该窗口中这些变量已设置完毕。  当你想要使用命令行工具时，可以运行这些快捷方式之一，也可以打开纯“命令提示符”窗口，然后运行 vcvarsall.bat 命令文件。  
  
 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 命令行工具使用 PATH、TMP、INCLUDE、LIB 和 LIBPATH 环境变量，还可以使用特定于工具的环境变量。  由于这些环境变量的值特定于安装，并且可能因产品更新或升级而进行更改，因此建议使用 vcvarsall.bat 或“开发人员命令提示”快捷方式，而不是由你自行设置它们。  有关由编译器和链接器使用的特定环境变量的信息，请参阅 [CL 环境变量](../build/reference/cl-environment-variables.md)和 [LINK 环境变量](../build/reference/link-environment-variables.md)。  
  
> [!NOTE]
>  多个命令行工具或工具选项都需要管理员权限。  若要使用它们，建议通过使用**“以管理员身份运行”**选项（位于要打开的“命令提示符”窗口的快捷菜单上）打开“命令提示符”窗口。  
  
## 使用“命令提示”快捷方式  
 包括在每个版本的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中的“开发人员命令提示”快捷方式将打开“命令提示符”窗口，并设置环境以使用要面向 x86 处理器的 32 位 x86 本机工具集。  还可以使用面向 x64 和 ARM 平台的 32 位跨编译器的命令提示符。  还可以使用面向 x64 处理器的 64 位 x64 本机工具集的“命令提示”快捷方式，以及面向 x86 处理器的 64 位跨编译器的“命令提示”快捷方式，具体取决于你的系统和安装的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本。  可在所有版本的 Visual Studio 中使用这些版本的命令行工具集：  
  
 x86 on x86  
 使用此工具集可为 x86 计算机创建输出文件。  它在 x86 计算机上和 64 位 Windows 操作系统中的 WOW64 下作为 32 位本机进程运行。  
  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] on x86（[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 跨平台编译器）  
 使用此工具集可为 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 创建输出文件。  它在 x86 计算机上和 64 位 Windows 操作系统中的 WOW64 下作为 32 位本机进程运行。  
  
 x86 上的 ARM（ARM 跨平台编译器）  
 使用此工具集可为 ARM 计算机创建输出文件。  它在 x86 计算机上和 64 位 Windows 操作系统中的 WOW64 下作为 32 位本机进程运行。  
  
 可在 64 位平台上使用这些版本的命令行工具集：  
  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 上的 x86  
 使用此工具集可为 x86 计算机创建输出文件。  它在 64 位 Windows 操作系统上作为本机进程运行。  
  
 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] on[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]  
 使用此工具集可为 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 计算机创建输出文件。  它在 64 位 Windows 操作系统上作为本机进程运行。  
  
 x64 上的 ARM（ARM 跨平台编译器）  
 使用此工具集可为 ARM 计算机创建输出文件。  它在 64 位 Windows 操作系统上作为 64 位本机进程运行。  
  
#### 打开“开发人员命令提示”窗口  
  
1.  在显示的 Windows 8“开始”屏幕上，键入 Visual Studio Tools。  请注意，随着你的键入搜索结果将相应变化，当**“Visual Studio Tools”**出现时，请选择它。  
  
     在早期版本的 Windows 上，选择**“开始”**，然后在搜索框中键入 Visual Studio Tools。  当**“Visual Studio Tools”**出现在搜索结果中时，请选择它。  
  
2.  在**“Visual Studio Tools”**文件夹中，打开适用于你的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本的**“开发人员命令提示”**。  （若要以管理员身份运行，请打开“开发人员命令提示”的快捷菜单，然后选择**“以管理员身份运行”**。）  
  
 “开发人员命令提示”将设置环境以使用要面向 x86 处理器的 32 位本机工具集。  选择**“x64 兼容工具命令提示”**以使用要面向 x64 处理器的 32 位本机工具集。  选择**“ARM 兼容工具命令提示”**以使用要面向 ARM 处理器的 32 位本机工具集。  选择**“x64 本机工具命令提示”**以使用要面向 x64 处理器的 64 位本机工具集。  
  
## 在“命令提示符”窗口中使用 vcvarsall.bat  
 通过在纯“命令提示符”窗口中运行 vcvarsall.bat，可设置环境变量以配置适用于 32 位或 64 位本机编译的命令行，或适用于面向 x86、x64 或 ARM 处理器的交叉编译的命令行。  如果未提供任何参数，vcvarsall.bat 将配置环境变量以供使用面向 x86 的 32 位本机编译器。  但是，你可以用该编译器来配置所有的编译器。  如果指定在生成计算机体系结构上未安装或不可用的编译器配置，将会显示一条消息。  下表显示了支持的参数。  
  
|Vcvarsall.bat 参数|编译器|生成计算机体系结构|生成输出体系结构|  
|----------------------|---------|---------------|--------------|  
|x86|x86 32 位本机|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|x86|  
|x86\_amd64|x86 跨平台上的 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|x86\_arm|x86 跨平台上的 ARM|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|ARM|  
|amd64|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 64 位本机编译器|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|amd64\_x86|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 跨平台上的 x86|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|x86|  
|amd64\_arm|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 跨平台上的 ARM|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|ARM|  
  
 以下步骤显示如何配置“命令提示”，以使用要面向 x86 平台的 32 位本机工具集。  
  
#### 运行 vcvarsall.bat  
  
1.  在命令提示符下，更改到 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 安装目录。  （该位置取决于系统和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安装，但典型位置是 C:\\Program Files \(x86\)\\Microsoft Visual Studio *version*\\VC\\。）例如，输入：  
  
     cd "\\Program Files \(x86\)\\Microsoft Visual Studio 12.0\\VC"  
  
2.  若要为 32 位 x86 命令行生成配置此“命令提示符”窗口，请在命令提示符下，输入：  
  
     `vcvarsall x86`  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 还提供 vcvars32.bat 来设置命令行环境。  vcvars32.bat 文件仅限于设置适当的环境变量，以启用 32 位 x86 命令行生成。  它与 `vcvarsall x86` 命令等效。  
  
 如果你要将 [DEVENV](../Topic/Devenv%20Command%20Line%20Switches.md) 用于命令行生成，除非还指定了 **\/useenv** 选项，否则由 vcvarsall.bat 或 vcvars32.bat 设置的环境不会对你的生成产生任何影响。  
  
> [!CAUTION]
>  vcvarsall.bat 文件在不同的计算机中会有所不同。  不要使用另一台计算机中的文件替换丢失或损坏的 vcvarsall.bat 文件。  重新运行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安装程序以替换丢失的文件。  
>   
>  vcvarsall.bat 文件在不同的版本中也会有所不同。  如果安装 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 的当前版本的计算机上也安装有 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 的早期版本，则不要在同一“命令提示符”窗口中运行来自不同版本的 vcvarsall.bat 或 vcvars32.bat。  
  
## 请参阅  
 [在命令行上生成](../build/building-on-the-command-line.md)   
 [链接](../build/reference/linking.md)   
 [链接器选项](../build/reference/linker-options.md)   
 [编译 C\/C\+\+ 程序](../build/reference/compiling-a-c-cpp-program.md)   
 [编译器选项](../build/reference/compiler-options.md)