---
title: 演练：编译 C 程序命令行上
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: 54f5810e60cdaada6a99651a732570c88ea883ce
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822218"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>演练：编译 C 程序命令行上

Visual c + + 包括一个 C 编译器，可用于创建从基本的控制台程序到完整的 Windows 桌面应用程序、 移动应用和的详细信息。

本演练演示如何创建基本的"Hello，World"-使用文本编辑器中，样式 C 程序中，然后在命令行上对其进行编译。 如果您想使用 c + + 中命令行上，请参阅[演练：编译本机 c + + 程序命令行上](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果你想要试用 Visual Studio IDE 而不是使用命令行，请参阅[演练：使用项目和解决方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用 Visual Studio IDE 进行 c + + 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>系统必备

若要完成本演练中，你必须安装 Visual Studio 和可选的 Visual c + + 组件或生成工具用于 Visual Studio。

Visual Studio 是全功能的编辑器、 资源管理器、 调试器和编译器支持多种语言和平台的强大的集成的开发环境。 了解这些功能以及如何下载和安装 Visual Studio 中，包括免费的 Visual Studio Community 版，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

用于 Visual Studio 版本的 Visual Studio 的生成工具安装仅命令行工具集、 编译器、 工具和生成 C 和 c + + 程序所需的库。 它非常适合生成实验室或教室练习和相对较快的安装。 若要安装仅命令行工具集，请下载[用于 Visual Studio 生成工具](https://go.microsoft.com/fwlink/p/?linkid=875721)运行安装程序。

可以在命令行上生成的 C 或 c + + 程序前，必须验证安装了工具，以及，您可以从命令行访问它们。 Visual c + + 有复杂要求要查找的工具、 标头和使用的库的命令行环境。 **不能在普通命令提示符窗口中使用 Visual c + +** 而无需一些准备工作。 所需*开发人员命令提示*窗口中，这是一个常规的命令提示窗口，但不包含设置的所有必需的环境变量。 幸运的是，Visual c + + 安装用于启动已设置为命令行生成环境的开发人员命令提示快捷的方式。 遗憾的是，开发人员命令提示符快捷方式和所处位置的名称是在几乎每个版本的 Visual c + + 和不同版本的 Windows 上不同的。 在第一个演练任务是查找正确的快捷方式，以便使用。

> [!NOTE]
> 开发人员命令提示符快捷方式会自动设置编译器和工具，以及任何必需的标头和库的正确路径。 其中某些值是不同的每个生成配置。 您必须设置这些环境值自己如果不使用其中一个快捷方式。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。 生成环境很复杂，因为我们强烈建议你使用而不是构建你自己的开发人员命令提示符快捷方式。

## <a name="open-a-developer-command-prompt"></a>打开开发人员命令提示

1. 如果已在 Windows 10 上安装 Visual Studio 2017，打开开始菜单，然后向下滚动并打开**Visual Studio 2017**文件夹 （不是 Visual Studio 2017 应用程序）。 选择**VS 2017 开发人员命令提示**若要打开命令提示符窗口。

   如果已在 Windows 10 上安装 Microsoft Visual c + + 生成工具 2015年，打开**启动**菜单，然后向下的滚动并打开**Visual c + + 生成工具**文件夹。 选择**Visual c + + 2015 x86 本机工具命令提示**若要打开命令提示符窗口。

   如果要使用不同版本的 Visual Studio 或在运行不同版本的 Windows，在开始菜单中查找或包含开发人员命令提示符快捷方式的 Visual Studio 工具文件夹的起始页。 此外可以使用 Windows 搜索功能搜索"开发人员命令提示符"并选择一个与你已安装的 Visual Studio 版本匹配。 使用快捷方式打开命令提示符窗口。

1. 接下来，验证正确设置 Visual c + + 开发人员命令提示。 在命令提示符窗口中，输入`cl`并验证输出看起来类似如下：

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   可能存在的当前目录或版本号，具体取决于 Visual c + + 和安装任何更新的版本之间的差异。 如果上面的输出类似于您所看到的内容，然后你便可以构建在命令行 C 或 c + + 程序。

   > [!NOTE]
   > 如果您遇到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件中，"错误 C1034 或错误 LNK1104 运行时**cl**命令，则可以不使用开发人员命令提示符下，或有问题与你安装的 Visual c + +。 必须修复此问题，然后才能继续。

   如果找不到开发人员命令提示符快捷方式，或当你输入时收到错误消息`cl`，则您的 Visual c + + 安装可能存在问题。 如果您使用的 Visual Studio 2017，请尝试重新安装**使用 c + + 的桌面开发**在 Visual Studio 安装程序的工作负荷。 有关详细信息，请参阅[Visual Studio 中的安装 c + + 支持](vscpp-step-0-installation.md)。 或重新安装[用于 Visual Studio 生成工具](https://go.microsoft.com/fwlink/p/?linkid=875721)。 不转到下一节之前此示例的工作。 有关安装和故障排除 Visual Studio 的详细信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

   > [!NOTE]
   > 根据上计算机和系统安全配置的 Windows 版本，您可能需要右键单击以打开开发人员命令提示符快捷方式的快捷菜单，然后选择**以管理员身份运行**到已成功生成并运行通过完成本演练创建的程序。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>创建 C 源文件并在命令行上对其进行编译

1. 在开发人员命令提示符窗口中，输入`cd c:\`若要将当前工作目录更改为 c： 驱动器的根目录。 接下来，输入`md c:\simple`以创建一个目录，然后输入`cd c:\simple`更改为该目录。 此目录会保存您的源文件和编译的程序。

1. 输入`notepad simple.c`开发人员命令提示符处。 在弹出的记事本警报对话框，选择**是**在工作目录中创建新的 simple.c 文件。

1. 在记事本中，输入以下代码行：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在记事本的菜单栏上依次选择**文件** > **保存**simple.c 保存在工作目录中。

1. 切换回开发人员命令提示窗口。 输入`dir`在命令提示符下，若要列出 c:\simple 目录的内容。 应会看到源文件 simple.c 中的目录列表中，类似于如下所示：

    ```Output
    C:\simple>dir
     Volume in drive C has no label.
     Volume Serial Number is CC62-6545

     Directory of C:\simple

    10/02/2017  03:46 PM    <DIR>          .
    10/02/2017  03:46 PM    <DIR>          ..
    10/02/2017  03:36 PM               143 simple.c
                   1 File(s)            143 bytes
                   2 Dir(s)  514,900,566,016 bytes free

    ```

   您的计算机上将不同的日期，以及其他详细信息。 如果看不到源代码文件，simple.c，请确保已更改为 c:\simple 你创建的目录，并在记事本中，请确保在此目录中保存您的源文件。 此外请确保扩展名为.c 文件，不带.txt 扩展名保存的源代码。

1. 若要编译你的程序，请输入`cl simple.c`开发人员命令提示符处。

   可以看到可执行程序的名称，simple.exe，在编译器显示的输出信息的行中：

    ```Output
    c:\simple>cl simple.c
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
    Copyright (C) Microsoft Corporation.  All rights reserved.

    simple.c
    Microsoft (R) Incremental Linker Version 14.10.25017.0
    Copyright (C) Microsoft Corporation.  All rights reserved.

    /out:simple.exe
    simple.obj
    ```

   > [!NOTE]
   > 如果您遇到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件中，"错误 C1034 或错误 LNK1104，开发人员命令提示符下未正确设置。 有关如何解决此问题的信息，请返回到**打开开发人员命令提示**部分。

   > [!NOTE]
   > 如果你获取不同的编译器或链接器错误或警告，请查看源代码以更正任何错误，然后将其保存并再次运行编译器。 有关特定错误的信息，使用搜索框中的此页顶部以查找错误号。

1. 若要运行程序，请输入`simple`在命令提示符处。

   程序将在显示以下文本后退出：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   祝贺你，你已编译并运行 C 程序中使用命令行。

## <a name="next-steps"></a>后续步骤

此"Hello，World"示例是最简单如 C 程序中可以获取。 实际程序具有标头文件和多个源文件，在库中，链接和执行有用的工作。

可以使用在本演练中的步骤来生成你自己的 C 代码而无需键入显示的示例代码。 此外可以生成许多其他位置查找的 C 代码示例程序。 若要编译有其他的源代码文件的程序，其所有上输入命令行中，如：

`cl file1.c file2.c file3.c`

编译器输出一个名为 file1.exe 程序。 若要将名称更改为 program1.exe，添加[/out](reference/out-output-file-name.md)链接器选项：

`cl file1.c file2.c file3.c /link /out:program1.exe`

若要自动捕获更多的编程错误，我们建议使用编译[/W3](reference/compiler-option-warning-level.md)或[/w4](reference/compiler-option-warning-level.md)警告等级选项：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

编译器、 cl.exe，具有更多的选项可以应用于生成、 优化、 调试和分析你的代码。 有关快速列表中，输入`cl /?`开发人员命令提示符处。 也可以编译和链接单独并应用更复杂的生成方案中的链接器选项。 编译器和链接器选项和使用情况的详细信息，请参阅[C/c + + 生成参考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和生成文件或 MSBuild 和项目文件，若要配置和命令行上生成更复杂的项目。 有关使用这些工具的详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)并[MSBuild](msbuild-visual-cpp.md)。

C 和 c + + 语言非常相似，但不是相同。 MSVC 编译器使用一个简单的规则来确定编译您的代码时要使用的语言。 默认情况下，MSVC 编译器将以.c C 源代码，结尾的所有文件和.cpp c + + 源代码为在结尾的所有文件。 若要强制编译器将所有文件都视为 C 非依赖的文件扩展名，请使用[/Tc](reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。

Visual c + + C 编译器是符合 ISO C99 标准，但不是完全符合标准。 在大多数情况下，可移植 C 代码将编译并按预期方式运行。 Visual c + + 不支持在 ISO C11 中的大多数更改。 MSVC 编译器已弃用某些库函数和 POSIX 函数名称。 支持的函数，但首选的名称已更改。 有关详细信息，请参阅[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)并[编译器警告 （等级 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>请参阅

[演练：创建标准 C++ 程序 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 语言参考](../c-language/c-language-reference.md)<br/>
[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[兼容性](../c-runtime-library/compatibility.md)
