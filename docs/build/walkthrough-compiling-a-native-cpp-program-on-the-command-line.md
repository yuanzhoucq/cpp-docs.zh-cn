---
title: 演练： 编译本机 c + + 程序命令行上 |Microsoft 文档
ms.custom: conceptual
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb0d7aab8000febdf07288370da058f437767387
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322428"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>演练：在命令行上编译本机 C++ 程序

Visual c + + 包括一个命令行的 c + + 编译器，可用来创建从基本控制台应用到通用 Windows 平台应用程序、 桌面应用、 设备驱动程序和.NET 组件。

在本演练中，你可以创建一个基本的"Hello，World"-通过使用文本编辑器中，样式 c + + 程序，然后在命令行上对其进行编译。 如果你想要尝试 Visual Studio IDE 而不是使用命令行，请参阅[演练： 使用项目和解决方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

在此演练中，可使用你自己的 Visual C++ 程序（而非键入显示的程序），也可使用另一个帮助文章中的 Visual C++ 代码示例。

## <a name="prerequisites"></a>系统必备

若要完成本演练，你必须已安装 Visual Studio 和可选**使用 c + + 桌面开发**工作负荷或命令行生成 Tools for Visual Studio。

Visual Studio 是针对许多语言和平台支持齐全编辑器、 资源管理器、 调试器和编译器的功能强大的集成的开发环境 (IDE)。 有关如何下载并安装 Visual Studio 中，包括免费 Visual Studio Community 版中，以及如何包括针对 C/c + + 开发的支持的信息，请参阅[Visual Studio 中的安装 c + + 支持](../build/vscpp-step-0-installation.md)。

生成 Tools for Visual Studio 安装命令行编译器、 工具和生成 C 和 c + + 程序所需的库。 它非常适用于生成实验室或教室练习，并且安装相对快一点。 若要只安装命令行工具，下载[生成 Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721)。

你可以在命令行上生成 C 或 c + + 程序之前，必须验证，安装工具，并且，你可以从命令行访问它们。 Visual c + + 查找工具、 标头和使用的库具有复杂的命令行环境要求。 **不能使用 Visual c + + 中的普通命令提示符窗口**而无需执行一些准备工作。 幸运的是，Visual c + + 安装可启动具有为命令行生成设置的环境的开发人员命令提示快捷的方式。 遗憾的是，开发人员命令提示符快捷方式和他们的位置的名称是几乎每个版本的 Visual c + + 和在不同版本的 Windows 中不同。 你的第一个演练任务发现右要使用。

> [!NOTE]
> 开发人员命令提示符快捷方式会自动设置编译器和工具，以及任何必需的标头和库的正确路径。 你必须设置这些环境值自己如果使用常规的命令提示符窗口。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。 我们建议你使用而不是生成你自己的开发人员命令提示符快捷方式。

### <a name="open-a-developer-command-prompt"></a>打开开发人员命令提示

1. 如果你已在 Windows 10 上安装 Visual Studio 2017，打开开始菜单，然后选择**所有应用**。 向下滚动并打开**Visual Studio 2017**文件夹 （不是 Visual Studio 2017 应用程序）。 选择**VS 2017 的开发人员命令提示符**打开命令提示符窗口。

   如果你在 Windows 10 上安装 Microsoft Visual c + + 生成工具 2015年，打开**启动**菜单，然后选择**所有应用**。 向下滚动并打开**Visual c + + 生成工具**文件夹。 选择**Visual c + + 2015 x86 本机工具命令提示**打开命令提示符窗口。

   如果你正在使用不同版本的 Visual Studio 或运行不同版本的 Windows，在开始菜单中查找或启动包含开发人员命令提示符快捷方式的 Visual Studio 工具文件夹的页。 你可以使用 Windows search 函数要搜索的"开发人员命令提示符"，然后选择一个与你安装 Visual Studio 的版本。 使用快捷方式打开命令提示符窗口。

2. 接下来，验证正确设置 Visual c + + 开发人员命令提示。 在命令提示符窗口中，输入`cl`并验证输出看起来类似如下内容：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   可能在当前目录或版本号，具体取决于 Visual c + + 和安装任何更新的版本存在差异。 如果这是类似于你所看到的内容，然后你就可以生成在命令行 C 或 c + + 程序。

   > [!NOTE]
   > 如果你收到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件"错误 C1034 或错误 LNK1104 运行时**cl**命令时，则或者你不使用开发人员命令提示，或有问题与你安装的 Visual c + +。 你必须修复此问题，然后才能继续。

   如果找不到开发人员命令提示符快捷方式，或当你输入时收到错误消息`cl`，则你的 Visual c + + 安装可能会产生问题。 请尝试重新安装 Visual c + + 组件在 Visual Studio 中，或重新安装 Microsoft Visual c + + 生成工具。 不继续到下一节之前之所以能够正常。 有关安装和 Visual c + + 疑难解答的详细信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 具体取决于计算机和系统安全配置上的 Windows 版本，你可能需要右键单击以打开开发人员命令提示符快捷方式的快捷菜单，然后选择**以管理员身份运行**到已成功生成并运行通过完成本演练创建的程序。

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>创建 Visual c + + 源文件并在命令行上对其进行编译

1. 在开发人员命令提示符窗口中，输入**md c:\hello**以创建一个目录，然后输入**cd c:\hello**更改为该目录。 这是您的源文件和已编译的程序中创建的目录。

2. 输入**notepad hello.cpp**在命令提示符窗口。

   选择**是**记事本提示你创建文件时。 这将打开一个空白的记事本窗口，供你在一个名为 hello.cpp 文件中输入你的代码。

3. 在记事本中，输入以下代码行：

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   这是一个非常简单的程序，会在屏幕上写入一行文本，然后退出。 为了尽量减少错误，请将此代码复制并粘贴到记事本中。

4. 保存所有内容！ 在记事本中，在“文件”  菜单上选择“保存” 。

   祝贺你，你创建了 Visual c + + 源文件，hello.cpp，即准备进行编译。

5. 切换回开发人员命令提示符窗口。 输入**dir**在命令提示符下，若要列出 c:\hello 目录的内容。 你应看到源文件 hello.cpp 在目录列表中，如下所示：

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

   在你的计算机上，日期和其他详细信息也将有所不同。 如果看不到源代码文件中，hello.cpp，请确保你已更改为 c:\hello 创建的目录，并在记事本中，请确保你在此目录中保存源文件。 此外请确保扩展名为.cpp 文件，不.txt 扩展名保存的源代码。

6. 在开发人员命令提示符下输入`cl /EHsc hello.cpp`来编译你的程序。

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
   > 如果你收到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件"错误 C1034 或错误 LNK1104，你的开发人员命令提示未正确设置。 有关如何解决此问题的信息，请返回到**打开开发人员命令提示**部分。

   > [!NOTE]
   > 如果您收到不同的编译器或链接器错误或警告，查看你的源代码以更正任何错误，然后将其保存并再次运行编译器。 有关特定错误的信息，使用搜索框此 MSDN 页面上查找错误号。

7. 若要运行 hello.exe 程序，请在命令提示处输入 `hello`。

   该程序显示以下文本并退出：

   ```Output
   Hello, world, from Visual C++!
   ```

   祝贺你，你刚刚编译并运行通过使用命令行工具的 c + + 程序。

## <a name="next-steps"></a>后续步骤

此"Hello，World"示例是最简单的 c + + 程序可以获得。 现实世界程序具有标头文件和多个源文件，在库中，链接和执行有用的工作。

可以使用此演练中的步骤来生成你自己的 c + + 代码，而非键入显示的示例代码。 你也可以生成许多其他位置查找的 c + + 代码示例程序。 你可以将你的源代码，并生成任何可写目录中的应用。 默认情况下，Visual Studio IDE 在文档文件夹中，名为你的 Visual Studio 版本的 Visual Studio 文件夹的项目子文件夹中创建项目。

若要编译有多个源代码文件的程序，输入在命令行，如下：

`cl /EHsc file1.cpp file2.cpp file3.cpp`

**/EHsc** 命令行选项指示编译器启用 C++ 异常处理。 有关详细信息，请参阅 [/EH（异常处理模型）](../build/reference/eh-exception-handling-model.md)。

当你提供类似的多个源文件时，编译器将使用第一个输入的文件以创建程序名称。 在这种情况下，它将输出一个名为 file1.exe 程序。 若要将名称更改为 program1.exe，添加[/out](../build/reference/out-output-file-name.md)链接器选项：

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

若要自动捕获更多的编程错误，我们建议你通过使用编译和[/W3](../build/reference/compiler-option-warning-level.md)或[/W4](../build/reference/compiler-option-warning-level.md)警告等级选项：

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

编译器，cl.exe，具有更多的选项可以将应用于生成、 优化、 调试和分析你的代码。 有关快速列表中，输入**cl /？** 在开发人员命令提示符。 你还可以编译和链接单独并应用更复杂的生成方案中的链接器选项。 编译器和链接器选项以及使用情况的详细信息，请参阅[C/c + + 生成参考](../build/reference/c-cpp-building-reference.md)。

可以使用 NMAKE 和生成文件或 MSBuild 和项目文件来配置和命令行上生成更复杂的项目。 有关使用这些工具的详细信息，请参阅[NMAKE 参考](../build/nmake-reference.md)和[MSBuild](../build/msbuild-visual-cpp.md)。

C 和 c + + 语言与此类似，但不是相同。 Visual c + + 编译器使用简单规则来确定它编译你的代码时要使用的语言。 默认情况下，Visual C++ 编译器将以 .c 结尾的所有文件视为 C 源代码，将以 .cpp 结尾的所有文件视为 C++ 源代码。 若要强制编译器将所有文件视为 c + +，而不管文件扩展名如何，使用[/TC](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。

Visual c + + 编译器将包含符合 ISO C99 标准中，但不严格符合 C 运行库 (CRT)。 在大多数情况下，可移植代码将编译并按预期方式运行。 Visual c + + 不支持某些 CRT 更改在 ISO C11 中。 由 Visual c + + 编译器已弃用某些库函数和 POSIX 函数名称。 支持的函数，但首选的名称已更改。 有关详细信息，请参阅[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)和[编译器警告 （等级 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>请参阅

[C++ 语言参考](../cpp/cpp-language-reference.md)  
[生成 C/C++ 程序](../build/building-c-cpp-programs.md)  
[编译器选项](../build/reference/compiler-options.md)  
