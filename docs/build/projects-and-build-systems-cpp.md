---
title: C /C++的项目并构建 Visual Studio 中的系统
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 12/08/2018
f1_keywords:
- vcbuilding
- buildingaprogramVC
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.openlocfilehash: 73797f3817338c48e8ff11eaaadff71263374fd0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341177"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>C /C++的项目并构建 Visual Studio 中的系统

Visual Studio 2017 可用于编辑、 编译和生成任何C++代码库，且无需将该代码转换到 Visual Studio 项目或使用 MSVC 工具集编译的完全 IntelliSense 支持。 例如，可以编辑跨平台的 CMake 项目在 Visual Studio 中的 Windows 计算机上，然后将其编译为在远程 Linux 计算机上使用 g + + 的 Linux。

## <a name="c-compilation"></a>C++编译

向*构建*C++程序意味着若要编译源代码从一个或多个文件，然后将这些文件链接到可执行文件 (.exe)、 动态加载库 (.dll) 或静态库 (.lib)。 

基本C++编译包括三个主要步骤：

- C++预处理器转换每个源代码文件中所有的 #directives 和宏的定义。 这将创建*翻译单元*。
- C++编译器将编译对象文件 (.obj)，为每个翻译单元应用任何编译器选项已设置。
- *链接器*将对象文件合并到单个的可执行文件，应用已设置链接器选项。 

## <a name="the-msvc-toolset"></a>MSVC 工具集

MicrosoftC++编译器、 链接、 标准库和相关的实用工具组成 MSVC 编译器工具集 （也称为工具链或"生成工具"）。 这些元素包含在 Visual Studio 中。 此外可以下载，并从免费作为独立程序包使用的工具集[Visual Studio 2017 生成工具下载位置](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)。

可以通过调用 MSVC 编译器 (cl.exe) 直接从命令行构建简单的程序。 下面的命令接受单个源代码文件中，并调用生成名为可执行文件的 cl.exe *hello.exe*: 

```cmd
cl /EHsc hello.cpp
```
请注意，此处编译器 (cl.exe) 会自动调用C++预处理器和链接器以生成最终输出文件。  有关详细信息，请参阅[命令行上生成](building-on-the-command-line.md)。

## <a name="build-systems-and-projects"></a>生成系统和项目

大多数实际程序中使用某些类型的*构建系统*来管理复杂的编译多个配置的多个源代码文件 （即发布与调试），多个平台 (x86、 x64、 ARM，等等)，自定义生成步骤，以及甚至多个必须以特定顺序编译的可执行文件。 在生成配置文件，请设置并生成系统接受该文件作为输入之前调用编译器。 调用的源代码文件和生成的可执行文件所需的生成配置文件集*项目*。 

以下列表显示了各种选项为 Visual Studio 项目的C++:

- 使用 Visual Studio IDE 创建 Visual Studio 项目并将其配置通过使用属性页。 Visual Studio 项目会生成在 Windows 运行的程序。 有关概述，请参阅[编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)Visual Studio 文档中。

- 打开包含 CMakeLists.txt 文件的文件夹。 CMake 支持已集成到 Visual Studio。 可以使用 IDE 来编辑、 测试和调试而无需修改任何方式中的 CMake 文件。 这使你能够在同一 CMake 项目中为其他人可能使用不同的编辑器。 CMake 是跨平台开发的推荐的方法。 有关详细信息，请参阅[CMake 项目](cmake-projects-in-visual-studio.md)。
 
- 与任何项目文件来打开松散源文件的文件夹。 Visual Studio 将使用试探法来生成的文件。 这是编译并运行小型控制台应用程序的简单办法。 有关详细信息，请参阅[打开文件夹项目](open-folder-projects-cpp.md)。

- 打开包含生成文件或任何其他生成系统配置文件的文件夹。 可以配置 Visual Studio 以调用任何任意的生成命令通过将 JSON 文件添加到的文件夹。 有关详细信息，请参阅[打开文件夹项目](open-folder-projects-cpp.md)。
 
- 在 Visual Studio 中打开 Windows 生成文件。 有关详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)。

## <a name="msbuild-from-the-command-line"></a>MSBuild 从命令行 

通过将其传递以及命令行选项的.vcxproj 文件，你可以从命令行调用 MSBuild。 这种方法需要 MSBuild，更好地理解，建议仅在绝对必要时使用。 有关详细信息，请参阅 [MSBuild](msbuild-visual-cpp.md)。

## <a name="in-this-section"></a>本节内容

[Visual Studio 项目](creating-and-managing-visual-cpp-projects.md)如何创建、 配置和生成C++在 Visual Studio 中使用其本机项目生成系统 (MSBuild)。

[CMake 项目](cmake-projects-in-visual-studio.md)如何进行编码、 构建和部署 Visual Studio 中的 CMake 项目。

[打开文件夹项目](open-folder-projects-cpp.md)如何使用 Visual Studio 进行编码、 构建和部署C++基于任何任意的生成系统或没有项目生成系统。 完全。 

[发行版本](release-builds.md)如何创建和故障排除优化的发布版本以部署到最终用户。

[通过命令行使用 MSVC 工具集](building-on-the-command-line.md)<br/>
讨论如何使用 C /C++直接从命令行，而无需使用 Visual Studio IDE 的编译器和生成工具。

[构建 Visual Studio 中的 Dll](dlls-in-visual-cpp.md)如何创建、 调试和部署 C /C++ Visual Studio 中的 Dll （共享库）。

[演练：创建和使用静态库](walkthrough-creating-and-using-a-static-library-cpp.md)如何创建一个.lib 二进制文件。

[生成 C /C++独立应用程序和通过并行程序集](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)介绍了 Windows 桌面应用程序，其理论基础的独立应用程序和通过并行程序集的部署模型。

[配置C++项目的 64 位 x64 目标](configuring-programs-for-64-bit-visual-cpp.md)如何面向 64 位 x64 硬件与 MSVC 构建工具。

[配置C++项目类型提供的 ARM 处理器](configuring-programs-for-arm-processors-visual-cpp.md)如何使用 MSVC 生成工具面向 ARM 硬件。

[优化代码](optimizing-your-code.md)如何优化您的代码中包括程序按配置优化的各种方法。

[配置适用于 Windows XP 的程序](configuring-programs-for-windows-xp.md)如何 MSVC Windows XP 生成工具的目标。

[C/C++ 生成参考](reference/c-cpp-building-reference.md)<br/>
提供指向有关使用 C++ 生成程序、编译器和链接器选项以及各种生成工具的参考文章的链接。
