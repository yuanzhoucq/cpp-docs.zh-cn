---
title: 如何：启用命令行上的 64 位 MSVC 工具集
ms.date: 03/29/2018
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
ms.openlocfilehash: 8436254a3d8c5c1dae018c2309ceaad7bd5b2408
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188907"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>如何：启用 64 位，x64 托管在命令行上的 MSVC 工具集

Visual Studio 提供了C++编译器、 链接器，并可用于创建特定于平台的版本，你可以在 32 位、 64 位或基于 ARM 的 Windows 操作系统运行的应用的其他工具。 其他可选的 Visual Studio 工作负载，可以使用C++面向其他平台，例如 iOS、 Android 和 Linux 的工具。 默认生成体系结构使用 32 位、 x86 承载的工具来生成 32 位、 x86 本机 Windows 代码。 但是，很可能在 64 位计算机。 通过使用 64 位，x64 托管工具集生成 x86、 x64 或 ARM 处理器的代码时，可以充分利用处理器和内存空间可用于 64 位代码。

> [!NOTE]
> 有关每个 Visual Studio 版本附带的特定工具的信息，请参阅[可视化C++工具和 Visual Studio 版本中的功能](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md)。
>
> 有关如何使用 Visual Studio IDE 创建 64 位应用程序的信息，请参阅[如何：针对 64 位 x64 平台配置 Visual C++ 项目](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。

当你安装C++Visual Studio 安装程序中的工作负载，它始终会安装 32 位、 x86 承载、 本机和跨平台编译器工具，用于构建 x86 和 x64 代码。 如果包括通用 Windows 平台工作负荷时，它还会安装 x86 承载在跨平台编译器工具生成 ARM 代码。 如果将这些工作负荷安装在 64 位 x64 处理器，您还获得 64 位本机和跨用于创建 x86、 x64 和 ARM 的编译器工具的代码。 32 位和 64 位工具生成相同的代码，但 64 位工具支持预编译标头符号和全程序优化的更多的内存 ([/GL](reference/gl-whole-program-optimization.md)并[/LTCG](reference/ltcg-link-time-code-generation.md)) 选项。 如果使用 32 位工具时遇到内存限制，请，尝试在 64 位工具。

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>使用 64 位托管开发人员命令提示符快捷方式

当在 64 位 Windows 操作系统上安装 Visual Studio 时，将用 64 位，x64 托管本机和跨平台编译器的其他开发人员命令提示符快捷方式。 若要访问在 Windows 10 上的这些命令提示符**启动**菜单中，打开你的 Visual Studio 版本的文件夹，例如**Visual Studio 2017**，然后选择 x64 本机或跨工具之一开发人员命令提示。 若要访问在 Windows 8 上这些命令提示符**启动**屏幕上，打开**的所有应用**。 在安装版本的 Visual Studio 标题下，打开**Visual Studio**文件夹 (在较旧版本的 Visual Studio 中，可能名为**Visual Studio Tools**)。 在早期版本的 Windows 中，选择**启动**，展开**所有程序**，你的版本文件夹**Visual Studio** (和较早版本的 Visual Studio **Visual Studio 工具**)。 有关详细信息，请参阅[开发人员命令提示快捷方式](building-on-the-command-line.md#developer_command_prompt_shortcuts)。

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>使用 Vcvarsall.bat 设置 64 位托管的生成体系结构

任何本机或跨编译器工具生成配置可以使用命令行通过运行 vcvarsall.bat 命令文件。 此命令文件配置的路径，并启用特定的环境变量生成现有的命令提示符窗口中的体系结构。 有关具体说明，请参阅[开发人员命令文件位置](building-on-the-command-line.md#developer_command_file_locations)。

## <a name="see-also"></a>请参阅

[配置C++适用于 64 位 x64 目标项目](configuring-programs-for-64-bit-visual-cpp.md)<br/>
