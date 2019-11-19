---
title: 演练：在命令行上编译 C 程序
ms.custom: conceptual
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
ms.openlocfilehash: d91ee36d26e307577aa56560eb95bef5ed03305b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051529"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>演练：在命令行上编译 C 程序

Visual C++包含一个 C 编译器，可用于创建从基本控制台程序到完整的 Windows 桌面应用程序、移动应用等的所有内容。

本演练演示如何使用文本编辑器创建一个基本的 "Hello，World" C 程序，然后在命令行上对其进行编译。 如果要在命令行C++上操作，请参阅[演练：在命令行上编译C++本机程序](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果你想要尝试使用 visual studio ide 而不是使用命令行，请参阅[演练：使用项目和解决方案（C++）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用 Visual Studio ide 进行C++桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>Prerequisites

若要完成本演练，你必须已安装 Visual Studio 和 visual Studio 的C++可选可视组件或生成工具。

Visual Studio 是一个功能强大的集成开发环境，支持多种语言和平台的功能齐全的编辑器、资源管理器、调试器和编译器。 有关这些功能以及如何下载和安装 Visual Studio （包括免费 Visual Studio 社区版）的信息，请参阅[安装 Visual studio](/visualstudio/install/install-visual-studio)。

Visual studio 版本的 visual studio 生成工具仅安装了生成 C 和C++程序所需的命令行工具集、编译器、工具和库。 这相当于构建实验室或教室练习，安装速度相对较快。 若要仅安装命令行工具集，请从[Visual studio 下载](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)页下载用于 visual Studio 的生成工具，然后运行安装程序。 在 Visual Studio 安装程序中，选择 "  **C++生成工具**" 工作负载，然后选择 "**安装**"。

在命令行上生成 C 或C++程序之前，必须先验证是否已安装这些工具，并且是否可以从命令行访问它们。 对于C++命令行环境而言，视觉对象要求查找所使用的工具、标头和库。 **如果没有进行某些C++准备，就不能在普通的命令提示符窗口中使用视觉对象**。 需要一个 "*开发人员命令提示*" 窗口，该窗口是一个常规的命令提示符窗口，其中设置了所有必需的环境变量。 幸运的是C++ ，Visual 安装的快捷方式可让你启动开发人员命令提示，并为命令行生成设置环境。 遗憾的是，开发人员命令提示快捷方式的名称以及它们所在的位置在 Visual C++和不同版本的 Windows 上都是不同的。 你的第一个演练任务是查找要使用的正确快捷方式。

> [!NOTE]
> 开发人员命令提示快捷方式自动设置编译器和工具的正确路径，以及任何所需的标头和库。 对于每个生成配置，其中的某些值是不同的。 如果不使用其中一个快捷方式，则必须自行设置这些环境值。 有关详细信息，请参阅 [为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。 由于生成环境比较复杂，因此强烈建议使用开发人员命令提示符快捷方式，而不是构建自己的快捷方式。

这些说明根据你所使用的 Visual Studio 版本的不同而有所不同。 在继续之前，请确保已正确设置此页左上角的版本选择器。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>在 Visual Studio 2019 中打开开发人员命令提示

如果在 Windows 10 上安装了 Visual Studio 2019，请打开 "开始" 菜单，然后向下滚动并打开**Visual studio 2019**文件夹（而不是 visual studio 2019 应用）。 选择 "**用于 VS 2019 开发人员命令提示**" 打开 "命令提示符" 窗口。

如果使用的是其他版本的 Windows，请在 "开始" 菜单或 "开始" 页中查找包含 "开发人员命令提示" 快捷方式的 "Visual Studio tools" 文件夹。 你还可以使用 Windows search 函数搜索 "开发人员命令提示"，并选择与已安装的 Visual Studio 版本相匹配的工具。 使用快捷方式打开 "命令提示符" 窗口。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>在 Visual Studio 2017 中打开开发人员命令提示

如果在 Windows 10 上安装了 Visual Studio 2017，请打开 "开始" 菜单，然后向下滚动并打开**Visual studio 2017**文件夹（而不是 visual studio 2017 应用）。 选择 "**用于 VS 2017 开发人员命令提示**" 打开 "命令提示符" 窗口。

如果运行的是其他版本的 Windows，请在 "开始" 菜单或 "开始" 页中查找包含 "开发人员命令提示" 快捷方式的 "Visual Studio tools" 文件夹。 你还可以使用 Windows search 函数搜索 "开发人员命令提示"，并选择与已安装的 Visual Studio 版本相匹配的工具。 使用快捷方式打开 "命令提示符" 窗口。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>在 Visual Studio 2015 中打开开发人员命令提示

如果在 Windows 10 上安装C++了 Microsoft Visual build Tools 2015，请打开 "**开始**" 菜单，然后向下滚动并打开 "  **C++可视化生成工具**" 文件夹。 选择 **" C++ Visual 2015 x86 本机工具命令提示**打开" 命令提示符 "窗口。

如果运行的是其他版本的 Windows，请在 "开始" 菜单或 "开始" 页中查找包含 "开发人员命令提示" 快捷方式的 "Visual Studio tools" 文件夹。 你还可以使用 Windows search 函数搜索 "开发人员命令提示"，并选择与已安装的 Visual Studio 版本相匹配的工具。 使用快捷方式打开 "命令提示符" 窗口。
   
::: moniker-end


接下来，验证是否正确C++设置了 Visual developer 命令提示符。 在 "命令提示符" 窗口中，输入 `cl`，并验证输出如下所示：

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

根据视觉对象C++和安装的任何更新的版本，当前目录或版本号可能有所不同。 如果上面的输出类似于你所看到的内容，则可以在命令行上生成C++ C 或程序。

> [!NOTE]
> 如果收到错误，如 "' cl ' 无法识别为内部或外部命令、可操作程序或批处理文件"、"错误 C1034" 或 "错误 LNK1104" （运行**cl**命令时），则可能是未使用开发人员命令提示，或视觉C++对象安装有问题。 必须先解决此问题，然后才能继续。

如果你找不到 "开发人员命令提示" 快捷方式，或者当你输入 `cl`时收到错误消息，则C++你的视觉对象安装可能有问题。 如果使用的是 visual studio 2017 或更高版本，请尝试**使用C++**  visual studio 安装程序中的工作负荷重新安装桌面开发。 有关详细信息，请参阅[在 Visual Studio 中C++安装支持](vscpp-step-0-installation.md)。 或者，从[Visual Studio 下载](https://visualstudio.microsoft.com/downloads/)页重新安装生成工具。 请不要继续执行下一节，直到这样做。 有关安装 Visual Studio 和排查其问题的详细信息，请参阅[安装 Visual studio](/visualstudio/install/install-visual-studio)。

> [!NOTE]
> 根据计算机上的 Windows 版本和系统安全配置，您可能必须右键单击以打开 "开发人员命令提示" 快捷方式的快捷菜单，然后选择 "以**管理员身份运行**"，以成功生成并运行您按照本演练创建的程序。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>创建 C 源文件，并在命令行上对其进行编译

1. 在 "开发人员命令提示" 窗口中，输入 `cd c:\` 将当前工作目录更改为 C：驱动器的根目录。 接下来，输入 `md c:\simple` 以创建目录，然后输入 `cd c:\simple` 更改为该目录。 此目录将包含源文件和编译程序。

1. 在开发人员命令提示符下输入 `notepad simple.c`。 在弹出的 "记事本警报" 对话框中，选择 **"是"** 以在工作目录中创建新的简单 .c 文件。

1. 在记事本中，输入以下代码行：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在 "记事本" 菜单栏上，选择 " > **文件**" "**保存**"，将 simple 保存在工作目录中。

1. 切换回 "开发人员命令提示" 窗口。 在命令提示符下输入 `dir` 以列出 c:\simple 目录的内容。 目录列表中应会显示源文件 simple，如下所示：

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

   在您的计算机上，日期和其他详细信息会有所不同。 如果看不到源代码文件，请确保已更改为所创建的 c:\simple 目录，并在记事本中确保已将源文件保存在此目录中。 此外，请确保保存的源代码文件扩展名为 .c，而不是 .txt 扩展名。

1. 若要编译程序，请在开发人员命令提示符下输入 `cl simple.c`。

   可以在编译器显示的输出信息行中查看可执行程序名称 "simple"：

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
   > 如果收到错误，如 "' cl ' 无法识别为内部或外部命令、可运行程序或批处理文件"、"错误 C1034" 或 "错误 LNK1104"，则不会正确设置开发人员命令提示。 有关如何解决此问题的信息，请返回到 "**打开开发人员命令提示**" 部分。

   > [!NOTE]
   > 如果收到不同的编译器或链接器错误或警告，请查看源代码以更正任何错误，然后保存并再次运行编译器。 有关特定错误的信息，请使用此页顶部的 "搜索" 框来查找错误号。

1. 若要运行程序，请在命令提示符下输入 `simple`。

   程序将在显示以下文本后退出：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜，你已使用命令行编译并运行 C 程序。

## <a name="next-steps"></a>后续步骤

此 "Hello，World" 示例与 C 程序一样简单。 实际程序具有标头文件和更多源文件，在库中链接，并执行有用的工作。

您可以使用本演练中的步骤来生成自己的 C 代码，而不是键入所示的示例代码。 你还可以生成多个在其他位置找到的 C 代码示例程序。 若要编译具有其他源代码文件的程序，请在命令行上输入它们，如下所示：

`cl file1.c file2.c file3.c`

编译器输出名为 file1 的程序。 若要将名称更改为 program1，请添加[/out](reference/out-output-file-name.md)链接器选项：

`cl file1.c file2.c file3.c /link /out:program1.exe`

为了自动捕获更多的编程错误，我们建议使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告等级选项进行编译：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

编译器（node.js）有更多选项可用于生成、优化、调试和分析代码。 对于 "快速列表"，请在开发人员命令提示符下输入 `cl /?`。 你还可以单独编译和链接，并在更复杂的生成方案中应用链接器选项。 有关编译器和链接器选项和用法的详细信息，请参阅[C/C++生成引用](reference/c-cpp-building-reference.md)。

可以在命令行中使用 NMAKE 和生成文件、MSBuild 和项目文件来配置和生成更复杂的项目。 有关使用这些工具的详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)和[MSBuild](msbuild-visual-cpp.md)。

C 和语言C++类似，但并不相同。 Microsoft C/C++编译器（MSVC）使用简单的规则来确定在编译代码时要使用的语言。 默认情况下，MSVC 编译器会将以 .c 结尾的所有文件视为 C 源代码，并将以 .cpp 结尾的所有文件视为C++源代码。 若要强制编译器将所有文件视为非依赖于文件扩展名的 C，请使用[/tc](reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。

MSVC 兼容 ISO C99 标准，但不严格相容。 在大多数情况下，可移植的 C 代码将按预期方式进行编译和运行。 视觉C++对象不支持 ISO C11 中的大多数更改。 某些库函数和 POSIX 函数名称被 MSVC 弃用。 支持函数，但首选名称已更改。 有关详细信息，请参阅[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)和[编译器警告（等级3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>请参阅

[演练：创建标准 C++ 程序 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C# 语言参考](../c-language/c-language-reference.md)<br/>
[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[兼容性](../c-runtime-library/compatibility.md)
