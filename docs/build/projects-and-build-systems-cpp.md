---
title: Visual Studio 中的 C/C++ 项目和生成系统
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 3d82ac4569e06a4472047a79da60032ad2db43ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078471"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Visual Studio 中的 C/C++ 项目和生成系统

你可以使用 Visual Studio 来编辑、编译和生成任何C++具有完整 IntelliSense 支持的基本代码，而无需将该代码转换为 Visual Studio 项目，也无需使用 MSVC 工具集进行编译。 例如，你可以在 Windows 计算机上的 Visual Studio 中编辑跨平台的 CMake 项目，然后在远程 Linux 计算机上使用 g + + 为 Linux 编译该项目。

## <a name="c-compilation"></a>C++汇编

若*build*要生成C++程序，则意味着要从一个或多个文件编译源代码，然后将这些文件链接到可执行文件（.exe）、动态加载库（.dll）或静态库（.lib）。

基本C++编译涉及三个主要步骤：

- C++预处理器会转换每个源文件中的所有 #directives 和宏定义。 这将创建一个*翻译单元*。
- C++编译器将每个翻译单元编译为对象文件（.obj），并应用已设置的任何编译器选项。
- *链接器*将对象文件合并为一个可执行文件，并应用已设置的链接器选项。

## <a name="the-msvc-toolset"></a>MSVC 工具集

Microsoft C++编译器、链接器、标准库和相关的实用工具包含 MSVC 编译器工具集（也称为工具链或 "生成工具"）。 它们包含在 Visual Studio 中。 你还可以从[Visual Studio 2019 的生成工具下载位置](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)免费下载并使用工具集作为独立包。

可以通过从命令行直接调用 MSVC 编译器（cl）来构建简单的程序。 以下命令接受单个源代码文件，并调用 mage.exe 来生成名为 " *hello*" 的可执行文件：

```cmd
cl /EHsc hello.cpp
```

请注意，此时编译器（cl）会自动调用C++预处理器和链接器以生成最终的输出文件。  有关详细信息，请参阅[在命令行上生成](building-on-the-command-line.md)。

## <a name="build-systems-and-projects"></a>生成系统和项目

大多数实际程序使用某种类型的*生成系统*来管理复杂的编译多个配置的多个源文件（即，调试和发布）、多个平台（x86、X64、ARM 等）、自定义生成步骤，甚至是必须按特定顺序编译的多个可执行文件。 您在生成配置文件中进行设置，并且生成系统在调用编译器之前接受该文件作为输入。 生成可执行文件所需的一组源代码文件和生成配置文件称为 "*项目*"。

以下列表显示了 Visual Studio 项目的各种选项- C++：

- 使用 Visual Studio IDE 创建 Visual Studio 项目，并使用属性页对其进行配置。 Visual Studio 项目生成在 Windows 上运行的程序。 有关概述，请参阅 Visual Studio 文档中的[编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)。

- 打开包含 Cmakelists.txt 文件的文件夹。 CMake 支持已集成到 Visual Studio 中。 您可以使用 IDE 进行编辑、测试和调试，而无需以任何方式修改 CMake 文件。 这使您可以与可能使用不同编辑器的其他人一起使用同一 CMake 项目。 CMake 是用于跨平台开发的建议方法。 有关详细信息，请参阅[CMake 项目](cmake-projects-in-visual-studio.md)。

- 打开源文件的松散文件夹，不包含任何项目文件。 Visual Studio 将使用试探法来生成文件。 这是一种简单的方法来编译和运行小型控制台应用程序。 有关详细信息，请参阅[打开文件夹项目](open-folder-projects-cpp.md)。

- 打开包含生成文件的文件夹或任何其他生成系统配置文件。 可以通过将 JSON 文件添加到文件夹中，将 Visual Studio 配置为调用任意生成命令。 有关详细信息，请参阅[打开文件夹项目](open-folder-projects-cpp.md)。

- 在 Visual Studio 中打开 Windows makefile。 有关详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)。

## <a name="msbuild-from-the-command-line"></a>命令行中的 MSBuild

可以通过在命令行中传递 .vcxproj 文件和命令行选项来调用 MSBuild。 此方法需要充分了解 MSBuild，建议仅在绝对必要时使用。 有关详细信息，请参阅 [MSBuild](msbuild-visual-cpp.md)。

## <a name="in-this-section"></a>本节内容

[Visual Studio 项目](creating-and-managing-visual-cpp-projects.md)如何使用其本机生成系统（MSBuild C++ ）在 Visual Studio 中创建、配置和生成项目。

[CMake 项目](cmake-projects-in-visual-studio.md)如何在 Visual Studio 中编码、生成和部署 CMake 项目。

[打开文件夹项目](open-folder-projects-cpp.md)如何使用 Visual Studio 来编码、生成和部署C++基于任意生成系统的项目，或者不生成系统。 完全。

[发布](release-builds.md)版本如何创建优化的发布版本并对最终用户进行故障排除。

[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)<br/>
讨论如何直接从命令行使用C++ C/编译器和生成工具，而不是使用 VISUAL Studio IDE。

[在 Visual Studio 中生成 dll](dlls-in-visual-cpp.md)如何在 Visual Studio 中创建、调试和C++部署 C/dll （共享库）。

[演练：创建和使用静态库](walkthrough-creating-and-using-a-static-library-cpp.md)如何创建 .lib 二进制文件。

[生成 C/C++独立应用程序和并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)基于独立应用程序和并行程序集的概念描述 Windows 桌面应用程序的部署模型。

[为C++ 64 位、x64 目标配置项目](configuring-programs-for-64-bit-visual-cpp.md)如何将64位 x64 硬件用于 MSVC 生成工具。

[配置C++ ARM 处理器的项目](configuring-programs-for-arm-processors-visual-cpp.md)如何使用 MSVC 生成工具来面向 ARM 硬件。

[优化代码](optimizing-your-code.md)如何以各种方式优化代码，包括按计划优化。

[为 WINDOWS XP 配置程序](configuring-programs-for-windows-xp.md)如何将 Windows XP 与 MSVC 生成工具面向。

[C/C++ 生成参考](reference/c-cpp-building-reference.md)<br/>
提供指向有关使用 C++ 生成程序、编译器和链接器选项以及各种生成工具的参考文章的链接。
