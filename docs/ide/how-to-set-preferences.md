---
title: 在可视化工作室中设置C++编码首选项
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: e3a665ead7a314b343ec3320e95b189f83a38a47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365394"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>在可视化工作室中设置C++编码首选项

通过个性化 Visual Studio，您可以使C++编码体验更加方便、高效和愉快。 可以：

- 自定义菜单和工具栏。
- 排列窗口布局。
- 设置颜色主题。
- 指定C++格式设置规则，包括 ClangFormat 的几种样式。
- 创建自定义键盘快捷键。

您可以在多台计算机上同步首选项，并创建和存储多组首选项，并与团队成员共享这些首选项集。 您可以安装 Visual Studio 应用商店中的扩展，从而提供自定义行为的其他选项。 有关详细信息，请参阅[个性化可视化工作室 IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="arrange-window-layout"></a>排列窗口布局

在 Visual Studio 窗口中，空间分为主菜单、工具栏、代码编辑器（或文档窗口）和工具窗口（如解决方案资源管理器和错误列表）。 某些窗口在同一位置相互重叠。 例如，解决方案资源管理器、类视图、资源视图和源代码管理资源管理器都共享相同的默认位置。 通过选择框架底部的选项卡，您可以在它们之间切换。 要使两个或多个窗口同时可见，只需按标题栏将其中一个窗口拖动到新位置。 您可以将它停靠在 Visual Studio 主窗口边框之一上，也可以浮动它。

以下屏幕截图显示**Team Explorer**窗口从默认位置拖动到代码编辑器左侧的新停靠位置。 蓝色阴影区域显示释放鼠标按钮时窗口的位置。

![可视化工作室团队资源管理器窗口的屏幕截图，突出显示布局更改](media/window-layout-move-team-explorer.png)

在文档窗口中，每个打开的文件都包含在选项卡式框架中。 您可以浮动或锁定这些选项卡，就像工具窗口一样。 有关详细信息，请参阅[在可视化工作室中自定义窗口布局](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

要隐藏所有工具窗口并最大化代码编辑器窗口，请按**Alt** + **Shift** + **Enter**切换*全屏模式*。

## <a name="set-c-coding-styles-and-formatting"></a>设置C++编码样式和格式

您可以指定许多单独的代码格式设置选项，如缩进和大括号位置。 为此，转到**工具** > **选项** > **文本编辑器** > **C/C++** > **格式**（或键入**Ctrl + Q**并搜索"格式"）。 或者，您可以指定一种[ClangFormat 样式](https://clang.llvm.org/docs/ClangFormat.html)（或您自己的自定义 ClangFormat 样式）。

![Clang格式选项的屏幕截图](media/clang-format-ide.png)

有关所有格式选项的详细信息，请参阅[选项、文本编辑器、C/C++、格式化](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)。

## <a name="set-the-color-theme"></a>设置颜色主题

要设置浅色或深色背景，键入**Ctrl + Q**并搜索"颜色主题"。 您还可以通过进入**工具** > **选项** > **环境**来找到这些，并选择**颜色主题**。

![颜色主题的屏幕截图](media/tools-options-color-theme.png)

例如，下面是深色主题：

![带有深色主题的视觉工作室的屏幕截图](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>自定义代码着色

在 Visual Studio 2019 中，您可以从三个预定义的*配色方案中*选择 。 这些指定代码元素在编辑器中的着色方式。 要选择主题，请转到**工具** > **选项** > **文本编辑器** > **C/C++** > **视图**，然后选择 **"颜色方案**"：

![C++配色方案选项的屏幕截图，并突出显示增强](media/color-schemes.png)

在名为 Visual **Studio 2017**的配色方案中，大多数代码元素只是黑色。 在**增强**配色方案中，函数、局部变量、宏和其他元素被着色。 在**增强（全局与成员）** 方案中，全局函数和变量的颜色与类成员进行对比。 默认模式为**增强**，如下所示：

![增强配色方案的屏幕截图](media/color-scheme-enhanced.png)

无论哪个主题或配色方案处于活动状态，都可以自定义各个代码元素的字体和颜色。 为此，转到**工具** > **选项** > **环境** > **字体和颜色**（或键入**Ctrl + Q**并搜索"字体"）。 向下滚动显示项列表，直到看到C++选项。

![C++字体和颜色选项的屏幕截图](media/tools-options-cpp-colors.png)

此处设置的颜色将覆盖为配色方案定义的值。 如果要返回配色方案的默认颜色，将颜色设置回**默认**。

## <a name="customize-the-toolbars"></a>自定义工具栏

工具栏提供了一种只需单击即可发出命令的便捷方法，而不是使用菜单或键盘快捷键。 Visual Studio 包含一组标准工具栏。 对于标准C++开发，最有用的工具栏可能是标准、文本编辑器、生成、调试、源代码控制和比较文件。 对于 Windows 开发，对话框编辑器和图像编辑器可用于布局对话框和编辑图标。

将鼠标悬停在工具栏中的图标上，以查看它表示的命令：

![工具栏图标的屏幕截图，以及悬停时可用的命令信息示例](media/toolbar-mouse-hover.png)

您可以通过选择向下箭头来添加或删除命令或创建自定义工具栏。 要将工具栏移动到新位置，请将其拖动到左侧的虚线。

![工具栏的屏幕截图，下箭头和虚线突出显示](media/toolbar-move-edit.png).

有关详细信息，请参阅[如何：在 Visual Studio 中自定义菜单和工具栏](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio)。

## <a name="show-or-hide-line-numbers"></a>显示或隐藏行号

您可以指定行号是否显示在编辑器窗口的左侧。 在**选项**中，**在 C/C++** 下，选择 **"常规**"。 在 **"设置"** 部分中，根据您的偏好选择或清除**行号**。

![常规选项的屏幕截图，突出显示行号](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>创建键盘快捷键

Visual Studio 中的许多命令都有*键盘快捷键*、键组合和 Ctrl、Alt 和 Shift 键。 您可以在 Visual Studio 中修改这些键盘快捷键或创建自己的键盘快捷键。 转到**工具** > **选项** > **Environment**环境 > **键盘**（或键入**Ctrl + Q**并搜索"快捷方式"）。 有关详细信息，请参阅在[Visual Studio 中识别和自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。
