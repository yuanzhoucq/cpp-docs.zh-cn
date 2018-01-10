---
title: "如何： 启用 64 位 Visual c + + 工具集在命令行上 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7712bcf73881d02b5d28c8a7645609be1df5e489
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-a-64-bit-x64-hosted-visual-c-toolset-on-the-command-line"></a>如何： 启用 64 位，x64 托管在命令行上的 Visual c + + 工具集

Visual c + + 包括编译器、 链接和可用于创建特定于平台的版本，你可以在 32 位和 64 位或基于 ARM 的 Windows 操作系统运行的应用的其他工具。 其他可选的 Visual Studio 工作负荷允许你使用 c + + 工具来创建面向其他平台，例如 iOS、 Android 和 Linux。 默认值生成体系结构使用 32 位、 x86 承载的工具来生成 32 位、 x86 本机 Windows 代码。 但是，可能出现的 64 位计算机。 当你生成适用于 x86、 x64 或 ARM 处理器代码时，使用 64 位，x64 托管工具集，可以充分利用的处理器和内存空间提供给 64 位代码。
  
> [!NOTE]
>  有关每个 Visual c + + 版本包含的特定工具的信息，请参阅[Visual c + + 工具和 Visual Studio 版本中的功能](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)。  
>   
>  有关如何使用 Visual Studio IDE 来创建 64 位应用程序的信息，请参阅[如何： 配置 Visual c + + 项目，以便针对 64 位 x64 平台](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。  
  
当在 Visual Studio 安装程序安装 c + + 工作负荷时，它始终会安装 32 位、 x86 承载、 本机和跨编译器工具以创建 x86 和 x64 代码。 如果包括通用 Windows 平台工作负荷，它还会安装 x86 承载在跨平台编译器工具以创建 ARM 代码。 如果你将这些工作负荷都安装在 64 位 x64 处理器，你还可获得 64 位本机和跨生成 x86、 x64 和 ARM 编译器工具的代码。 32 位和 64 位工具生成相同的代码，但是，64 位工具针对预编译标头符号和全程序优化支持更多的内存 ([/GL](../build/reference/gl-whole-program-optimization.md)和[/LTCG](../build/reference/ltcg-link-time-code-generation.md)) 选项。 如果当你使用 32 位工具遇到内存限制，请尝试的 64 位工具。  

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>使用 64 位托管开发人员命令提示符快捷方式
  
当在 64 位 Windows 操作系统上安装 Visual Studio 时，则其他开发人员命令提示符快捷方式为 64 位 x64 承载的本机和跨平台编译器才可用。 若要访问在 Windows 10 中，这些命令提示在**启动**菜单上，打开你的 Visual Studio 版本的文件夹，例如**Visual Studio 2017**，然后选择 x64 本机或跨工具之一开发人员命令提示。 若要访问在 Windows 8 中，这些命令提示在**启动**屏幕上，打开**所有应用**。 在已安装版本的 Visual Studio 标题下，打开**Visual Studio**文件夹 (在较旧版本的 Visual Studio 中，可能名为**Visual Studio Tools**)。 在早期版本的 Windows 中，选择**启动**，展开**所有程序**，你的版本的文件夹**Visual Studio** (和在较旧版本的 Visual Studio 中， **Visual Studio 工具**)。 有关详细信息，请参阅[开发人员命令提示符快捷方式](../build/building-on-the-command-line.md#developer_command_prompt_shortcuts)。  
  
## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>使用 Vcvarsall.bat 设置 64 位托管的生成体系结构
  
任何本机或跨编译器工具生成配置可在命令行通过运行 vcvarsall.bat 命令文件。 此命令文件配置路径，并启用特定的环境变量构建在现有的命令提示符窗口的体系结构。 有关具体的说明，请参阅[开发人员命令文件和位置](../build/building-on-the-command-line.md#developer_command_files)。  
  
## <a name="see-also"></a>请参阅  

[针对 64 位 x64 目标配置 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md)