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
ms.openlocfilehash: d807fa75b32b515c2222fec9ea9d070266303e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335261"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>演练：在命令行上编译 C 程序

Visual C++ 包括一个 C 编译器，可用于创建从基本控制台程序到完整 Windows 桌面应用程序、移动应用等的所有内容。

本演练演示如何使用文本编辑器创建基本的"你好，世界"风格的 C 程序，然后在命令行上编译它。 如果您希望在命令行上C++工作，请参阅[演练：在命令行上编译本机C++程序](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果要尝试可视化工作室 IDE 而不是使用命令行，请参阅[演练：使用项目和解决方案 （C++）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或使用[可视化工作室 IDE C++桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>先决条件

要完成本演练，必须安装 Visual Studio 和可选的可视化C++组件，或安装可视化工作室的生成工具。

Visual Studio 是一个强大的集成开发环境，支持多种语言和平台的全功能编辑器、资源管理器、调试器和编译器。 有关这些功能以及如何下载和安装 Visual Studio 的信息，包括免费的视觉工作室社区版，请参阅[安装可视化工作室](/visualstudio/install/install-visual-studio)。

Visual Studio 的可视化工作室版本的"构建工具"仅安装构建 C 和C++程序所需的命令行工具集、编译器、工具和库。 它非常适合构建实验室或课堂练习，安装速度相对较快。 要仅安装命令行工具集，请从[Visual Studio 下载](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)页面下载可视化工作室的构建工具并运行安装程序。 在可视化工作室安装程序中，选择**C++生成工具**工作负载，然后选择 **"安装**"。

在命令行上构建 C 或 C++ 程序之前，必须验证工具是否已安装，以及是否可以从命令行访问这些工具。 可视化C++对命令行环境具有复杂的要求，用于查找它使用的工具、标头和库。 如果不进行一些准备 **，就不能在普通命令提示窗口中使用 Visual C++。** 您需要一个*开发人员命令提示*窗口，这是一个常规命令提示窗口，它设置了所有必需的环境变量。 幸运的是，Visual C++ 安装快捷方式，用于启动已为命令行生成设置环境的开发人员命令提示。 遗憾的是，在几乎每个版本的 Visual C++ 和不同版本的 Windows 中，开发人员命令提示快捷方式的名称及其位置都不同。 您的第一个演练任务是找到要使用的正确快捷方式。

> [!NOTE]
> 开发人员命令提示快捷方式会自动设置编译器和工具以及任何必需标头和库的正确路径。 对于每个生成配置，其中一些值是不同的。 如果不使用其中一个快捷方式，则必须自己设置这些环境值。 有关详细信息，请参阅 [为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。 由于生成环境很复杂，因此强烈建议您使用开发人员命令提示快捷方式，而不是构建自己的快捷方式。

这些说明因您使用的 Visual Studio 版本而异。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>在 Visual Studio 2019 中打开开发人员命令提示

如果在 Windows 10 上安装了 Visual Studio 2019，请打开"开始"菜单，然后向下滚动并打开**Visual Studio 2019**文件夹（不是 Visual Studio 2019 应用）。 选择**VS 2019 的开发人员命令提示符**以打开命令提示窗口。

如果您使用的是 Windows 的不同版本，请查看"开始"菜单或"开始"页，查看包含开发人员命令提示快捷方式的 Visual Studio 工具文件夹。 您还可以使用 Windows 搜索功能搜索"开发人员命令提示符"，并选择与已安装版本的 Visual Studio 相匹配的函数。 使用快捷方式打开命令提示窗口。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>在 Visual Studio 2017 中打开开发人员命令提示

如果在 Windows 10 上安装了 Visual Studio 2017，请打开"开始"菜单，然后向下滚动并打开**Visual Studio 2017**文件夹（不是 Visual Studio 2017 应用）。 选择**VS 2017 的开发人员命令提示符**以打开命令提示窗口。

如果您正在运行不同版本的 Windows，请查看"开始"菜单或"开始"页，查看包含开发人员命令提示快捷方式的 Visual Studio 工具文件夹。 您还可以使用 Windows 搜索功能搜索"开发人员命令提示符"，并选择与已安装版本的 Visual Studio 相匹配的函数。 使用快捷方式打开命令提示窗口。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>在 Visual Studio 2015 中打开开发人员命令提示

如果在 Windows 10 上安装了 Microsoft 视觉C++构建工具 2015，请打开 **"开始"** 菜单，然后向下滚动并打开 **"视觉C++生成工具"** 文件夹。 选择**可视C++ 2015 x86 本机工具命令提示符**以打开命令提示窗口。

如果您正在运行不同版本的 Windows，请查看"开始"菜单或"开始"页，查看包含开发人员命令提示快捷方式的 Visual Studio 工具文件夹。 您还可以使用 Windows 搜索功能搜索"开发人员命令提示符"，并选择与已安装版本的 Visual Studio 相匹配的函数。 使用快捷方式打开命令提示窗口。

::: moniker-end

接下来，验证可视化C++开发人员命令提示是否设置正确。 在命令提示窗口中，输入`cl`并验证输出是否如下所示：

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

当前目录或版本号可能存在差异，具体取决于 Visual C++的版本和安装的任何更新。 如果上述输出与您所看到的类似，那么您就可以在命令行生成 C 或C++程序。

> [!NOTE]
> 如果收到错误，如"'cl'未识别为内部或外部命令、可操作程序或批处理文件"，则在运行**cl**命令时出现错误 C1034 或错误 LNK1104，则表示您未使用开发人员命令提示符，或者安装 Visual C++时出现问题。 必须先解决此问题，然后才能继续。

如果找不到开发人员命令提示快捷方式，或者在输入`cl`时收到错误消息，则 Visual C++安装可能有问题。 如果您使用的是 Visual Studio 2017 或更高版本，请尝试在 Visual Studio 安装程序中重新安装**具有C++工作负载的桌面开发**。 有关详细信息，请参阅[在可视化工作室中安装C++支持](vscpp-step-0-installation.md)。 或者，从[可视化工作室下载](https://visualstudio.microsoft.com/downloads/)页面重新安装生成工具。 在此工作之前，不要继续下一节。 有关安装视觉工作室和故障排除的详细信息，请参阅[安装可视化工作室](/visualstudio/install/install-visual-studio)。

> [!NOTE]
> 根据计算机上的 Windows 版本和系统安全配置，您可能需要右键单击才能打开开发人员命令提示快捷方式的快捷方式菜单，然后选择 **"作为管理员运行"** 才能成功生成并运行通过本演练创建的程序。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>创建 C 源文件并在命令行上编译

1. 在开发人员命令提示窗口中，输入`cd c:\`以将当前工作目录更改为 C： 驱动器的根目录。 接下来，输入`md c:\simple`以创建目录，然后输入`cd c:\simple`更改为该目录。 此目录将保存您的源文件和编译的程序。

1. 在`notepad simple.c`开发人员命令提示符处输入。 在弹出的记事本警报对话框中，选择 **"是"** 以在工作目录中创建新的 simple.c 文件。

1. 在记事本中，输入以下代码行：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在记事本菜单栏上，选择 **"文件** > **保存"** 以保存工作目录中的简单.c。

1. 切换回开发人员命令提示窗口。 在`dir`命令提示符处输入以列出 c：_简单目录的内容。 您应该在目录列表中看到源文件 simple.c，如下所示：

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

   您的计算机上的日期和其他详细信息会有所不同。 如果看不到源代码文件 simple.c，请确保已更改为创建的 c：_简单目录，并在记事本中，请确保将源文件保存到此目录中。 还要确保使用 .c 文件名扩展名而不是 .txt 扩展名保存了源代码。

1. 要编译程序，`cl simple.c`请输入开发人员命令提示符。

   您可以在编译器显示的输出信息行中看到可执行程序名称 simple.exe：

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
   > 如果收到错误，如"'cl'未识别为内部或外部命令、可操作程序或批处理文件"、"错误 C1034"或错误 LNK1104，则开发人员命令提示符设置不正确。 有关如何解决此问题的信息，请访问 **"打开开发人员命令提示符"** 部分。

   > [!NOTE]
   > 如果收到其他编译器或链接器错误或警告，请查看源代码以更正任何错误，然后保存它并再次运行编译器。 有关特定错误的信息，请使用此页面顶部的搜索框查找错误编号。

1. 要运行程序，请在命令`simple`提示符处输入。

   程序将在显示以下文本后退出：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜您，您已经使用命令行编译并运行了 C 程序。

## <a name="next-steps"></a>后续步骤

这个"你好，世界"的例子就像C程序可以得到的一样简单。 现实世界的程序有头文件和更多的源文件，在库中链接，并做有用的工作。

您可以使用本演练中的步骤构建自己的 C 代码，而不是键入显示的示例代码。 您还可以构建许多 C 代码示例程序，这些程序在其他地方找到。 要编译具有其他源代码文件的程序，请在命令行中全部输入它们，例如：

`cl file1.c file2.c file3.c`

编译器输出一个称为 file1.exe 的程序。 要将名称更改为程序1.exe，添加[/out](reference/out-output-file-name.md)链接器选项：

`cl file1.c file2.c file3.c /link /out:program1.exe`

为了自动捕获更多的编程错误，我们建议您使用[/W3](reference/compiler-option-warning-level.md)或[/W4](reference/compiler-option-warning-level.md)警告级别选项进行编译：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

编译器（cl.exe）还有更多选项可用于构建、优化、调试和分析代码。 有关快速列表，`cl /?`请输入开发人员命令提示符。 您还可以单独编译和链接，并在更复杂的生成方案中应用链接器选项。 有关编译器和链接器选项和使用情况的详细信息，请参阅[C/C++建筑参考](reference/c-cpp-building-reference.md)。

您可以使用 NMAKE 和 makefile，或 MSBuild 和项目文件来配置和生成命令行上更复杂的项目。 有关使用这些工具的详细信息，请参阅[NMAKE 参考](reference/nmake-reference.md)和[MSBuild](msbuild-visual-cpp.md)。

C 和C++语言相似，但不同。 Microsoft C/C++ 编译器 （MSVC） 使用一个简单的规则来确定在编译代码时使用哪种语言。 默认情况下，MSVC 编译器将以 .c 结尾的所有文件视为 C 源代码，并将以 .cpp 结尾的所有文件视为C++源代码。 要强制编译器将所有文件视为不依赖于文件名扩展名的 C，请使用[/Tc](reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。

MSVC 符合 ISO C99 标准，但不符合严格要求。 在大多数情况下，便携式 C 代码将按预期编译和运行。 可视C++不支持 ISO C11 中的大部分更改。 MSVC 会弃用某些库函数和 POSIX 函数名。 支持函数，但首选名称已更改。 有关详细信息，请参阅 CRT 和[编译器警告 （级别 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)[中的安全功能](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="see-also"></a>另请参阅

[演练：创建标准 C++ 程序 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 语言参考](../c-language/c-language-reference.md)<br/>
[项目和构建系统](projects-and-build-systems-cpp.md)<br/>
[兼容性](../c-runtime-library/compatibility.md)
