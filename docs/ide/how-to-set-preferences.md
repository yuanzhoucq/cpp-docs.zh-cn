---
title: 在 Visual C++ Studio 中设置代码首选项
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: f1d222dc38720ea897cfbf2fb9fa0dd2727e7720
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816564"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>在 Visual C++ Studio 中设置代码首选项

你可以通过个性化C++ Visual Studio 使你的编码体验更方便、更高效，并愉悦。 你可以：

- 自定义菜单和工具栏。
- 排列窗口布局。
- 设置颜色主题。
- 指定C++格式规则，包括多个 ClangFormat 样式。
- 创建自定义键盘快捷方式。

你可以在多台计算机上同步首选项，并创建和存储多组首选项，并与团队成员共享这些首选项。 可以从 Visual Studio Marketplace 安装扩展，为自定义行为提供其他选项。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。

## <a name="arrange-window-layout"></a>排列窗口布局

在 Visual Studio 窗口中，空间划分为主菜单、工具栏、代码编辑器（或文档窗口）和工具窗口（如解决方案资源管理器和错误列表）。 某些窗口在同一位置相互重叠。 例如，解决方案资源管理器、类视图、资源视图和源代码管理器均共享同一默认位置。 通过选择框架底部的选项卡，可以在这些选项卡之间进行切换。 若要使这两个或更多窗口同时可见，只需将其中一个控件的标题栏拖到新位置即可。 你可以将其停靠在某个 Visual Studio 主窗口边框上，也可以将其浮动。

下面的屏幕截图显示将从其默认位置拖动到代码编辑器左侧新的停靠位置的**团队资源管理器**窗口。 蓝色阴影区域显示了在释放鼠标按钮时将放置窗口的位置。

![Visual Studio 团队资源管理器窗口的屏幕截图，其中突出显示了布局更改](media/window-layout-move-team-explorer.png)

在文档窗口中，每个打开的文件都包含在选项卡式框架中。 可以浮动或锁定这些选项卡，就像工具窗口一样。 有关详细信息，请参阅[在 Visual Studio 中自定义窗口布局](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要隐藏所有工具窗口并最大化 "代码编辑器" 窗口，请按**Alt** +  Shift **@no__t 以**切换*全屏模式*。

## <a name="set-c-coding-styles-and-formatting"></a>设置C++编码样式和格式设置

可以指定多个单独的代码格式设置选项，如缩进和大括号位置。 为此，请跳到 "**工具**"  >  "**选项**"  >  "**文本编辑器** > **C/C++**  > **格式**（或键入**Ctrl + Q**并搜索" 格式 "）。 或者，您可以指定一个[ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)样式（或您自己的自定义 ClangFormat 样式）。

![ClangFormat 选项的屏幕截图](media/clang-format-ide.png)

有关所有格式设置选项的详细信息，请参阅[选项、文本编辑器、CC++/和格式设置](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)。

## <a name="set-the-color-theme"></a>设置颜色主题

若要设置浅色或深色背景，请按**Ctrl + Q**并搜索 "颜色主题"。 你还可以通过转到 "**工具**"  >  "选项 @no__t 3"**环境**，并选择 "**颜色主题**" 来找到这些**选项**。

![颜色主题屏幕截图](media/tools-options-color-theme.png)

例如，下面是深色主题：

![具有深色主题的 Visual Studio 的屏幕截图](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>自定义代码着色

在 Visual Studio 2019 中，可以从三个预定义的*配色方案*中进行选择。 这些指定如何在编辑器中着色代码元素。 若要选择主题，请使用 "**工具**"  >  "**选项** > "**文本编辑器**" > **C/C++**  > **视图**，然后选择"**配色方案**：

![突出显示C++了突出显示的配色方案选项的屏幕截图](media/color-schemes.png)

在名为**Visual Studio 2017**的配色方案中，大多数代码元素只是黑色。 在**增强**的配色方案中，函数、局部变量、宏和其他元素为着色。 在 @no__t 0Enhanced （Globals 与成员） ** 方案，全局函数和变量与类成员着色。 默认模式为 "**增强**"，它如下所示：

![增强的配色方案的屏幕截图](media/color-scheme-enhanced.png)

无论哪个主题或配色方案处于活动状态，都可以为各个代码元素自定义字体和颜色。 为此，请在 "**工具**"  >  "**选项** > "**环境** >  "**字体和颜色**" 中（或键入**Ctrl + Q**并搜索 "Fonts"）。 向下滚动显示项的列表，直到看到C++选项。

![字体和C++颜色选项的屏幕截图](media/tools-options-cpp-colors.png)

此处设置的颜色将覆盖为配色方案定义的值。 如果要返回到配色方案的默认颜色，请将颜色设置回**默认值**。

## <a name="customize-the-toolbars"></a>自定义工具栏

使用工具栏，只需一次单击即可轻松发出命令，而不是使用菜单或键盘快捷方式。 Visual Studio 包含一组标准的工具栏。 对于标准C++开发，最有用的工具栏可能是标准、文本编辑器、生成、调试、源代码管理和比较文件。 对于 Windows 开发，"对话框编辑器" 和 "图像编辑器" 对于布局对话框和编辑图标很有用。

将鼠标悬停在工具栏上的图标上，以查看它代表哪个命令：

![工具栏图标的屏幕截图，并显示悬停时可用的命令信息示例](media/toolbar-mouse-hover.png)

可以通过选择向下箭头来添加或删除命令，或创建自定义工具栏。 若要将工具栏移动到新位置，请将其拖至左侧的点虚线。

![工具栏的屏幕截图，突出显示了向下箭头和虚线](media/toolbar-move-edit.png).

有关详细信息，请参阅[如何：自定义 Visual Studio @ no__t 中的菜单和工具栏。

## <a name="show-or-hide-line-numbers"></a>显示或隐藏行号

您可以指定 "行号" 是否显示在编辑器窗口的左侧。 在 "**选项**" 中的 " **C/C++** " 下，选择 "**常规**"。 在 "**设置**" 部分中，根据你的偏好选择或清除 "**行号**"。

![常规选项的屏幕截图，其中突出显示了行号](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>创建键盘快捷方式

Visual Studio 中的许多命令都具有*键盘快捷方式*、带 Ctrl、Alt 和 Shift 键的组合键。 你可以在 Visual Studio 中修改这些键盘快捷方式或创建自己的快捷方式。 中转到 "**工具**"  >  个**选项** > **环境** > **键盘**（或键入**Ctrl + Q**并搜索 "快捷方式"）。 有关详细信息，请参阅[在 Visual Studio 中标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。
