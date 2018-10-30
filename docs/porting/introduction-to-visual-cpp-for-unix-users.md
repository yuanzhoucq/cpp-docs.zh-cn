---
title: Visual C++ 简介（针对 UNIX 用户）| Microsoft Docs
ms.custom: ''
ms.date: 09/01/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 963a43987163bf390f2ded652c5ea56eaa58bcb8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066963"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Visual C++ 简介（针对 UNIX 用户）

本主题的内容适用于不熟悉 Visual Studio 且希望使用 C++ 及 Visual Studio 集成开发环境 (IDE) 高效工作的 UNIX 用户。

## <a name="getting-started-on-the-command-line"></a>首先使用命令行

可按使用 UNIX 命令行环境的相似方式来使用命令行中的 C++ 编译器。 使用命令行 C 和 C++ 编译器 (CL.EXE)、链接器 (LINK.EXE) 以及包括 NMAKE.EXE（Microsoft 版 UNIX make 实用工具）在内的其他工具，从命令提示符进行编译。

在 UNIX 中，命令安装在常用文件夹中，例如 /usr/bin。 在 Visual Studio 中，命令行工具安装在 VC\bin 子目录及其子目录的 Visual Studio 安装目录中。 不同于 UNIX，这些工具在纯命令提示符窗口中不可用。 要使用命令行工具，请使用开发者命令提示符快捷方式，或者运行 vcvarsall.bat 等开发者命令文件。 此操作设置路径和从命令行编译 C++ 程序所必需的其他环境变量。 有关详细信息，请参阅[在命令行上生成 C/C++ 代码](../build/building-on-the-command-line.md)和[演练：在命令行上编译本机 C++ 程序](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。

要打开开发者命令提示符快捷方式，请在桌面搜索控件中输入“开发者命令提示符”，然后选择适用于你的 Visual Studio 版本的“开发者命令提示符”结果。 要选择为特定主机和目标体系结构预配置的开发者命令提示符，请打开“开始”菜单（桌面一角的 Windows 图标），然后滚动到你的 Visual Studio 版本的文件夹，例如“Visual Studio 2017”。 打开文件夹，选择首选主机和目标体系结构的命令提示符快捷方式。

要利用更强大的功能（例如 Visual Studio 调试程序、IntelliSense 代码查找和语句完成、可视化设计器、项目管理等），需要使用 Visual Studio IDE。

## <a name="debugging-your-code"></a>调试代码

如果使用命令行并在开发工作站上运行应用程序，则在代码遇到内存访问冲突、未处理的异常或其他不可恢复的错误时，将显示运行 Visual Studio 调试器的对话框。 如果单击“确定”，将启动 Visual Studio 开发环境，并且在故障点之前调试器都将打开。 可按此方法调试应用程序，而且在这种情况下，只有在使用 [/Z7、/Zi、/ZI（调试信息格式）](../build/reference/z7-zi-zi-debug-information-format.md)交换机进行编译时，源代码才可用。 有关详细信息，请参阅[调试本机代码](/visualstudio/debugger/debugging-native-code)和[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="using-the-development-environment"></a>使用开发环境

使用开发环境更容易在项目中编辑和生成源代码。 项目是指将编译到单个单元（如库或可执行文件）中的源文件和相关文件的集合。 项目还包括文件生成方式的相关信息。 项目的相关信息存储在扩展名为 .prj 的项目文件中。

单个解决方案中内含的多个项目中存储了包含多个库和可执行文件的应用程序，其中每个库或文件都可以一组不同的编译器选项，或甚至以不同语言生成。 解决方案是容器的抽象概念，用来将多个项目组合在一起。 解决方案的相关信息存储在扩展名为 .sln 的解决方案文件中。 有关详细信息，请参阅[Visual Studio 中的解决方案和项目](/visualstudio/ide/solutions-and-projects-in-visual-studio)和[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="importing-your-existing-code"></a>导入现有代码

可使用 C++ 编译器生成现有代码（无论代码是设置为使用生成文件进行编译还是不用此文件），再将其放入 Visual Studio 项目。 有关详细信息，请参阅[如何：通过现有代码创建 C++ 项目](../ide/how-to-create-a-cpp-project-from-existing-code.md)。

## <a name="creating-a-new-project"></a>创建新项目

可在开发环境中创建新项目。 Visual Studio 具备大量提供各种常见项目的标准代码的模板。 可使用应用程序向导为各种应用程序类型生成具有代码大纲的项目。

可以使用 **“控制台应用程序 (Win32) 向导”** 开始创建空项目。 选择“空项目”复选框。 然后稍后可将新的和现有文件添加到项目。

当创建项目时，必须对其进行命名。 默认情况下，项目名称即为动态链接库 (DLL) 或从此项目生成的可执行文件的名称。 有关详细信息，请参阅[创建解决方案和项目](/visualstudio/ide/creating-solutions-and-projects)。

## <a name="microsoft-specific-modifiers"></a>Microsoft 专用的修饰符

Microsoft Visual C++ 编译器实现了一些对标准 C++ 编程语言的扩展，支持 Windows 操作系统编程。 这些扩展用于指定存储类特性、函数调用约定和基于寻址以及其他用途。 有关所有受支持的 C++ 扩展的完整列表，请参阅 [Microsoft 专用的修饰符](../cpp/microsoft-specific-modifiers.md)。

可以使用 `/Za` 编译器选项禁用所有特定于 Microsoft 的 C++ 扩展。 如果希望编写可在多个平台上运行的代码，建议使用此选项。 有关 `/Za` 编译器选项的详细信息，请参阅 [/Za、/Ze（禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md)。 有关 C++ 编译器符合性的详细信息，请参阅 [Visual C++ 语言符合性](../visual-cpp-language-conformance.md)和[非标准行为](../cpp/nonstandard-behavior.md)。

## <a name="precompiled-headers"></a>预编译标头

Microsoft C 和 C++ 编译器提供预编译任何 C 或 C++ 代码（包括内联代码）的选项。 使用此性能功能，可以编译稳定的代码正文，在文件中存储已编译的代码状态，并在后续编译过程中将预编译代码和仍在开发的代码合并在一起。 每个后续编译的速度都更快，因为无需重新编译稳定的代码。

默认情况下，所有预编译的代码均在文件 stdafx.h 和 stdafx.cpp 中进行指定。 “新建项目”向导将自动创建这些文件，除非取消选择“预编译标头”选项。 有关预编译标头的详细信息，请参阅[创建预编译标头文件](../build/reference/creating-precompiled-header-files.md)。

## <a name="related-sections"></a>相关章节

有关详细信息，请参阅[从 UNIX 到 Win32 的迁移](../porting/porting-from-unix-to-win32.md)。

## <a name="see-also"></a>请参阅

[生成 C/C++ 程序](../build/building-c-cpp-programs.md)