---
title: "如何：在命令行上启用 64 位 Visual C++ 工具集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "64 位编译器 [C++], 命令行用法"
  - "64 位编译器 [C++], 在命令行上进行的工具集启用"
  - "命令行 [C++], 64 位编译器"
  - "IPF"
  - "IPF, 命令行编译器"
  - "Itanium [C++]"
  - "Itanium [C++], 命令行编译器"
  - "x64 [C++]"
  - "x64 [C++], 命令行编译器"
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 如何：在命令行上启用 64 位 Visual C++ 工具集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 包括编译器，可用于创建可在 32 位、64 位或基于 ARM 的 Windows 操作系统上运行的应用程序。  
  
> [!NOTE]
>  有关 Visual C\+\+ 版本附带的特定工具的信息，请参阅 [Visual Studio 版本中的 Visual C\+\+ 工具和模板](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)。  
>   
>  有关如何使用 Visual Studio IDE 创建 64 位应用程序的信息，请参阅[如何：针对 64 位平台配置 Visual C\+\+ 项目](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。  
  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 包括 32 位、x86 承载的 x86 本机和跨平台编译器、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 和 ARM 目标。  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 安装在 64 位 Windows 操作系统后，为每个目标（x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 和 ARM）安装了 32 位的 x86 承载的本机和跨平台编译器以及 64 位的 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 承载的本机和跨平台编译器。  每个目标的 32 位和 64 位编译器生成相同的代码，但是，64 位编译器支持更多针对预编译头符号和全程序优化（[\/GL](../build/reference/gl-whole-program-optimization.md)、[\/LTCG](../build/reference/ltcg-link-time-code-generation.md)）选项的内存。  使用 32 位编译器时，如果遇到内存限制，请尝试使用 64 位编译器。  
  
 在 64 位 Windows 操作系统中安装 Visual Studio 后，某些 64 位本机 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 和 x86 跨平台编译器的其他命令符提示快捷方式可用。  若要在 Windows 8 上访问这些命令提示符，可在**“启动”**屏幕，打开**“所有应用程序”**。  在安装的**“[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]”**版本下，打开**“Visual Studio Tools”**，然后选择一个本机工具或跨工具命令提示符。  在 Windows 的早期版本中，选择**“启动”**，展开**“所有程序”**、**[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]**、**“Visual Studio Tools”**，然后选择命令提示。  
  
## Vcvarsall.bat  
 可以通过运行 Vcvarsall.bat 命令文件在命令行上使用任何编译器来配置启用编译器工具集的路径和环境变量。  由于没有命令提示符快捷方式可用于启用面向 x86 或 ARM 平台的 64 位工具集，因此请在命令提示符窗口中使用 vcvarsall.bat 以改用 64 位工具集。  有关详细信息，请参阅[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 下列步骤演示如何将命令提示符配置为使用面向 x86、x64 和 ARM 平台的 64 位本机工具集。  
  
#### 运行 vcvarsall.bat 以使用 64 位工具集  
  
1.  在命令提示符处，更改 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 安装目录。  （该位置取决于系统和安装的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，但典型位置为 C:\\Program Files \(x86\)\\Microsoft Visual Studio *version*\\VC\\。）例如，输入：  
  
     cd "\\Program Files \(x86\)\\Microsoft Visual Studio 12.0\\VC"  
  
2.  若要针对面向 x64 平台的 64 位命令行生成配置此命令提示符窗口，请在命令提示符处输入：  
  
     `vcvarsall amd64`  
  
3.  若要针对面向 x86 平台的 64 位命令行生成配置此命令提示符窗口，请在命令提示符处输入：  
  
     `vcvarsall amd64_x86`  
  
4.  若要针对面向 ARM 平台的 64 位命令行生成配置此命令提示符窗口，请在命令提示符处输入：  
  
     `vcvarsall amd64_arm`  
  
## 请参阅  
 [配置 64 位的程序](../build/configuring-programs-for-64-bit-visual-cpp.md)