---
title: Microsoft C++ For UNIX 用户简介
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 791c513553acbd300204746ae1e1dddf7a3ae5c4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626991"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>Microsoft C++ For UNIX 用户简介

本主题为所有种类的 UNIX 用户提供信息，这些用户不熟悉 Visual Studio，并且想要通过命令C++行或使用 Visual Studio 提高工作效率。 可以将 Visual Studio 与 Microsoft C++编译器结合使用来面向 Windows。 你还可以在 UNIX 环境（如远程 Linux 计算机，MinGW-mingw-w64）和 Windows 子系统（适用于 Linux）中使用带有 GCC 或 Clang 的 Visual Studio IDE。 若要C++在 Visual Studio 中使用，必须安装带有**C++** 工作负荷的桌面开发。 打开 Visual Studio 安装程序安装工作负荷，或者添加或删除可选组件。 如果要以远程 linux 计算机为目标，还应**使用C++** 工作负荷安装 Linux 开发。 对于 Android 或 iOS 开发，请安装**具有C++** 工作负载的移动开发。

## <a name="getting-started-on-the-command-line"></a>命令行入门

你可以从命令行C++使用 Microsoft 编译器，其方式与使用 UNIX 命令行环境类似。 使用命令行 C 和 C++ 编译器 (CL.EXE)、链接器 (LINK.EXE) 以及包括 NMAKE.EXE（Microsoft 版 UNIX make 实用工具）在内的其他工具，从命令提示符进行编译。

在 UNIX 中，命令安装在常用文件夹中，例如 /usr/bin。 在 Visual Studio 中，命令行工具安装在 VC\bin 子目录及其子目录的 Visual Studio 安装目录中。 不同于 UNIX，这些工具在纯命令提示符窗口中不可用。 若要使用命令行工具，必须使用特殊的开发人员命令提示，该提示设置编译C++程序所必需的路径和其他环境变量。 有关详细信息，请参阅[在命令行上生成 C/C++ 代码](../build/building-on-the-command-line.md)和[演练：在命令行上编译本机 C++ 程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。

## <a name="debugging-your-code"></a>调试代码

你可以从命令行或从 IDE 中C++使用适用于 Microsoft 项目的 Visual Studio 调试器。 使用[/Z7、/zi、/zi （调试信息格式）](../build/reference/z7-zi-zi-debug-information-format.md)交换机进行编译，以便能够逐步执行源。 有关详细信息，请参阅[调试本机代码](/visualstudio/debugger/debugging-native-code)和[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

对于用 GCC 或 Clang 编译的程序，Visual Studio 将调用 GDB、LLDB 或指定的任何自定义调试器。

## <a name="visual-studio-project-system"></a>Visual Studio 项目系统

Visual Studio 项目系统称为 MSBuild。 它使用 XML 格式的项目文件;C++项目文件的扩展名为 .vcxproj。 单个解决方案中内含的多个项目中存储了包含多个库和可执行文件的应用程序，其中每个库或文件都可以一组不同的编译器选项，或甚至以不同语言生成。 解决方案是容器的抽象概念，用来将多个项目组合在一起。 解决方案的相关信息存储在扩展名为 .sln 的解决方案文件中。 有关详细信息，请参阅[Visual Studio 中的解决方案和项目](/visualstudio/ide/solutions-and-projects-in-visual-studio)和[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。 从主菜单中，选择 "**文件**" " > **新建** > **项目**" 以查看可用的 Visual Studio 项目模板。

从 Visual Studio 2017 开始，添加了对 CMake 项目的支持，并提供了有关将 Microsoft C++编译器与任意生成系统一起使用的选项，以及用于源文件和无项目文件的松散文件夹的选项。 有关详细信息，请参阅[Visual studio 中的 CMake 项目](../build/cmake-projects-in-visual-studio.md)和[visual Studio 中的打开文件夹项目](../build/open-folder-projects-cpp.md)。

## <a name="microsoft-specific-modifiers"></a>Microsoft 专用的修饰符

Microsoft C++ 编译器实现对标准 C++ 编程语言的多个扩展，以支持 Windows 操作系统编程。 这些扩展用于指定存储类特性、函数调用约定和基于寻址以及其他用途。 有关所有受支持的 C++ 扩展的完整列表，请参阅 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)。

可以使用 `/Za` 编译器选项禁用所有特定于 Microsoft 的 C++ 扩展。 如果希望编写可在多个平台上运行的代码，建议使用此选项。 有关 `/Za` 编译器选项的详细信息，请参阅 [/Za、/Ze（禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)。 有关C++编译器一致性的详细信息，请[参阅C++ Microsoft Language 一致性表](../overview/visual-cpp-language-conformance.md)和[非标准行为](../cpp/nonstandard-behavior.md)。

## <a name="precompiled-headers"></a>预编译头

Microsoft C 和 C++ 编译器提供预编译任何 C 或 C++ 代码（包括内联代码）的选项。 使用此性能功能，可以编译稳定的代码正文，在文件中存储已编译的代码状态，并在后续编译过程中将预编译代码和仍在开发的代码合并在一起。 每个后续编译的速度都更快，因为无需重新编译稳定的代码。

默认情况下，所有预编译代码都是在文件 pch.h 和 pch.cpp（Visual Studio 2017 及更低版本中的 stdafx.h 和 stdafx.cpp）中指定。 有关预编译标头的详细信息，请参阅[创建预编译标头文件](../build/creating-precompiled-header-files.md)。

## <a name="related-sections"></a>相关章节

有关详细信息，请参阅[在 Windows 上运行 Linux 程序](../porting/porting-from-unix-to-win32.md)。

## <a name="see-also"></a>请参阅

[项目和生成系统](../build/projects-and-build-systems-cpp.md)
