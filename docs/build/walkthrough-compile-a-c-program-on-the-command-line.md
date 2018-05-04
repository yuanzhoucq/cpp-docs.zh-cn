---
title: 演练： 编译 C 程序命令行上的 |Microsoft 文档
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
helpviewer_keywords:
- command-line applications [C++], C programs
- Visual C, compiling
- compiling programs [C++]
- C program compiling [C++]
ms.assetid: 7e74cc2d-54b1-49de-b7ad-d3ae6b39ab8d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 033c29ff9871a427222b59fbf5c8350794a9bbe2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-compile-a-c-program-on-the-command-line"></a>演练： 编译 C 程序命令行上
Visual c + + 包括一个 C 编译器，可用来创建从基本的控制台程序到完整的 Windows 桌面应用程序、 移动应用和的详细信息。  
  
 本演练演示如何创建一个基本的"Hello，World"-通过使用文本编辑器中，样式 C 程序，然后在命令行上对其进行编译。 如果你想使用 c + + 中命令行上，请参阅[演练： 编译本机 c + + 程序命令行上](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)。 如果你想要尝试 Visual Studio IDE 而不是使用命令行，请参阅[演练： 使用项目和解决方案 （c + +）](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)或[使用适用于 c + + 桌面开发的 Visual Studio IDE](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。  
  
## <a name="prerequisites"></a>系统必备  
 若要完成本演练，必须安装 Visual Studio 和可选的 Visual c + + 组件中，或 Microsoft Visual c + + 生成工具。  
  
 Visual Studio 是一个功能强大的集成的开发环境，对于许多语言和平台支持齐全编辑器、 资源管理器、 调试器和编译器。 有关这些功能以及如何下载和安装 Visual Studio 中，包括免费 Visual Studio Community 版中，请参阅[VisualStudio.com](https://www.visualstudio.com/)。  
  
 Visual Studio 生成工具安装命令行编译器、 工具和生成 C 和 c + + 程序所需的库。 它非常适用于生成实验室或教室练习，并且安装相对快一点。 若要只安装命令行工具，下载[Visual Studio 生成工具](https://go.microsoft.com/fwlink/p/?linkid=840931)和运行安装程序。 有关详细信息，请参阅[Visual c + + 生成工具](http://landinghub.visualstudio.com/visual-cpp-build-tools)。  
  
 你可以在命令行上生成 C 或 c + + 程序之前，必须验证，安装工具，并且，你可以从命令行访问它们。 Visual c + + 查找工具、 标头和使用的库具有复杂的命令行环境要求。 **不能使用 Visual c + + 中的普通命令提示符窗口**。 你需要*开发人员命令提示*窗口中，这是已设置的所有必需的环境变量的正则命令提示符窗口。 幸运的是，Visual c + + 安装可启动具有设置为命令行生成环境的开发人员命令提示快捷的方式。 遗憾的是，开发人员命令提示符快捷方式和他们的位置的名称是几乎每个版本的 Visual c + + 和在不同版本的 Windows 中不同。 你的第一个演练任务是查找要使用的正确快捷方式。  
  
> [!NOTE]
>  开发人员命令提示符快捷方式会自动设置编译器和工具，以及任何必需的标头和库的正确路径。 其中某些值是不同的每个生成配置。 你必须设置这些环境值自己如果不使用快捷方式之一。 有关详细信息，请参阅[为命令行生成设置路径和环境变量](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。 生成环境很复杂，因为我们强烈建议你使用而不是生成你自己的开发人员命令提示符快捷方式。  
  
## <a name="open-a-developer-command-prompt"></a>打开开发人员命令提示  
  
1.  如果你已在 Windows 10 上安装 Visual Studio 2017，打开开始菜单，然后向下滚动并打开**Visual Studio 2017**文件夹 （不是 Visual Studio 2017 应用程序）。 选择**VS 2017 的开发人员命令提示符**打开命令提示符窗口。  
  
     如果你在 Windows 10 上安装 Microsoft Visual c + + 生成工具 2015年，打开**启动**菜单，然后向下的滚动并打开**Visual c + + 生成工具**文件夹。 选择**Visual c + + 2015 x86 本机工具命令提示**打开命令提示符窗口。  
  
     如果你正在使用不同版本的 Visual Studio 或运行不同版本的 Windows，在开始菜单中查找或启动包含开发人员命令提示符快捷方式的 Visual Studio 工具文件夹的页。 你可以使用 Windows search 函数要搜索的"开发人员命令提示符"，然后选择一个与你安装 Visual Studio 的版本。 使用快捷方式打开命令提示符窗口。  
  
2.  接下来，验证正确设置 Visual c + + 开发人员命令提示。 在命令提示符窗口中，输入`cl`并验证输出看起来类似如下内容：  
  
    ```Output  
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl  
    Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86  
    Copyright (C) Microsoft Corporation.  All rights reserved.  
    
    usage: cl [ option... ] filename... [ /link linkoption... ]  
    
    C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>  
    ```  
  
     可能在当前目录或版本号，具体取决于 Visual c + + 和安装任何更新的版本存在差异。 如果这是类似于你所看到的内容，然后你就可以生成在命令行 C 或 c + + 程序。  
  
    > [!NOTE]
    >  如果你收到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件"错误 C1034 或错误 LNK1104 运行时**cl**命令时，则或者你不使用开发人员命令提示，或有问题与你安装的 Visual c + +。 你必须修复此问题，然后才能继续。  
  
     如果找不到开发人员命令提示符快捷方式，或当你输入时收到错误消息`cl`，则你的 Visual c + + 安装可能会产生问题。 请尝试重新安装 Visual c + + 组件在 Visual Studio 中，或重新安装 Visual Studio 生成工具。 不继续到下一节之前之所以能够正常。 有关安装和 Visual c + + 疑难解答的详细信息，请参阅[安装 Visual Studio](/visualstudio/install/install-visual-studio)。  
  
    > [!NOTE]
    >  具体取决于计算机和系统安全配置上的 Windows 版本，你可能需要右键单击以打开开发人员命令提示符快捷方式的快捷菜单，然后选择**以管理员身份运行**到已成功生成并运行通过完成本演练创建的程序。  
  
## <a name="create-a-c-source-file-and-compile-it-on-the-command-line"></a>创建 C 源文件并在命令行上对其进行编译  
  
1.  在开发人员命令提示符窗口中，输入**cd c:\\** 若要将当前工作目录更改为 c： 驱动器的根目录。 接下来，输入**md c:\simple**以创建一个目录，然后输入**cd c:\simple**更改为该目录。 这是将包含您的源文件和已编译的程序的目录。  
  
2.  输入**记事本 simple.c**开发人员命令提示符处。 在记事本警报对话框弹出，选择**是**在你的工作目录中创建新的 simple.c 文件。  
  
3.  在记事本中，输入以下代码行：  
  
    ```C  
    #include <stdio.h>  
  
    int main()  
    {  
        printf("Hello, World! This is a native C program compiled on the command line.\n");  
        return 0;  
    }   
    ```  
  
4.  在记事本菜单栏上，选择**文件**，**保存**将 simple.c 保存在你的工作目录。  
  
5.  切换回开发人员命令提示符窗口。 输入**dir**在命令提示符下，若要列出 c:\simple 目录的内容。 你应看到源文件 simple.c 在目录列表中，如下所示：  
  
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
  
     在你的计算机上，日期和其他详细信息也将有所不同。 如果看不到源代码文件中，simple.c，请确保你已更改为 c:\simple 创建的目录，并在记事本中，请确保你在此目录中保存源文件。 此外请确保以.c 文件名称扩展名，不.txt 扩展名保存的源代码。  
  
6.  若要编译你的程序，请输入**cl simple.c**开发人员命令提示符处。  
  
     你可以看到可执行程序的名称，simple.exe，在编译器显示的输出信息的行：  
  
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
    >  如果你收到错误，如"'cl' 无法识别为内部或外部命令、 可操作程序或批处理文件"错误 C1034 或错误 LNK1104，你的开发人员命令提示未正确设置。 有关如何解决此问题的信息，请返回到**打开开发人员命令提示**部分。  
  
    > [!NOTE]
    >  如果您收到不同的编译器或链接器错误或警告，查看你的源代码以更正任何错误，然后将其保存并再次运行编译器。 有关特定错误的信息，使用搜索框此 MSDN 页面上查找错误号。  
  
7.  若要运行程序，请输入**简单**在命令提示符。  
  
     程序将在显示以下文本后退出：  
  
    ```Output  
    Hello, World! This is a native C program compiled on the command line.  
    ```  
  
     祝贺你，只是已编译，而使用命令行运行 C 程序中。  
  
## <a name="next-steps"></a>后续步骤  
 此"Hello，World"示例是关于一样简单，如 C 程序可以获取。 现实世界程序具有标头文件和多个源文件，在库中，链接和执行有用的工作。  
  
 可以使用此演练中的步骤来生成你自己的 C 代码而非键入显示的示例代码。 你也可以生成许多其他位置查找的 C 代码示例程序。 若要编译有多个源代码文件的程序，输入在命令行，如下：  
  
 `cl file1.c file2.c file3.c`  
  
 编译器将输出一个名为 file1.exe 程序。 若要将名称更改为 program1.exe，添加[/out](../build/reference/out-output-file-name.md)链接器选项：  
  
 `cl file1.c file2.c file3.c /link /out:program1.exe`  
  
 若要自动捕获更多的编程错误，我们建议你通过使用编译和[/W3](../build/reference/compiler-option-warning-level.md)或[/W4](../build/reference/compiler-option-warning-level.md)警告等级选项：  
  
 `cl /W4 file1.c file2.c file3.c /link /out:program1.exe`  
  
 编译器，cl.exe，具有更多的选项可以将应用于生成、 优化、 调试和分析你的代码。 有关快速列表中，输入**cl /？** 在开发人员命令提示符。 你还可以编译和链接单独并应用更复杂的生成方案中的链接器选项。 编译器和链接器选项以及使用情况的详细信息，请参阅[C/c + + 生成参考](../build/reference/c-cpp-building-reference.md)。  
  
 可以使用 NMAKE 和生成文件或 MSBuild 和项目文件来配置和命令行上生成更复杂的项目。 有关使用这些工具的详细信息，请参阅[NMAKE 参考](../build/nmake-reference.md)和[MSBuild](../build/msbuild-visual-cpp.md)。  
  
 C 和 c + + 语言与此类似，但不是相同。 Visual c + + 编译器使用简单规则来确定它编译你的代码时要使用的语言。 默认情况下，Visual C++ 编译器将以 .c 结尾的所有文件视为 C 源代码，将以 .cpp 结尾的所有文件视为 C++ 源代码。 若要强制编译器将所有文件视为 C，而不管文件扩展名如何，使用[/Tc](../build/reference/tc-tp-tc-tp-specify-source-file-type.md)编译器选项。  
  
 Visual c + + C 编译器将通常符合 ISO C99 标准中，但不是严格符合。 在大多数情况下，可移植的 C 代码将编译并按预期方式运行。 Visual c + + 不支持在 ISO C11 中的大多数更改。 由 Visual c + + 编译器已弃用某些库函数和 POSIX 函数名称。 支持的函数，但首选的名称已更改。 有关详细信息，请参阅[CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)和[编译器警告 （等级 3） C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。  
  
## <a name="see-also"></a>请参阅  
 [演练： 创建标准 c + + 程序 （c + +）](../windows/walkthrough-creating-a-standard-cpp-program-cpp.md)   
 [C 语言参考](../c-language/c-language-reference.md)   
 [生成 C/C++ 程序](../build/building-c-cpp-programs.md)   
 [兼容性](../c-runtime-library/compatibility.md)