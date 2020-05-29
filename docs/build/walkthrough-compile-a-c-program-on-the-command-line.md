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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335261"
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>演练：在命令行上编译 C 程序

Visual C++ 包括一个 C 编译器，可用于创建从基本的控制台程序到完整的 Windows 桌面应用程序、移动应用等的各种程序。

本演练演示如何使用文本编辑器创建“Hello, World”样式的 C 程序，然后在命令行上对其进行编译。 如果想在命令行上使用 C++，请参阅[演练：在命令行上编译本机 C++ 程序](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果想尝试使用 Visual Studio IDE 而不是使用命令行，请参阅[演练：使用项目和解决方案 (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) 或[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。

## <a name="prerequisites"></a>先决条件

若要完成本演练，你必须已安装 Visual Studio 和可选的 Visual C++ 组件，或已安装 Visual Studio 生成工具。

Visual Studio 是功能强大的集成开发环境，它支持用于多种语言和平台的功能齐全的编辑器、资源管理器、调试程序和编译器。 有关这些功能以及如何下载和安装 Visual Studio（包括免费的 Visual Studio Community 版本）的信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

Visual Studio 生成工具只安装生成 C 和 C++ 程序所需的命令行工具集、编译器、工具和库。 它非常适合生成实验室或课堂练习，安装速度也相对较快。 若要仅安装命令行工具集，请从 [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)页下载 Visual Studio 生成工具，然后运行安装程序。 在 Visual Studio 安装程序中，选择“C++ 生成工具”工作负荷，然后选择“安装”   。

必须先验证是否已安装工具以及是否可以从命令行访问它们，然后才能在命令行上生成 C 或 C++ 程序。 Visual C++ 对用于查找其使用的工具、标头和库的命令行环境有复杂的要求。 如果没有事先准备，无法在普通命令提示窗口中使用 Visual C++  。 你需要开发人员命令提示窗口，这是常规命令提示窗口，其中设置了所有必需的环境变量  。 幸运的是，Visual C++ 为你安装了快捷方式来启动开发人员命令提示，这些命令提示为命令行生成设置了环境。 遗憾的是，开发人员命令提示快捷方式的名称和它们所在的位置在几乎所有版本的 Visual C++ 和不同版本的 Windows 中都是不同的。 你的第一个演练任务是找到要使用的正确快捷方式。

> [!NOTE]
> 开发人员命令提示快捷方式自动为编译器和工具以及所有必需的标头和库设置正确的路径。 对于每个生成配置，其中一些值有所不同。 如果不使用其中一个快捷方式，则必须自己设置这些环境值。 有关详细信息，请参阅 [为命令行生成设置路径和环境变量](setting-the-path-and-environment-variables-for-command-line-builds.md)。 因为生成环境很复杂，所以我们强烈建议使用开发人员命令提示快捷方式，而不要自己生成。

根据使用的 Visual Studio 版本，操作说明会有所不同。 若要查看 Visual Studio 首选项的文档，请使用“版本”选择器控件  。 它位于此页面上目录表的顶部。

::: moniker range="vs-2019"

## <a name="open-a-developer-command-prompt-in-visual-studio-2019"></a>在 Visual Studio 2019 中打开开发人员命令提示

如果已在 Windows 10 上安装 Visual Studio 2019，请打开“开始”菜单，然后向下滚动并打开“Visual Studio 2019”文件夹（而不是 Visual Studio 2019 应用）  。 选择“VS 2019 开发人员命令提示”以打开命令提示窗口  。

如果使用其他版本的 Windows，请在“开始”菜单或“开始”页中查找包含开发人员命令提示快捷方式的 Visual Studio 工具文件夹。 还可以使用 Windows 搜索功能搜索“开发人员命令提示”，然后选择与安装的 Visual Studio 版本匹配的命令提示。 使用快捷方式打开命令提示窗口。

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-developer-command-prompt-in-visual-studio-2017"></a>在 Visual Studio 2017 中打开开发人员命令提示

如果已在 Windows 10 上安装 Visual Studio 2017，请打开“开始”菜单，然后向下滚动并打开“Visual Studio 2017”文件夹（而不是 Visual Studio 2017 应用）  。 选择“VS 2017 开发人员命令提示”以打开命令提示窗口  。

如果运行其他版本的 Windows，请在“开始”菜单或“开始”页中查找包含开发人员命令提示快捷方式的 Visual Studio 工具文件夹。 还可以使用 Windows 搜索功能搜索“开发人员命令提示”，然后选择与安装的 Visual Studio 版本匹配的命令提示。 使用快捷方式打开命令提示窗口。

::: moniker-end

::: moniker range="vs-2015"

## <a name="open-a-developer-command-prompt-in-visual-studio-2015"></a>在 Visual Studio 2015 中打开开发人员命令提示

如果已在 Windows 10 上安装 Microsoft Visual C++ 2015 生成工具，请打开“开始”菜单，然后向下滚动并打开“Visual C++ 生成工具”文件夹   。 选择“Visual C++ 2015 x86 本机工具命令提示”，打开命令提示窗口  。

如果运行其他版本的 Windows，请在“开始”菜单或“开始”页中查找包含开发人员命令提示快捷方式的 Visual Studio 工具文件夹。 还可以使用 Windows 搜索功能搜索“开发人员命令提示”，然后选择与安装的 Visual Studio 版本匹配的命令提示。 使用快捷方式打开命令提示窗口。

::: moniker-end

接下来，验证 Visual C++ 开发人员命令提示是否设置正确。 在命令提示窗口中，输入 `cl`，并验证输出是否如下所示：

```Output
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
Copyright (C) Microsoft Corporation.  All rights reserved.

usage: cl [ option... ] filename... [ /link linkoption... ]
```

当前目录或版本号可能有所不同，具体取决于 Visual C++ 的版本和所安装的任何更新。 如果上述输出与所看到的类似，则可以在命令行中生成 C 或 C++ 程序。

> [!NOTE]
> 当你运行 cl 命令时，如果遇到错误（例如“‘cl’无法识别为内部或外部命令、可操作的程序或批处理文件”、错误 C1034 或错误 LNK1104），则说明你没有使用开发人员命令提示，或者安装 Visual C++ 时出错  。 必须先解决此问题，然后才能继续。

如果找不到开发人员命令提示快捷方式，或在输入 `cl` 时收到错误消息，则说明 Visual C++ 安装可能有问题。 如果使用 Visual Studio 2017 或更高版本，请尝试重新安装 Visual Studio 安装程序中的“使用 C++ 的桌面开发”工作负荷  。 有关详细信息，请参阅[在 Visual Studio 中安装 C++ 支持](vscpp-step-0-installation.md)。 或者，从 [Visual Studio 下载](https://visualstudio.microsoft.com/downloads/)页重新安装生成工具。 在操作生效前，请不要继续进行下一部分。 有关 Visual Studio 的安装和故障排除的详细信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。

> [!NOTE]
> 根据计算机上的 Windows 版本和系统安全配置，可能必须右键单击以打开“开发人员命令提示”快捷方式的快捷菜单，然后选择“以管理员身份运行”，才能成功生成和运行通过本演练创建的程序  。

## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>创建 C 源文件并在命令行上对其进行编译

1. 在开发人员命令提示窗口中，输入 `cd c:\` 以将当前工作目录更改为 C: 驱动器的根目录。 接下来，输入 `md c:\simple` 以创建目录，然后输入 `cd c:\simple` 以更改为该目录。 此目录将保存源文件和编译的程序。

1. 在开发人员命令提示下输入 `notepad simple.c`。 在弹出的记事本警报对话框中，选择“是”以在工作目录中创建新的 simple.c 文件  。

1. 在记事本中，输入以下代码行：

    ```C
    #include <stdio.h>

    int main()
    {
        printf("Hello, World! This is a native C program compiled on the command line.\n");
        return 0;
    }
    ```

1. 在“记事本”菜单栏上，选择“文件” > “保存”以将 simple.c 保存到工作目录   。

1. 切换回开发人员命令提示窗口。 在命令提示下输入 `dir` 以列出 c:\simple 目录的内容。 目录列表中应显示源文件 simple.c，如下所示：

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

   日期和其他详细信息在你的计算机上会有所不同。 如果看不到源代码文件 simple.c，请确保已更改为所创建的 c:\simple 目录，并确保已在记事本中将源文件保存到此目录中。 另请确保以 .c 文件扩展名（而不是 .txt 扩展名）保存源代码。

1. 若要编译程序，请在开发人员命令提示下输入 `cl simple.c`。

   你可以在编译器显示的多行输出信息中看到可执行程序的名称 simple.exe：

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
   > 如果遇到错误（例如“‘cl’无法识别为内部或外部命令、可操作的程序或批处理文件”、错误 C1034 或错误 LNK1104），则说明未正确设置开发人员命令提示。 有关如何解决此问题的信息，请返回“打开开发人员命令提示”部分  。

   > [!NOTE]
   > 如果收到其他编译器或链接器错误或警告，请检查源代码以更正任何错误，然后保存它并再次运行编译器。 有关特定错误的信息，请使用此页面顶部的搜索框查找错误号。

1. 若要运行程序，请在命令提示下输入 `simple`。

   程序将在显示以下文本后退出：

    ```Output
    Hello, World! This is a native C program compiled on the command line.
    ```

   恭喜，你已通过命令行编译并运行了 C 程序。

## <a name="next-steps"></a>后续步骤

此“Hello, World”示例是最简单的 C 程序。 现实世界中的程序具有头文件和更多源文件，且库中有链接，因此可以执行有用的任务。

你可以使用本演练中的步骤生成自己的 C 代码，而不是键入所示的示例代码。 你还可以生成在其他位置看到的许多 C 代码示例程序。 若要编译包含其他源代码文件的程序，请在命令行上将它们全部输入，例如：

`cl file1.c file2.c file3.c`

编译器输出名为 file1.exe 的程序。 若要将名称更改为 program1.exe，请添加 [/out](reference/out-output-file-name.md) 链接器选项：

`cl file1.c file2.c file3.c /link /out:program1.exe`

若要自动捕获更多编程错误，我们建议使用 [/W3](reference/compiler-option-warning-level.md) 或 [/W4](reference/compiler-option-warning-level.md) 警告级别选项进行编译：

`cl /W4 file1.c file2.c file3.c /link /out:program1.exe`

编译器 cl.exe 具有更多可用于生成、优化、调试和分析代码的选项。 如需快速列表，请在开发人员命令提示下输入 `cl /?`。 你还可以单独编译和链接，并在更复杂的生成方案中应用链接器选项。 有关编译器和链接器选项及用法的详细信息，请参阅 [C/C++ 生成参考](reference/c-cpp-building-reference.md)。

可以使用 NMAKE 和生成文件或 MSBuild 和项目文件在命令行上配置和生成更复杂的项目。 有关如何使用这些工具的详细信息，请参阅 [NMAKE 参考](reference/nmake-reference.md)和 [MSBuild](msbuild-visual-cpp.md)。

C 和 C++ 语言相似，但并不相同。 Microsoft C/C++ 编译器 (MSVC) 使用简单的规则确定在编译代码时要使用的语言。 默认情况下，MSVC 编译器将以 .c 结尾的所有文件视为 C 源代码，将以 .cpp 结尾的所有文件视为 C++ 源代码。 若要强制编译器将所有文件视为与文件扩展名无关的 C，请使用 [/Tc](reference/tc-tp-tc-tp-specify-source-file-type.md) 编译器选项。

MSVC 与 ISO C99 标准兼容，但不严格相容。 在大多数情况下，可移植的 C 代码将按预期方式进行编译和运行。 Visual C++ 不支持 ISO C11 中的大部分更改。 MSVC 已弃用某些库函数和 POSIX 函数名。 这些函数仍然受支持，但首选名称已更改。 有关详细信息，请参阅 [CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)和[编译器警告（级别 3）C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。

## <a name="see-also"></a>请参阅

[演练：创建标准 C++ 程序 (C++)](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)<br/>
[C 语言参考](../c-language/c-language-reference.md)<br/>
[项目和生成系统](projects-and-build-systems-cpp.md)<br/>
[兼容性](../c-runtime-library/compatibility.md)
