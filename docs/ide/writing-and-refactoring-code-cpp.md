---
title: 编写和重构代码 （c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/27/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 56ffb9e9-514f-41f4-a3cf-fd9ce2daf3b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02a028ddf5cbd4ac33f1ff9b148e7f20e5114c69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="writing-and-refactoring-code-c"></a>编写和重构代码 (C++)

Visual C++ 代码编辑器和 IDE 提供许多编码帮助。 有些为 C++ 所独有，有些实质上对于所有 Visual Studio 语言均相同。 有关共享的功能的详细信息，请参阅[在代码和文本编辑器中编写代码](/visualstudio/ide/writing-code-in-the-code-and-text-editor)。 启用和配置特定于 c + + 的功能的选项位于[文本编辑器 c + + 高级](/visualstudio/ide/reference/options-text-editor-c-cpp-advanced)对话框 (**工具&#124;选项&#124;文本编辑器&#124;C/c + +&#124;高级**或键入"c + + Advanced"**快速启动**)。 选择你想要设置的选项之后, 中，你可以获取更多帮助通过按**F1**对话框时焦点。 如需通用代码格式设置选项，键入`Editor C++`到**快速启动**。

实验性功能，可能是也可能不包括 Visual Studio 的未来版本中，位于[文本编辑器 c + + 实验](/visualstudio/ide/reference/options-text-editor-c-cpp-experimental)对话框。 在 Visual Studio 2017 年 1 可以启用**预测 Intellisense**在此对话框。

## <a name="adding-new-code"></a>添加新代码

创建项目之后，可以开始在为你生成的文件中进行编码。 若要添加新文件，右键单击解决方案资源管理器中的项目节点并选择**添加&#124;新建**。

若要设置格式设置缩进、 括号补全和着色等选项，键入`C++ Formatting`到**快速启动**窗口。

### <a name="intellisense"></a>IntelliSense

IntelliSense 是一组提供有关成员、类型和函数重载的内联信息的功能的名称。 下图显示在你键入时出现的成员下拉列表。 可以按 tab 键将选定的项文本键入代码文件中。

![C&#43; &#43;成员下拉列表](../ide/media/vs2015_cpp_statement_completion.png "vs2015_cpp_statement_completion")

有关完整信息请参阅[Visual c + + Intellisense](/visualstudio/ide/visual-cpp-intellisense)。

### <a name="insert-snippets"></a>插入代码片段

代码片段是一段预定义的源代码。 在单个点上或在选定文本上右键单击以插入代码片段或用代码片段环绕选定文本。 下图显示用 for 循环环绕选定语句的三个步骤。 最终图像中的黄色突出显示是使用 tab 键访问的可编辑字段。 有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。

![Visual C&#43; &#43;插入代码段放&#45;下](../ide/media/vs2015_cpp_surround_with.png "vs2015_cpp_surround_with")

### <a name="add-class"></a>添加类

添加新类从**项目**通过使用类向导的菜单。

![在 Visual C 中添加新类&#43;&#43;](../ide/media/vs2015_cpp_add_class.png "vs2015_cpp_add_class")

### <a name="class-wizard"></a>类向导

使用类向导修改或检查现有类，或添加新类。 有关详细信息，请参阅[添加功能使用代码向导 （c + +）](../ide/adding-functionality-with-code-wizards-cpp.md)。

![Visual C&#43; &#43;类向导](../ide/media/vs2015_cpp_class_wizard.png "vs2015_cpp_class_wizard")

## <a name="refactoring"></a>重构

重构是可在快速操作上下文菜单或通过单击[灯泡](/visualstudio/ide/perform-quick-actions-with-light-bulbs)在编辑器中。  在中也发现一些**编辑 > 重构**菜单。  这些功能包括：

* [重命名](refactoring/rename.md)
* [提取函数](refactoring/extract-function.md)
* [实现纯虚方法](refactoring/implement-pure-virtuals.md)
* [创建声明/定义](refactoring/create-declaration-definition.md)
* [移动函数定义](refactoring/move-definition-location.md)
* [转换为原始字符串文本](refactoring/convert-to-raw-string-literal.md)
* [更改签名](refactoring/change-signature.md)

## <a name="navigate-and-understand"></a>导航和了解

与其他语言，visual c + + 共享许多代码导航功能。 有关详细信息，请参阅[导航代码](/visualstudio/ide/navigating-code)和[查看代码结构](/visualstudio/ide/viewing-the-structure-of-code)。

### <a name="quickinfo"></a>QuickInfo

将鼠标悬停在变量上以查看其类型信息。

![Visual C++ 快速信息](../ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")

### <a name="open-document-navigate-to-header"></a>打开文档（导航至标头）

右键单击 `#include` 指令中的标头名称，然后打开头文件。

![Visual C&#43; &#43;打开文档菜单选项](../ide/media/vs2015_cpp_open_document.png "vs2015_cpp_open_document")

### <a name="peek-definition"></a>查看定义

将鼠标悬停在变量或函数声明上，右键单击，然后选择**查看定义**若要查看其定义的内联视图。 有关详细信息，请参阅[查看定义 (Alt + F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12)。

![Visual C&#43; &#43;查看定义](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

### <a name="go-to-definition"></a>转到定义

将鼠标悬停在变量或函数声明上，右键单击，然后选择**转到定义**打开定义对象的文档。

### <a name="view-call-hierarchy"></a>查看调用层次结构

右键单击任意函数调用并查看它调用的所有函数和所有调用它的函数的递归列表。 列表中的每个函数都能以相同方式展开。 有关详细信息，请参阅[调用层次结构](/visualstudio/ide/reference/call-hierarchy)。

![Visual C&#43; &#43;调用层次结构](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

### <a name="toggle-header--code-file"></a>切换标题/代码文件

右键单击并选择**切换标头 / 代码文件**标头文件和其关联的代码文件之间来回切换。

### <a name="outlining"></a>大纲显示

右键单击源代码文件中的任意位置，然后选择**大纲**以折叠或展开定义和/或自定义区域，以便更加轻松地仅浏览的部分你感兴趣。 有关详细信息，请参阅[大纲显示](/visualstudio/ide/outlining)。

![Visual C&#43; &#43;大纲显示](../ide/media/vs2015_cpp_outlining.png "vs2015_cpp_outlining")

### <a name="scroll-bar-map-mode"></a>滚动条映射模式

滚动条映射模式使你能快速滚动和浏览整个代码文件，而无需实际离开当前位置。 或者单击代码图上的任意位置，以直接转至该位置。

![代码图中 Visual C&#43;&#43;](../ide/media/vs2015_cpp_code_map.png "vs2015_cpp_code_map")

### <a name="generate-graph-of-include-files"></a>生成包含文件的关系图

右键单击你的项目中的代码文件，然后选择**生成的包含文件关系图**以查看文件被其他文件包含的其中一个图表。

![Visual C&#43; &#43;包含文件关系图](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

### <a name="f1-help"></a>F1 帮助

将光标置于任意类型、关键字或函数的上方或后面，然后按 F1，以便直接转到相关的 MSDN 参考主题。 F1 也适用于错误列表和许多对话框中的项。

### <a name="quick-launch"></a>快速启动

若要轻松地导航至 Visual Studio 中的任意窗口或工具，只需在 UI 右上角的“快速启动”窗口中键入其名称即可。 “自动完成”列表将在你键入时进行筛选。

![Visual Studio 快速启动](../ide/media/vs2015_cpp_quick_launch.png "vs2015_cpp_quick_launch")
