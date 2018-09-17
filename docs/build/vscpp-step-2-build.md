---
title: 生成并运行 c + + 控制台应用程序项目 |Microsoft Docs
description: 生成并运行 Visual c + + 中的 Hello World 控制台应用
ms.custom: mvc
ms.date: 12/12/2017
ms.topic: tutorial
ms.technology:
- devlang-C++
ms.devlang: C++
dev_langs:
- C++
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05a5204234eb127da676e3b4a12ef875baecdad0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705778"
---
# <a name="build-and-run-a-c-console-app-project"></a>生成并运行 c + + 控制台应用程序项目

时创建一个 c + + 控制台应用程序项目并输入你的代码后，可以构建和运行 Visual Studio 中，，然后从命令行运行作为一款独立应用。

## <a name="prerequisites"></a>系统必备

- 使用 c + + 工作负载安装并运行您的计算机上具有 Visual Studio 中使用的桌面开发。 如果未尚未安装，请按照中的步骤[Visual Studio 中的安装 c + + 支持](../build/vscpp-step-0-installation.md)。

- 创建"Hello，World ！" 项目并输入其源代码。 如果尚未执行此操作，请按照中的步骤[创建一个 c + + 控制台应用程序项目](../build/vscpp-step-1-create.md)。

如果 Visual Studio 外观如下所示，您就可以生成并运行你的应用：

   ![准备好生成新项目](../build/media/vscpp-ready-to-build.png "准备好生成新项目")

## <a name="build-and-run-your-code-in-visual-studio"></a>生成并在 Visual Studio 中运行你的代码

1. 若要生成项目时，选择**生成解决方案**从**生成**菜单。 **输出**窗口会显示生成过程的结果。

   ![生成项目](../build/media/vscpp-build-solution.gif "生成项目")

1. 若要运行代码，在菜单栏上，选择**调试**，**启动但不调试**。

   ![启动项目](../build/media/vscpp-start-without-debugging.gif "启动项目")

    打开一个控制台窗口，然后运行您的应用程序。 当在 Visual Studio 中启动控制台应用程序时，它运行你的代码，然后打印"按任意键继续。 . ." 若要让人可以看到输出。

祝贺你！ 你已创建你的第一个"Hello，world ！" 在 Visual Studio 中的控制台应用 ！ 按某个键关闭控制台窗口并返回到 Visual Studio。

[我遇到了问题。](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>在命令窗口中运行你的代码

通常情况下，不在 Visual Studio 命令提示符处运行控制台应用。 您的应用程序构建后通过 Visual Studio，你可以从任何命令窗口中运行它。 下面介绍了如何查找并运行新的应用程序的命令提示符窗口中。

1. 在中**解决方案资源管理器**，选择是 HelloWorld 解决方案，然后右键单击以打开上下文菜单。 选择**在文件资源管理器中打开文件夹**以打开**文件资源管理器**HelloWorld 解决方案文件夹中的窗口。

1. 在中**文件资源管理器**窗口中，打开调试文件夹。 这包含您的应用程序中，HelloWorld.exe 和几个其他调试文件。 选择 HelloWorld.exe，请按住 Shift 键并右键单击以打开上下文菜单。 选择**复制为路径**将路径复制到您的应用程序到剪贴板。

1. 若要打开命令提示符窗口，按 Windows-R，打开**运行**对话框。 输入*cmd.exe*中**打开**文本框中，然后选择**确定**若要运行的命令提示符窗口。

1. 在命令提示符窗口中，右键单击要将您的应用程序的路径粘贴到命令提示符。 按 Enter 以运行你的应用。

   ![在命令提示符下运行应用程序](../build/media/vscpp-run-in-cmd.gif "在命令提示符下运行应用")

恭喜，你已生成并在 Visual Studio 中运行控制台应用 ！

[我遇到了问题。](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>后续步骤

一旦你已生成并运行此简单应用程序，您就可以为更复杂的项目。 请参阅[使用 Visual Studio IDE 进行 c + + 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)有关更多详细演练，介绍了 Visual c + + 在 Visual Studio 中的功能。

## <a name="troubleshooting-guide"></a>故障排除指南

到这里的解决方案到常见的问题时创建第一个 c + + 项目。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>生成并运行你的代码在 Visual Studio 问题

如果在源代码编辑器中的任何内容显示红色波浪线，生成可能错误或警告。 查看你的代码匹配拼写、 标点符号和用例中的示例。

[回去。](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>问题在命令窗口中运行你的代码

此外可导航到在命令行来运行你的应用的解决方案 Debug 文件夹。 不能从其他目录运行您的应用程序，而无需指定应用程序的路径。 但是，可以将您的应用程序复制到另一个目录，并从该处运行它。

如果没有看到**复制为路径**在快捷菜单中，关闭菜单，然后按住 Shift 键，重新打开它。 这只是为了方便起见。 此外可以从文件资源管理器搜索栏中，复制到的文件夹的路径，并将其粘贴到**运行**对话框中，然后输入结束时的可执行文件的名称。 它是只是一些键入操作要多，但它具有相同的结果。

[回去。](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
