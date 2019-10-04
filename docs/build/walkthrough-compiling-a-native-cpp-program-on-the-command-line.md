---
title: 演练：在命令行C++上编译本机程序
description: 在命令提示符C++下使用 Microsoft 编译器。
ms.custom: conceptual
ms.date: 04/23/2019
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: 36017b28ab91478da2515cd7c8588a998013171d
ms.sourcegitcommit: c53a3efcc5d51fc55fa57ac83cca796b33ae888f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960716"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>演练：在命令行C++上编译本机程序

Visual Studio 包含一个命令行C++编译器，可用于创建从基本控制台应用到通用 Windows 平台应用、桌面应用、设备驱动程序和 .net 组件的所有内容。

在本演练中，你将使用文本编辑器创建一个基本的 "Hello C++ ，World" 样式的程序，然后在命令行上对其进行编译。 若要尝试使用 Visual Studio IDE，而不是使用命令行，请参阅 [Walkthrough：使用项目和解决方案（C++） ](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) 或[使用 Visual Studio IDE 进行C++桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在此演练中，可使用你自己的 Visual C++ 程序（而非键入显示的程序），也可使用另一个帮助文章中的 Visual C++ 代码示例。

## <a name="prerequisites"></a>先决条件

若要完成本演练，你必须已安装 visual studio 和**使用C++** 工作负荷的可选桌面开发，或用于 Visual Studio 的命令行生成工具。

Visual Studio 是一个功能强大的集成开发环境（IDE），它支持多种语言和平台的功能齐全的编辑器、资源管理器、调试器和编译器。 若要了解如何下载和安装 Visual Studio （包括免费 Visual Studio 社区版），并提供对 C/C++开发的支持，请参阅[在 Visual Studio 中安装C++支持](vscpp-step-0-installation.md)。

Visual Studio 生成工具仅安装生成 C 和C++程序所需的命令行编译器、工具和库。 这相当于构建实验室或教室练习，安装速度相对较快。 若要仅安装命令行工具，请在[Visual Studio 下载](https://visualstudio.microsoft.com/downloads/)页上查找 visual Studio 的生成工具。

在命令行上生成 C 或C++程序之前，必须先验证是否已安装这些工具，并且是否可以从命令行访问它们。 对于C++命令行环境而言，视觉对象要求查找所使用的工具、标头和库。 如果没有进行某些准备 **，就不能在普通的命令提示符窗口中使用视觉对象C++**  。 幸运的是C++ ，Visual 安装的快捷方式可让你启动开发人员命令提示，该提示已为命令行生成设置环境。 遗憾的是，开发人员命令提示快捷方式的名称以及它们所在的位置在 Visual C++和不同版本的 Windows 上都是不同的。 第一项演练任务是查找正确的操作。

> [!NOTE]
> 开发人员命令提示快捷方式自动设置编译器和工具的正确路径，以及任何所需的标头和库。 如果使用常规的**命令提示符**窗口，则必须自行设置这些环境值。 有关详细信息，请参阅 [为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。 建议使用开发人员命令提示符快捷方式，而不是构建自己的快捷方式。

### <a name="open-a-developer-command-prompt"></a>打开开发人员命令提示

1. 如果已在 Windows 10 上安装了 Visual Studio 2017 或更高版本，请打开 "开始" 菜单，并选择 "**所有应用**"。 向下滚动并打开**Visual studio**文件夹（而不是 visual studio 应用程序）。 选择 "**用于 VS" 开发人员命令提示**打开 "命令提示符" 窗口。

   如果在 Windows 10 上安装C++了 Microsoft Visual Build Tools 2015，请打开 "**开始**" 菜单，并选择 "**所有应用**"。 向下滚动并打开 **" C++视觉对象生成工具**" 文件夹。 选择 **" C++ Visual 2015 x86 本机工具命令提示**打开" 命令提示符 "窗口。

   你还可以使用 Windows search 函数搜索 "开发人员命令提示"，并选择与已安装的 Visual Studio 版本相匹配的工具。 使用快捷方式打开 "命令提示符" 窗口。

1. 接下来，验证是否正确C++设置了 Visual developer 命令提示符。 在 "命令提示符" 窗口中，输入 `cl` 并验证输出如下所示：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   根据视觉对象C++和安装的任何更新的版本，当前目录或版本号可能有所不同。 如果上面的输出类似于你所看到的内容，则可以在命令行上生成C++ C 或程序。

   > [!NOTE]
   > 如果收到错误，如 "' cl ' 无法识别为内部或外部命令、可操作程序或批处理文件"、"错误 C1034" 或 "错误 LNK1104" （运行**cl**命令时），则可能是你未使用开发人员命令提示，或出现了错误安装您的视觉对象C++。 必须先解决此问题，然后才能继续。

   如果你找不到 "开发人员命令提示" 快捷方式，或者当你输入 `cl` 时收到错误消息，则C++你的视觉对象安装可能有问题。 尝试在 Visual Studio C++中重新安装视觉组件，或重新安装 Microsoft C++ visual Build Tools。 请不要继续执行下一节，直到这样做。 若要详细了解如何安装视觉对象C++，请参阅[安装 visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根据计算机上的 Windows 版本和系统安全配置，您可能必须右键单击以打开 "开发人员命令提示" 快捷方式的快捷菜单，然后选择 "以**管理员身份运行**" 才能成功生成并运行按照此演练创建的程序。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>创建一个 Visual C++源文件，并在命令行上对其进行编译

1. 在 "开发人员命令提示" 窗口中，输入 `md c:\hello` 创建目录，然后输入 `cd c:\hello` 以更改到该目录。 此目录是在其中创建源文件和已编译程序的位置。

1. 在命令提示符窗口中输入 `notepad hello.cpp`。

   当记事本提示您创建文件时，请选择 **"是"** 。 此步骤将打开一个空白的 "记事本" 窗口，您可以在名为 "hello" 的文件中输入代码。

1. 在记事本中，输入以下代码行：

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   此代码是一个简单的程序，它将在屏幕上写入一行文本，然后退出。 为了尽量减少错误，请将此代码复制并粘贴到记事本中。

1. 保存所有内容！ 在记事本中，在“文件” 菜单上选择“保存”。

   恭喜，你已经创建了C++一个已准备好进行编译的源文件。

1. 切换回 "开发人员命令提示" 窗口。 在命令提示符下输入 `dir` 以列出 c:\hello 目录的内容。 目录列表中应会显示 "源文件"，如下所示：

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

   在您的计算机上，日期和其他详细信息会有所不同。 如果看不到源代码文件 "你好"，请确保已更改为所创建的 c:\hello 目录，并在记事本中确保已将源文件保存在此目录中。 此外，请确保已保存带有 .cpp 文件扩展名（而不是 .txt 扩展名）的源代码。

1. 在开发人员命令提示符处，输入 `cl /EHsc hello.cpp` 以编译程序。

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
   > 如果收到错误，如 "' cl ' 无法识别为内部或外部命令、可运行程序或批处理文件"、"错误 C1034" 或 "错误 LNK1104"，则不会正确设置开发人员命令提示。 有关如何解决此问题的信息，请返回到 "**打开开发人员命令提示**" 部分。

   > [!NOTE]
   > 如果收到不同的编译器或链接器错误或警告，请查看源代码以更正任何错误，然后保存并再次运行编译器。 有关特定错误的信息，请使用此 MSDN 页上的 "搜索" 框来查找错误号。

1. 若要运行 hello.exe 程序，请在命令提示处输入 `hello`。

   该程序显示以下文本并退出：

   ```Output
   Hello, world, from Visual C++!
   ```

   恭喜，你已使用命令行工具C++编译并运行程序。

## <a name="next-steps"></a>后续步骤

此 "Hello，World" 示例与C++程序一样简单。 实际程序具有标头文件和更多源文件，在库中链接，并执行有用的工作。

您可以使用本演练中的步骤来生成自己C++的代码，而不是键入所示的示例代码。 你还可以生成多C++个在其他位置找到的代码示例程序。 你可以在任何可写目录中放置你的源代码并构建你的应用程序。 默认情况下，Visual Studio IDE 会在 "文档" 文件夹中的 "项目" 子文件夹中的 visual Studio 文件夹的 "项目" 子文件夹中创建项目。

若要编译具有其他源代码文件的程序，请在命令行上输入它们，如下所示：

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc` 命令行选项指示编译器启用 C++ 异常处理。 有关详细信息，请参阅 [/EH（异常处理模型）](reference/eh-exception-handling-model.md)。

提供其他源文件时，编译器将使用第一个输入文件来创建程序名称。 在这种情况下，它将输出名为 file1 的程序。 若要将名称更改为 program1，请添加[/out](reference/out-output-file-name.md)链接器选项：

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

为了自动捕获更多的编程错误，我们建议使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告等级选项进行编译：

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

编译器（node.js）有更多选项可用于生成、优化、调试和分析代码。 对于 "快速列表"，请在开发人员命令提示符下输入 `cl /?`。 你还可以单独编译和链接，并在更复杂的生成方案中应用链接器选项。 有关编译器和链接器选项和用法的详细信息，请参阅[C/C++生成引用](reference/c-cpp-building-reference.md)。

可以在命令行中使用 NMAKE 和生成文件、MSBuild 和项目文件来配置和生成更复杂的项目。 有关使用这些工具的详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)和[MSBuild](msbuild-visual-cpp.md)。

C 和语言C++类似，但并不相同。 MSVC 编译器使用简单的规则来确定在编译代码时要使用的语言。 默认情况下，MSVC 编译器会将以 .c 结尾的所有文件视为 C 源代码，并将以 .cpp 结尾的所有文件视为C++源代码。 若要强制编译器将所有文件视为C++不依赖于文件扩展名，请使用[/tp](reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。

MSVC 编译器包含与 ISO C99 standard 兼容但不严格相容的 C 运行时库（CRT）。 在大多数情况下，可移植代码将按预期方式进行编译和运行。 视觉C++对象不支持 ISO C11 中的某些 CRT 更改。 某些库函数和 POSIX 函数名称已被 MSVC 编译器弃用。 支持函数，但首选名称已更改。 有关详细信息，请参阅[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)和[编译器警告（等级3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
