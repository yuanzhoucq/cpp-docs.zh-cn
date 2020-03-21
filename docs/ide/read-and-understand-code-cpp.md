---
title: 阅读并理解 Visual Studio 中的 C++ 代码
description: 使用 Visual Studio 中的 C++ 代码编辑器来设置代码格式以及理解代码。
ms.date: 05/28/2019
ms.openlocfilehash: aa9008900ae631668d7a87fb413dd389696f3454
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079047"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>阅读并理解 Visual Studio 中的 C++ 代码

C++ 代码编辑器和 Visual Studio IDE 提供许多编码帮助。 有些为 C++ 所独有，有些实质上对于所有 Visual Studio 语言均相同。 有关共享功能的详细信息，请参阅[在代码和文本编辑器中编写代码](/visualstudio/ide/writing-code-in-the-code-and-text-editor)。  

## <a name="colorization"></a>着色

Visual Studio 对语法元素进行着色，以区分语言关键字、类型名称、变量名称、函数参数、字符串文本等符号类型。

![代码着色](../ide/media/code-outline-colorization.png "C++上色")

未使用的代码（例如 #if 0 下的代码）颜色更淡。

![非活动代码](../ide/media/inactive-code-cpp.png "C++非活动代码")

在“快速启动”中键入“字体”，然后选择“字体和颜色”，即可自定义颜色。 在“字体和颜色”对话框中，向下滚动到 C/C++ 选项，然后选择自定义字体和/或颜色。

## <a name="outlining"></a>大纲显示

右键单击源代码文件中的任意位置，然后选择“大纲显示”以折叠或展开代码块和/或自定义区域，以便更轻松地仅浏览你感兴趣的代码。 有关详细信息，请参阅[大纲显示](/visualstudio/ide/outlining)。

![C&#43; &#43;大纲显示](../ide/media/vs2015_cpp_outlining.png "大纲显示")

在将光标放到大括号“{”或“}”前面时，编辑器会突出显示其匹配的对应内容。

其他大纲显示选项位于主菜单中的“大纲显示” **“修改”下** > 。

## <a name="line-numbers"></a>行号

通过转到 "**工具**" > **选项**" > **文本编辑器**" > **所有语言** > "**常规**" 或通过 "**快速启动" （Ctrl + Q）** 搜索 "行号"，可以向项目添加行号。 可以为所有语言或仅针对特定语言（包括 C++）设置行号。

## <a name="scroll-and-zoom"></a>滚动和缩放

按 Ctrl 键并使用鼠标滚轮滚动，即可放大或缩小编辑器。 还可以使用左下角中的缩放设置进行缩放。

![C&#43; &#43;缩放控件](../ide/media/zoom-control.png "缩放控件")

滚动条“映射模式”使你能快速滚动和浏览整个代码文件，而无需离开当前位置。 可以单击代码图上的任意位置，以直接转至该位置。

![C 中的代码图&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "代码图")

若要打开**映射模式**，请在主工具栏的 "**快速启动**" 搜索框中键入 "Map"，然后选择 "**使用滚动图模式**"。 有关详细信息，请参阅[如何：通过自定义滚动条来跟踪代码](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar)。

“映射模式”关闭后，滚动条仍会突出显示你在文件中所做的更改。 绿色表示已保存的更改，黄色表示未保存的更改。

## <a name="quick-info-and-parameter-info"></a>快速信息和参数信息

将鼠标悬停在任何变量、函数或其他符号上，即可以获取相关信息，包括声明以及位于其前面的任何注释。

::: moniker range="vs-2019"

![C 中的快速信息&#43;&#43;](../ide/media/quick-info-vs2019.png "快速信息")

“快速信息”工具提示具有“联机搜索”链接。 转到“工具” **“选项”** “文本编辑器” > “C++” **“视图”，以指定搜索提供程序** >  >  > 。

如果代码中存在错误，可以将鼠标悬停在该代码上，“快速信息”将随即显示错误消息。 还可以在“错误列表”窗口中找到该错误消息。

![有关错误的快速信息](../ide/media/quickinfo-on-error.png "有关错误的快速信息")

::: moniker-end

::: moniker range="<=vs-2017"

![C 中的快速信息&#43;&#43;](../ide/media/quick-info.png "快速信息")

如果代码中存在错误，可以将鼠标悬停在该代码上，“快速信息”将随即显示错误消息。 还可以在“错误列表”窗口中找到该错误消息。

![有关错误的快速信息](../ide/media/quickinfo-on-error.png "有关错误的快速信息")

::: moniker-end

调用函数时，“参数信息”显示参数类型及其预期顺序。

![C 中的参数信息&#43;&#43;](../ide/media/parameter-info.png "参数信息")

## <a name="peek-definition"></a>查看定义

将鼠标悬停在变量或函数声明上，右键单击，然后选择“查看定义”，无需离开当前位置，即可查看其定义的内联视图。 有关详细信息，请参阅[查看定义 (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12)。

![C&#43; &#43;速览定义](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

##  <a name="f1-help"></a>F1 帮助

将光标置于任意类型、关键字或函数的上方或后面，然后按 F1，以便直接转到 docs.microsoft.com 上相关的参考主题。 F1 也适用于错误列表和许多对话框中的项。

## <a name="class-view"></a>类视图

“类视图”显示所有代码符号及其范围和父级/子级层次结构的可搜索树集，并且按每个项目进行整理。 可以在“类视图设置”中配置“类视图”的显示内容（单击窗口顶部的齿轮箱图标）。

![C 中的类视图&#43;&#43;](../ide/media/class-view.png "类视图")

## <a name="generate-graph-of-include-files"></a>生成包含文件的关系图

右键单击项目中的代码文件，然后选择“生成包含文件的关系图”以查看其他文件包含哪些文件的关系图。

![包含&#43; &#43;文件的 C 图形](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>查看调用层次结构

右键单击任意函数调用并查看它调用的所有函数和所有调用它的函数的递归列表。 列表中的每个函数都能以相同方式展开。 有关详细信息，请参阅[调用层次结构](/visualstudio/ide/reference/call-hierarchy)。

![C&#43; &#43;调用层次结构](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>另请参阅

[编辑和重构代码 (C++)](writing-and-refactoring-code-cpp.md)</br>
[在 Visual Studio 中导航 C++ 代码库](navigate-code-cpp.md)</br>
[使用适用于 C++ 的 Live Share 进行协作](live-share-cpp.md)
