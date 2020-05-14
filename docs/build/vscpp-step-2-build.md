---
title: 生成并运行 C++ 控制台应用项目
description: 在 Visual C++ 中生成并运行 Hello World 控制台应用
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749238"
---
# <a name="build-and-run-a-c-console-app-project"></a>生成并运行 C++ 控制台应用项目

你已创建 C++ 控制台应用项目并输入了代码。 现在可以在 Visual Studio 中生成并运行它。 然后，从命令行中将其作为独立的应用运行。

## <a name="prerequisites"></a>先决条件

- 在 Visual Studio 中安装“使用 C++ 的桌面开发”工作负载并在计算机上运行。 如果尚未安装，请按照[在 Visual Studio 中安装 C++ 支持](vscpp-step-0-installation.md)中的步骤进行操作。

- 创建“Hello, World!” 项目并输入其源代码。 如果未执行此步骤，请按照[创建 C++ 控制台应用项目](vscpp-step-1-create.md)中的步骤进行操作。

如果 Visual Studio 如下所示，则可以生成并运行应用：

   ![准备好生成新项目](media/vscpp-ready-to-build.png "准备好生成新项目")

## <a name="build-and-run-your-code-in-visual-studio"></a>在 Visual Studio 中生成并运行代码

1. 若要生成项目，请从“生成”菜单选择“生成解决方案”   。 “输出”窗口将显示生成过程的结果  。

   ![生成项目](media/vscpp-build-solution.gif "生成项目")

1. 若要运行代码，请在菜单栏上选择“调试”、“开始执行(不调试)”   。

   ![启动项目](media/vscpp-start-without-debugging.gif "启动项目")

   随即将打开控制台窗口，然后运行你的应用。 在 Visual Studio 中启动控制台应用时，它会运行代码，然后输出“按任意键继续。 。 。” 让你有机会看到输出。

祝贺你！ 你在 Visual Studio 中已创建首个“Hello, world!” 控制台应用！ 按任意键关闭该控制台窗口并返回到 Visual Studio。

[我遇到了问题。](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>在命令窗口中运行代码

通常在命令提示符处（而不是在 Visual Studio 中）运行控制台应用。 在 Visual Studio 中生成应用后，便可以从任何命令窗口运行它。 下面介绍如何在命令提示窗口中查找并运行新应用。

1. 在“解决方案资源管理器”中，选择 HelloWorld 解决方案（而不是 HelloWorld 项目），然后右键单击以打开上下文菜单  。 选择“在文件资源管理器中打开文件夹”，打开 HelloWorld 解决方案文件夹中的“文件资源管理器”窗口   。

1. 在“文件资源管理器”窗口中，打开“Debug”文件夹  。 此文件夹包含应用、HelloWorld.exe 和一些其他调试文件  。 按住 Shift，然后右键单击 HelloWorld.exe，打开上下文菜单   。 选择“复制为路径”，将到应用的路径复制到剪贴板  。

1. 要打开命令提示窗口，请按 Windows+R 以打开“运行”对话框   。 在“打开”文本框中输入 cmd.exe，然后选择“确定”，运行命令提示窗口    。

1. 在命令提示窗口中，右键单击以将应用的路径粘贴到命令提示符中。 按 Enter 运行应用。

   ![在命令提示符处运行应用](media/vscpp-run-in-cmd.gif "在命令提示符处运行应用")

恭喜，你已在 Visual Studio 中生成并运行了控制台应用！

[我遇到了问题。](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>后续步骤

生成并运行此简单应用后，即可开始更复杂的项目。 有关详细信息，请参阅[使用 Visual Studio IDE 进行 C++ 桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。 此部分对在 Visual Studio 中探索 Microsoft C++ 功能提供了更详细的演练。

## <a name="troubleshooting-guide"></a>故障排除指南

此指南提供创建第一个 C++ 项目时的常见问题的解决方案。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>在 Visual Studio 中生成并运行代码：问题

如果在源代码编辑器中的任何内容下显示红色波形曲线，则生成可能包含错误或警告。 检查代码是否与拼写、标点和大小写中的示例匹配。

[返回。](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>在命令窗口中运行代码：问题

如果在“文件资源管理器”中显示的路径以 \\HelloWorld\\HelloWorld 结尾，则表示你打开的是 HelloWorld 项目，而不是 HelloWorld 解决方案    。 你会对不包含你的应用的“Debug”文件夹感到困惑。 在文件资源管理器中向上导航一个级别，以访问解决方案文件夹，这是路径中的第一个 HelloWorld  。 该文件夹还包含一个“Debug”文件夹，可在此文件夹找到你的应用。

还可导航到命令行上的解决方案“Debug”文件夹来运行你的应用。 在没有指定应用路径的情况下，应用不会从其他目录运行。 但是，你可以将应用复制到其他目录，并在那里运行它。 还可将其复制到 PATH 环境变量指定的目录，然后即可从任何位置运行它。

如果没有在快捷菜单中看到“复制为路径”，请关闭菜单，然后在再次打开它时按住 Shift   。 此命令只是为了方便起见。 还可以从“文件资源管理器”搜索栏将路径复制到文件夹，并将其粘贴到“运行”对话框中，然后在末尾输入可执行文件的名称  。 只是多一点输入，但结果相同。

[返回。](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
