---
title: 生成并运行 C++ 控制台应用项目
description: 在可视化C++中构建并运行 Hello World 控制台应用
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749238"
---
# <a name="build-and-run-a-c-console-app-project"></a>生成并运行 C++ 控制台应用项目

您已经创建了一个C++控制台应用项目并输入了代码。 现在，您可以在可视化工作室中构建和运行它。 然后，从命令行作为独立应用运行它。

## <a name="prerequisites"></a>先决条件

- 在 Visual Studio 中安装“使用 C++ 的桌面开发”工作负载并在计算机上运行。 如果尚未安装，请按照["安装C++视觉工作室中支持](vscpp-step-0-installation.md)的步骤操作。

- 创建一个"你好，世界！ 项目并输入其源代码。 如果尚未完成此步骤，请按照[C++控制台应用项目](vscpp-step-1-create.md)中的步骤操作。

如果 Visual Studio 如下所示，则可以构建和运行应用：

   ![准备构建新项目](media/vscpp-ready-to-build.png "准备构建新项目")

## <a name="build-and-run-your-code-in-visual-studio"></a>在可视化工作室中构建和运行代码

1. 若要生成项目，请从“生成”菜单选择“生成解决方案”********。 “输出”窗口将显示生成过程的结果****。

   ![生成项目](media/vscpp-build-solution.gif "生成项目")

1. 若要运行代码，请在菜单栏上选择“调试”、“开始执行(不调试)”********。

   ![启动项目](media/vscpp-start-without-debugging.gif "启动项目")

   随即将打开控制台窗口，然后运行你的应用。 在 Visual Studio 中启动控制台应用时，它会运行代码，然后输出“按任意键继续。 . ." 让你有机会看到输出。

祝贺你！ 你在 Visual Studio 中已创建首个“Hello, world!” 控制台应用！ 按任意键关闭该控制台窗口并返回到 Visual Studio。

[我遇到了问题。](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>在命令窗口中运行代码

通常，在命令提示符下运行控制台应用，而不是在 Visual Studio 中运行控制台应用。 应用由 Visual Studio 构建后，可以从任何命令窗口运行它。 下面了解如何在命令提示窗口中查找和运行新应用。

1. 在**解决方案资源管理器中**，选择 HelloWorld 解决方案（不是 HelloWorld 项目），然后右键单击以打开上下文菜单。 选择 **"文件资源管理器中的打开文件夹**"以在 HelloWorld 解决方案文件夹中打开**文件资源管理器**窗口。

1. 在 **"文件资源管理器"** 窗口中，打开调试文件夹。 此文件夹包含您的应用程序*HelloWorld.exe，* 以及其他几个调试文件。 按住**Shift**键并右键单击*HelloWorld.exe*以打开上下文菜单。 选择 **"复制为路径"** 以将路径复制到剪贴板。

1. 要打开命令提示窗口，请按**Windows+R**打开 **"运行"** 对话框。 在 **"打开**文本"框中输入*cmd.exe，* 然后选择 **"确定"** 以运行命令提示窗口。

1. 在命令提示窗口中，右键单击以将应用的路径粘贴到命令提示符中。 按 Enter 以运行应用。

   ![在命令提示符下运行应用](media/vscpp-run-in-cmd.gif "在命令提示符下运行应用")

恭喜您，您在 Visual Studio 中构建并运行了一个控制台应用程序！

[我遇到了问题。](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>后续步骤

构建并运行此简单应用后，即可完成更复杂的项目。 有关详细信息，请参阅[使用可视化工作室 IDE 进行C++桌面开发](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)。 它有更详细的演练，探索微软C++在视觉工作室的功能。

## <a name="troubleshooting-guide"></a>故障排除指南

创建第一个C++项目时，请在此处寻求常见问题的解决方案。

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>在可视化工作室中构建和运行代码：问题

如果源代码编辑器中的任何内容下出现红色波浪，则生成可能有错误或警告。 检查代码是否与拼写、标点符号和大小写中的示例匹配。

[回去。](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>在命令窗口中运行代码：问题

如果文件资源管理器中显示的路径在*\\HelloWorld\\HelloWorld*中结束，您已经打开了 HelloWorld*项目*，而不是 HelloWorld*解决方案*。 您将被不包含应用的 Debug 文件夹混淆。 在文件资源管理器中导航一个级别，以访问解决方案文件夹，这是路径中的第一个*HelloWorld。* 此文件夹还包含一个调试文件夹，您将在那里找到你的应用。

您还可以导航到命令行上的解决方案调试文件夹以运行应用。 如果不指定应用的路径，你的应用不会从其他目录运行。 但是，您可以将应用复制到其他目录，并从那里运行它。 还可以将其复制到 PATH 环境变量指定的目录，然后从任何位置运行它。

如果在快捷菜单中未将 **"复制"视为路径**，请关闭菜单，然后在再次打开 **"Shift"** 键时按住该键。 此命令只是为了方便起见。 还可以从文件资源管理器搜索栏将路径复制到文件夹，并将其粘贴到 **"运行"** 对话框中，然后在末尾输入可执行文件的名称。 只是打字多一点，但结果相同。

[回去。](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
