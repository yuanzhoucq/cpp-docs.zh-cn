---
title: 演练：在命令行上编译本机 C++ 程序
description: 使用命令提示符中的 Microsoft C++编译器。
ms.custom: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: c24fdfdaef612059d5c2fbaaa58f10d83f5fe3a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335235"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>演练：在命令行上编译本机 C++ 程序

Visual Studio 包括命令行 C 和C++编译器。 您可以使用它创建从基本控制台应用到通用 Windows 平台应用、桌面应用、设备驱动程序和 .NET 组件的所有内容。

在本演练中，您可以使用文本编辑器创建基本"你好，世界"风格的C++程序，然后在命令行上编译它。 如果要尝试可视化工作室 IDE 而不是使用命令行，请参阅[演练：使用项目和解决方案 （C++）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或使用[可视化工作室 IDE C++桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在本演练中，您可以使用自己的C++程序，而不是键入显示的程序。 或者，您可以使用其他帮助文章中C++代码示例。

## <a name="prerequisites"></a>先决条件

要完成本演练，您必须安装具有C++工作负载的可视化工作室和可选**桌面开发**，或者安装可视化工作室的命令行构建工具。

可视化工作室是一*个集成的开发环境*（IDE）。 它支持多种语言和平台的全功能编辑器、资源管理器、调试器和编译器。 可用的版本包括免费的视觉工作室社区版本，所有版本都可以支持 C 和C++开发。 有关如何下载和安装可视化工作室的信息，请参阅[在可视化工作室中安装C++支持](vscpp-step-0-installation.md)。

Visual Studio 的构建工具仅安装构建 C 和C++程序所需的命令行编译器、工具和库。 它非常适合构建实验室或课堂练习，安装速度相对较快。 要仅安装命令行工具，请在[可视化工作室下载](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)页面上查找可视化工作室的构建工具。

在命令行上构建 C 或 C++ 程序之前，请验证工具是否已安装，并且可以从命令行访问这些工具。 可视化C++对命令行环境具有复杂的要求，用于查找它使用的工具、标头和库。 如果不进行一些准备 **，就不能在普通命令提示窗口中使用 Visual C++。** 幸运的是，Visual C++安装快捷方式，以便启动具有为命令行生成设置环境的开发人员命令提示。 遗憾的是，在几乎每个版本的 Visual C++ 和不同版本的 Windows 中，开发人员命令提示快捷方式的名称及其位置都不同。 您的第一个演练任务是找到合适的任务。

> [!NOTE]
> 开发人员命令提示快捷方式会自动设置编译器和工具以及任何必需标头和库的正确路径。 如果使用常规**命令提示**窗口，则必须自己设置这些环境值。 有关详细信息，请参阅 [为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。 我们建议您使用开发人员命令提示快捷方式，而不是构建自己的快捷方式。

### <a name="open-a-developer-command-prompt"></a>打开开发人员命令提示

1. 如果您在 Windows 10 上安装了 Visual Studio 2017 或更高版本，请打开"开始"菜单并选择 **"所有应用**"。 向下滚动并打开**可视化工作室**文件夹（不是可视化工作室应用程序）。 选择**VS 的开发人员命令提示符**以打开命令提示窗口。

   如果您在 Windows 10 上安装了 Microsoft 视觉C++构建工具 2015，请打开 **"开始"** 菜单并选择 **"所有应用**"。 向下滚动并打开 **"视觉C++生成工具"** 文件夹。 选择**可视C++ 2015 x86 本机工具命令提示符**以打开命令提示窗口。

   您还可以使用 Windows 搜索功能搜索"开发人员命令提示符"，并选择与已安装版本的 Visual Studio 相匹配的函数。 使用快捷方式打开命令提示窗口。

1. 接下来，验证可视化C++开发人员命令提示是否设置正确。 在命令提示窗口中，输入`cl`并验证输出是否如下所示：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   当前目录或版本号可能存在差异。 这些值取决于 Visual C++ 版本和安装的任何更新。 如果上述输出与您所看到的类似，那么您就可以在命令行生成 C 或C++程序。

   > [!NOTE]
   > 如果收到错误，如"'cl'未识别为内部或外部命令、可操作程序或批处理文件"，则在运行**`cl`** 该命令时出现错误 C1034 或错误 LNK1104，则表示您未使用开发人员命令提示符，或者安装 Visual C++时出现问题。 必须先解决此问题，然后才能继续。

   如果找不到开发人员命令提示快捷方式，或者在输入`cl`时收到错误消息，则 Visual C++安装可能有问题。 请尝试在可视化工作室中重新安装视觉C++组件，或重新安装 Microsoft 视觉C++构建工具。 在命令工作之前，不要转到下一**`cl`** 节。 有关安装和故障排除视觉C++的详细信息，请参阅[安装可视化工作室](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根据计算机上的 Windows 版本和系统安全配置，您可能需要右键单击才能打开开发人员命令提示快捷方式的快捷方式菜单，然后选择 **"以管理员身份运行"** 才能成功生成并运行通过本演练创建的程序。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>创建可视化C++源文件并在命令行上编译

1. 在开发人员命令提示窗口中，输入`md c:\hello`以创建目录，然后输入`cd c:\hello`更改为该目录。 此目录是创建源文件和编译程序的位置。

1. 在`notepad hello.cpp`命令提示窗口中输入。

   当记事本提示您创建文件时，请选择"**是**"。 此步骤将打开一个空白的记事本窗口，随时允许您在名为 hello.cpp 的文件中输入代码。

1. 在记事本中，输入以下代码行：

   ```cpp
   #include <iostream>
   using namespace std;
   int main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   此代码是一个简单的程序，将在屏幕上编写一行文本，然后退出。 为了尽量减少错误，请将此代码复制并粘贴到记事本中。

1. 保存所有内容！ 在记事本中，在“文件” **** 菜单上选择“保存” ****。

   恭喜您，您已经创建了一个C++源文件，hello.cpp，该文件可以编译。

1. 切换回开发人员命令提示窗口。 在`dir`命令提示符处输入以列出 c：\hello 目录的内容。 您应该在目录列表中看到源文件 hello.cpp，如下所示：

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   您的计算机上的日期和其他详细信息会有所不同。 如果您没有看到源代码文件 *，hello.cpp，* 请确保您已更改为*c：hello\\*目录。 在记事本中，请确保将源文件保存到此目录中。 还要确保使用*`.cpp`* 文件名扩展名而不是*`.txt`* 扩展名保存了源代码。

1. 在开发人员命令提示符处，`cl /EHsc hello.cpp`输入以编译程序。

   cl.exe 编译器会生成包含已编译代码的 .obj 文件，然后运行链接器来创建名为 basic.exe 的可执行程序。 此名称会显示在编译器显示的多行输出信息中。 编译器的输出应如下所示：

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > 如果收到错误，如"'cl'未识别为内部或外部命令、可操作程序或批处理文件"、"错误 C1034"或错误 LNK1104，则开发人员命令提示符设置不正确。 有关如何解决此问题的信息，请访问 **"打开开发人员命令提示符"** 部分。

   > [!NOTE]
   > 如果收到其他编译器或链接器错误或警告，请查看源代码以更正任何错误，然后保存它并再次运行编译器。 有关特定错误的信息，请使用此 MSDN 页面上的搜索框查找错误编号。

1. 若要运行 hello.exe 程序，请在命令提示处输入 `hello`。

   该程序显示以下文本并退出：

   ```Output
   Hello, world, from Visual C++!
   ```

   恭喜您，您已经使用命令行工具编译并运行了C++程序。

## <a name="next-steps"></a>后续步骤

这个"你好，世界"的例子就像一个C++程序可以得到的一样简单。 现实世界中的程序通常具有头文件、更多的源文件和指向库的链接。

您可以使用本演练中的步骤构建您自己的C++代码，而不是键入显示的示例代码。 这些步骤还允许您构建许多C++代码示例程序，这些程序是您在其他位置找到的。 您可以将源代码并构建应用到任何可写入的目录中。 默认情况下，Visual Studio IDE 会在用户文件夹中、*源\\存储库*子文件夹中创建项目。 较旧版本可能会将项目放在*文档\\可视化工作室\<版本>\\*项目* 文件夹中。

要编译具有其他源代码文件的程序，请在命令行中全部输入它们，例如：

`cl /EHsc file1.cpp file2.cpp file3.cpp`

命令`/EHsc`行选项指示编译器启用标准C++异常处理行为。 如果没有它，引发的异常可能会导致未销毁的对象和资源泄漏。 有关详细信息，请参阅 [/EH（异常处理模型）](reference/eh-exception-handling-model.md)。

当您提供其他源文件时，编译器使用第一个输入文件创建程序名称。 在这种情况下，它输出一个程序称为 file1.exe。 要将名称更改为程序1.exe，添加[/out](reference/out-output-file-name.md)链接器选项：

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

为了自动捕获更多的编程错误，我们建议您使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告级别选项进行编译：

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

编译器，cl.exe，还有更多的选项。 您可以应用它们来生成、优化、调试和分析代码。 有关快速列表，`cl /?`请输入开发人员命令提示符。 您还可以单独编译和链接，并在更复杂的生成方案中应用链接器选项。 有关编译器和链接器选项和使用情况的详细信息，请参阅[C/C++建筑参考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和制作文件、MSBuild 和项目文件（CMake）在命令行上配置和构建更复杂的项目。 有关使用这些工具的详细信息，请参阅 Visual Studio 中的[NMAKE 参考](reference/nmake-reference.md)[、MSBuild](msbuild-visual-cpp.md)和[CMake 项目](cmake-projects-in-visual-studio.md)。

C 和C++语言相似，但不同。 MSVC 编译器使用一个简单的规则来确定在编译代码时要使用的语言。 默认情况下，MSVC 编译器将结尾*`.c`* 的文件视为 C 源代码，并将结束的文件*`.cpp`* 视为C++源代码。 要强制编译器将所有文件视为独立于文件名扩展名C++，请使用[/TP](reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。

MSVC 编译器包括符合 ISO C99 标准的 C 运行时库 （CRT），但有一些小例外。 便携式代码通常按预期编译和运行。 MSVC 编译器将弃用某些过时的库函数和几个 POSIX 函数名称。 支持函数，但首选名称已更改。 有关详细信息，请参阅 CRT 和[编译器警告 （级别 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)[中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="see-also"></a>另请参阅

[C++语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和构建系统](projects-and-build-systems-cpp.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
