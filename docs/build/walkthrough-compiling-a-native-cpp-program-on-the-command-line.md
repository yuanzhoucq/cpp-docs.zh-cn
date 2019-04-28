---
title: 演练：编译一个本机C++命令行上的程序
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: d7b5bc88966f7edbb7179c36398b1dd95afb971f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313878"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>演练：编译一个本机C++命令行上的程序

VisualC++包括一个命令行C++可用于创建从基本的控制台应用到通用 Windows 平台应用、 桌面应用程序、 设备驱动程序和.NET 组件的编译器。

在本演练中，您将创建一个基本的"Hello，World"的样式C++通过使用文本编辑器中，程序，然后在命令行上对其进行编译。 如果你想要试用 Visual Studio IDE 而不是使用命令行，请参阅[演练：使用项目和解决方案 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用 Visual Studio IDE 的C++桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在此演练中，可使用你自己的 Visual C++ 程序（而非键入显示的程序），也可使用另一个帮助文章中的 Visual C++ 代码示例。

## <a name="prerequisites"></a>系统必备

若要完成本演练中，你必须安装 Visual Studio 和可选**使用的桌面开发C++** 工作负荷或用于 Visual Studio 命令行生成工具。

Visual Studio 是全功能的编辑器、 资源管理器、 调试器和编译器支持多种语言和平台的强大的集成的开发环境 (IDE)。 有关如何下载并安装 Visual Studio 中，包括免费的 Visual Studio Community 版，并且包括用于 c 语言的支持信息 /C++开发，请参阅[安装C++Visual Studio 中支持](vscpp-step-0-installation.md)。

Visual Studio 的生成工具安装命令行编译器、 工具和构建 C 所需的库和C++程序。 它非常适合生成实验室或教室练习和相对较快的安装。 若要安装的命令行工具，下载[Visual Studio 2017 生成工具](https://go.microsoft.com/fwlink/p/?linkid=875721)。

您可以生成一个 C 前或C++程序必须在命令行中，验证安装这些工具，并且，你可以从命令行访问它们。 VisualC++对要查找的工具、 标头和使用的库的命令行环境的复杂要求。 **不能使用视觉对象C++在纯命令提示符窗口中**而无需执行一些准备工作。 幸运的是，VisualC++安装，以便启动已设置为命令行生成环境的开发人员命令提示符快捷方式。 遗憾的是，开发人员命令提示符快捷方式和所处位置的名称是不同视觉对象的几乎每个版本中C++和在不同版本的 Windows。 在第一个演练任务查找适合使用。

> [!NOTE]
> 开发人员命令提示符快捷方式会自动设置编译器和工具，以及任何必需的标头和库的正确路径。 必须设置这些环境值自己如果使用正则表达式**命令提示符下**窗口。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。 我们建议你使用而不是构建你自己的开发人员命令提示符快捷方式。

### <a name="open-a-developer-command-prompt"></a>打开开发人员命令提示

1. 如果已在 Windows 10 上安装 Visual Studio 2017，打开开始菜单，然后选择**所有应用**。 向下滚动并打开**Visual Studio 2017**文件夹 （不是 Visual Studio 2017 应用程序）。 选择**VS 2017 开发人员命令提示**若要打开命令提示符窗口。

   如果已安装 Microsoft Visual C++ Windows 10 上生成工具 2015年打开**启动**菜单，然后选择**的所有应用**。 向下滚动并打开**可视化C++生成工具**文件夹。 选择**可视化C++2015 x86 本机工具命令提示**以打开命令提示符窗口。

   如果要使用不同版本的 Visual Studio 或在运行不同版本的 Windows，在开始菜单中查找或包含开发人员命令提示符快捷方式的 Visual Studio 工具文件夹的起始页。 此外可以使用 Windows 搜索功能搜索"开发人员命令提示符"并选择一个与你已安装的 Visual Studio 版本匹配。 使用快捷方式打开命令提示符窗口。

1. 接下来，确保视觉对象C++开发人员命令提示设置是否正确。 在命令提示符窗口中，输入`cl`并验证输出看起来类似如下：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   可能会在当前目录或版本编号，具体取决于视觉对象的版本有所不同C++和安装任何更新。 如果上面的输出类似于您看到的则已准备好生成 C 或C++在命令行程序。

   > [!NOTE]
   > 如果您遇到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件中，"错误 C1034 或错误 LNK1104 运行时**cl**命令，则可以不使用开发人员命令提示符下，或出错的视觉对象安装C++。 必须修复此问题，然后才能继续。

   如果找不到开发人员命令提示符快捷方式，或当你输入时收到错误消息`cl`，然后视觉对象C++安装可能会产生问题。 请尝试重新安装该视觉对象C++组件在 Visual Studio 中，或重新安装 Microsoft VisualC++生成工具。 不转到下一节之前此示例的工作。 有关安装和故障排除视觉对象详细信息C++，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根据上计算机和系统安全配置的 Windows 版本，您可能需要右键单击以打开开发人员命令提示符快捷方式的快捷菜单，然后选择**以管理员身份运行**到已成功生成并运行通过完成本演练创建的程序。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>创建视觉对象C++源文件，并在命令行上对其进行编译

1. 在开发人员命令提示符窗口中，输入`md c:\hello`以创建一个目录，然后输入`cd c:\hello`更改为该目录。 此目录是在其中创建源文件和编译的程序。

1. 输入`notepad hello.cpp`在命令提示符窗口中。

   选择**是**时记事本会提示您创建一个文件。 此步骤将打开一个空白的记事本窗口，供你在一个名为 hello.cpp 文件中输入你的代码。

1. 在记事本中，输入以下代码行：

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   此代码是一个简单的程序，将在屏幕上写入一行文本，然后退出。 为了尽量减少错误，请将此代码复制并粘贴到记事本中。

1. 保存所有内容！ 在记事本中，在“文件”  菜单上选择“保存” 。

   恭喜，现已创建视觉对象C++源文件、 hello.cpp，即准备进行编译。

1. 切换回开发人员命令提示窗口。 输入`dir`在命令提示符下，若要列出 c:\hello 目录的内容。 应会看到源文件 hello.cpp 中的目录列表中，类似于如下所示：

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

   您的计算机上将不同的日期，以及其他详细信息。 如果看不到源代码文件，hello.cpp，请确保已更改为你创建 c:\hello 目录，并在记事本中，请确保在此目录中保存您的源文件。 此外请确保扩展名为.cpp 文件，不带.txt 扩展名保存的源代码。

1. 在开发人员命令提示符下输入`cl /EHsc hello.cpp`来编译你的程序。

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
   > 如果您遇到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件中，"错误 C1034 或错误 LNK1104，开发人员命令提示符下未正确设置。 有关如何解决此问题的信息，请返回到**打开开发人员命令提示**部分。

   > [!NOTE]
   > 如果你获取不同的编译器或链接器错误或警告，请查看源代码以更正任何错误，然后将其保存并再次运行编译器。 有关特定错误的信息，使用搜索框在此 MSDN 页上查找错误号。

1. 若要运行 hello.exe 程序，请在命令提示处输入 `hello`。

   该程序显示以下文本并退出：

   ```Output
   Hello, world, from Visual C++!
   ```

   祝贺你，你已编译并运行C++通过使用命令行工具进行编程。

## <a name="next-steps"></a>后续步骤

此"Hello，World"示例只需大约C++程序可以获取。 实际程序具有标头文件和多个源文件，在库中，链接和执行有用的工作。

可以使用此演练中的步骤来构建您自己C++而非键入显示的示例代码的代码。 此外可以生成许多C++代码示例程序的其他位置查找。 可以将你的源代码和生成你的应用在任何可写目录中。 默认情况下，Visual Studio IDE 在文档文件夹中，名为你的 Visual Studio 版本的 Visual Studio 文件夹的项目子文件夹中创建项目。

若要编译有其他的源代码文件的程序，其所有上输入命令行中，如：

`cl /EHsc file1.cpp file2.cpp file3.cpp`

`/EHsc` 命令行选项指示编译器启用 C++ 异常处理。 有关详细信息，请参阅 [/EH（异常处理模型）](reference/eh-exception-handling-model.md)。

时提供额外的源文件时，编译器使用第一个输入的文件创建程序名称。 在这种情况下，它将输出一个名为 file1.exe 程序。 若要将名称更改为 program1.exe，添加[/out](reference/out-output-file-name.md)链接器选项：

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

若要自动捕获更多的编程错误，我们建议使用编译[/W3](reference/compiler-option-warning-level.md)或[/w4](reference/compiler-option-warning-level.md)警告等级选项：

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

编译器、 cl.exe，具有更多的选项可以应用于生成、 优化、 调试和分析你的代码。 有关快速列表中，输入`cl /?`开发人员命令提示符处。 也可以编译和链接单独并应用更复杂的生成方案中的链接器选项。 编译器和链接器选项和使用情况的详细信息，请参阅[C /C++生成参考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和生成文件或 MSBuild 和项目文件，若要配置和命令行上生成更复杂的项目。 有关使用这些工具的详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)并[MSBuild](msbuild-visual-cpp.md)。

C 和C++语言与此类似，但不是相同。 MSVC 编译器使用一个简单的规则来确定编译您的代码时要使用的语言。 默认情况下，MSVC 编译器将以.c C 源代码，结尾的所有文件和所有文件以作为.cpp 结尾的C++的源代码。 若要强制编译器将所有文件视为C++上文件扩展名，使用非依赖[/TC](reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。

MSVC 编译器包含符合 ISO C99 标准，但不是完全符合标准 C 运行时库 (CRT)。 在大多数情况下，可移植代码将编译并按预期方式运行。 VisualC++不支持的 CRT 更改一些在 ISO C11 中。 MSVC 编译器已弃用某些库函数和 POSIX 函数名称。 支持的函数，但首选的名称已更改。 有关详细信息，请参阅[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)并[编译器警告 （等级 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[MSVC 编译器选项](reference/compiler-options.md)
