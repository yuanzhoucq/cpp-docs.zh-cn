---
title: 在 Visual C++ Studio 中设置代码首选项
ms.description: Customize C++ formatting, colors, layout, line numbers, menus and more in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: 90c9f39135b90a2c5015861a78dd8760b9a8aeed
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686946"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>在 Visual C++ Studio 中设置代码首选项

通过个性化 Visual Studio C++ ，你可以使你的编码体验更方便、更高效且更愉悦。 您可以自定义菜单和工具栏、排列窗口布局、设置颜色主题、指定C++格式设置规则（包括多种风格的 ClangFormat），以及创建自定义键盘快捷方式。 你可以在多台计算机上同步首选项，并创建和存储多组首选项，并与团队成员共享这些首选项。 你可以从提供附加自定义行为的 Visual Studio Marketplace 中安装扩展。 其中的许多选项都在[个性化 Visual STUDIO IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)下进行了介绍。

## <a name="arrange-window-layout"></a>排列窗口布局

在 Visual Studio 窗口中，空间划分为主菜单、工具栏、代码编辑器（或文档窗口）和工具窗口（**解决方案资源管理器**、**错误列表**等）。 某些窗口在同一位置相互重叠。 例如，**解决方案资源管理器**、**类视图**、**资源视图**和**源代码管理器**均共享同一默认位置。 通过单击框架底部的选项卡，可以在它们之间进行切换。 若要使这两个或更多窗口同时可见，只需将其中一个控件的标题栏拖到新位置即可。 你可以将其停靠在某个 Visual Studio 主窗口边框上，也可以将其浮动。 下图显示了从其默认位置拖动到代码编辑器左侧新停靠位置的过程中的 "**团队资源管理器**" 窗口。 蓝色阴影区域显示了在释放鼠标按钮时将放置窗口的位置。

![修改窗口布局](media/window-layout-move-team-explorer.png)

在文档窗口中，每个打开的文件都包含在选项卡式框架中。 可以浮动或锁定这些选项卡，就像工具窗口一样。 有关详细信息，请参阅[在 Visual Studio 中自定义窗口布局](/visualstudio/ide/customizing-window-layouts-in-visual-studio)。

若要隐藏所有工具窗口并最大化 "代码编辑器" 窗口，请按**Alt** +  Shift **@no__t 以**切换*全屏模式*。

## <a name="set-c-coding-styles-and-formatting"></a>设置C++编码样式和格式设置

您可以通过导航到 "**工具**"  >  "**选项**， > "**文本编辑器** > **C/C++**  > **格式**（或类型按**Ctrl + Q**并搜索 "格式设置"）。 或者，您可以指定一个[ClangFormat](https://clang.llvm.org/docs/ClangFormat.html)样式（或您自己的自定义 ClangFormat 样式）：

![ClangFormat 选项](media/clang-format-ide.png)

有关所有格式设置选项的详细信息，请参阅[选项、文本编辑器、CC++/和格式设置](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting)。

## <a name="set-the-color-theme"></a>设置颜色主题

若要设置浅色或深色背景，请按**Ctrl + Q**并搜索 "颜色主题"。 你还可以通过**工具** > **选项**通过  > **环境**，并选择**颜色主题**：

![颜色主题](media/tools-options-color-theme.png)

下图显示了深色主题：

![深色主题](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>自定义代码着色

在 Visual Studio 2019 中，可以从三个预定义的*颜色方案*中进行选择，这些方案指定如何在编辑器中着色代码元素。 若要选择主题，请导航到 "**工具**"  >  "**选项**， > "**文本编辑器**" > **C/C++**  > **视图**并选择"**配色方案**"：

![C++配色方案](media/color-schemes.png)

在**Visual Studio 2017**配色方案中，大多数代码元素只是黑色。 在**增强**的配色方案中，函数、局部变量、宏和其他元素为着色。 在 @no__t 0Enhanced （Globals 与成员） ** 方案，全局函数和变量与类成员着色。 默认模式为**增强**状态，如下所示：

![增强的配色方案](media/color-scheme-enhanced.png)

无论哪个主题或配色方案处于活动状态，都可以通过导航到 "**工具**"  > **Options** > **环境** >  个**字体和颜色**（或键入**按 Ctrl + Q**并搜索 "字体"）。 向下滚动显示项列表，直到看到以下C++选项：

![C++字体和颜色选项](media/tools-options-cpp-colors.png)

此处设置的颜色将覆盖为配色方案定义的值。 如果更改了颜色，但要为配色方案使用默认颜色，则必须将颜色设置回**默认值**。

## <a name="customize-the-toolbars"></a>自定义工具栏

使用工具栏，只需一次单击鼠标就可以轻松发出命令，而不是使用菜单或键盘快捷方式。 Visual Studio 包含一组标准的工具栏。 对于标准C++开发，最有用的工具栏可能是标准、文本编辑器、生成、调试、源代码管理和可能比较文件。 对于 Windows 开发，"对话框编辑器" 和 "图像编辑器" 对于布局对话框和编辑图标很有用。

将鼠标悬停在工具栏上的图标上，以查看它代表哪个命令：

![工具栏 QuickInfo](media/toolbar-mouse-hover.png)

单击向下箭头即可添加或删除命令或创建自定义工具栏。 若要将工具栏移动到新位置，请将其拖动到左侧的点线上：

![自定义或移动工具栏](media/toolbar-move-edit.png).

有关详细信息，请参阅[如何：自定义 Visual Studio @ no__t 中的菜单和工具栏。

## <a name="show-or-hide-line-numbers"></a>显示或隐藏行号

若要指定 "行号" 是否显示在编辑器窗口的左侧，请导航到并选中或取消选中**行号**：

![行号](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>创建键盘快捷方式

Visual Studio 中的所有命令都可以使用键盘快捷方式进行，并使用 Ctrl、Alt 和 Shift 键将各种键组合在一起。 您可以通过导航到 "**工具**"  >  "**选项** > **环境** > **键盘**（或键入**Ctrl + Q**并搜索" 快捷方式 "）来创建自己的快捷方式。 有关详细信息，请参阅[在 Visual Studio 中标识并自定义键盘快捷方式](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio)。
