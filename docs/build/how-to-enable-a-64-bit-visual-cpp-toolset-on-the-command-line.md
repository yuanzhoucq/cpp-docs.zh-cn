---
title: 如何：在命令行上启用64位 MSVC 工具集
ms.date: 07/24/2019
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
ms.openlocfilehash: 9e8a671a7fe67150e1b867c62231173429f7b6ed
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415932"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>如何：在命令行上启用64位 x64 托管的 MSVC 工具集

Visual Studio 包括 C++编 译器、链接器和其他工具，可用于创建特定于平台的应用版本，这些版本可以在 32 位、64 位或基于 ARM 的 Windows 操作系统上运行。 借助其他可选的 Visual Studio 工作负载，可使用 C++ 工具面向其他平台（例如 iOS、Android 和 Linux）。 默认生成体系结构使用由 x86 托管的 32 位工具来生成 32 位 x86 本机 Windows 代码。 但是，你可能使用 64 位计算机。 在 64 位 Windows 操作系统中安装 Visual Studio 时，由 x64 托管的 64 位本机与跨平台编译器可以使用额外的开发人员命令提示符快捷方式。 为 x86、x64 或 ARM 处理器生成代码时，可以通过由 x64 托管的 64 位工具集来使用 64 位代码可用的处理器和内存空间。

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>使用 64 位托管开发人员命令提示符快捷方式

若要在 Windows 10 上访问这些命令提示符，请在“开始”菜单上，打开 Visual Studio 版本的文件夹（如 Visual Studio 2019），然后选择其中一个 x64 本机或跨工具开发人员命令提示符。 

![x64 本机工具命令提示](media/x64-native-tools-command-prompt.png ""开始" 菜单中的 x64 本机工具")

若要在 Windows 8 上访问这些命令提示符，请在“开始”屏幕上，打开“所有应用”。 在已安装的 Visual Studio 版本的标题下，打开“Visual Studio”文件夹（在较旧版本的 Visual Studio 中，名称可能为“Visual Studio Tools”）。 在较早版本的 Windows 上，选择“开始”，展开“所有程序”，选择 Visual Studio 版本的文件夹（在较旧版本的 Visual Studio 上，名为“Visual Studio Tools”）。 有关详细信息，请参阅[开发人员命令提示快捷方式](building-on-the-command-line.md#developer_command_prompt_shortcuts)。

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>使用 Vcvarsall.bat 设置 64 位托管生成体系结构

通过运行 vcvarsall.bat 命令文件，可以在命令行上使用任何本机或跨编译器工具 生成配置。 此命令文件配置在现有命令提示符窗口中启用特殊生成体系结构的路径和环境变量。 有关具体说明，请参阅[开发人员命令文件位置](building-on-the-command-line.md#developer_command_file_locations)。

## <a name="remarks"></a>备注

> [!NOTE]
> 有关每个 Visual Studio 版本包含的特定工具的信息，请参阅 [Visual Studio 版本中的 Visual C++ 工具和功能](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md)。
>
> 有关如何使用 Visual Studio IDE 创建64位应用程序的信息，请参阅[如何：将视觉C++对象配置为面向64位、x64 平台](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)。

在 Visual Studio 安装程序中安装 C++ 工作负载时，系统始终安装由 x86 托管的 32 位本机与跨编译器工具来生成 x86 和 x64 代码。 如果包括通用 Windows 平台工作负载，系统还会安装由 x86 托管的跨编译器工具来生成 ARM 代码。 如果将这些工作负载安装在 64 位 x64 处理器上，还会获得 64 位本机与跨编译器工具以生成 x86、x64 和 ARM 代码。 32 位和 64 位工具生成相同的代码，但是，64 位工具支持更多针对预编译标头符号和全程序优化（[/GL](reference/gl-whole-program-optimization.md) 和 [/LTCG](reference/ltcg-link-time-code-generation.md)）选项的内存。 使用 32 位工具时，如果遇到内存限制，请尝试使用 64 位工具。

## <a name="see-also"></a>另请参阅

[针对 64 位 x64 目标配置 C++ 项目](configuring-programs-for-64-bit-visual-cpp.md)<br/>
