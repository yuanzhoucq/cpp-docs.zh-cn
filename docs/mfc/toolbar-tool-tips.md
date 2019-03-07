---
title: 工具栏工具提示
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], activating
- CBRS_TOOLTIPS constant [MFC]
- tool tips [MFC], adding text
- updates [MFC]
- CBRS_FLYBY constant [MFC]
- tool tips [MFC]
- updating status bar messages
- updates, status bar messages
- status bars [MFC], tool tips
- flyby status bar updates
ms.assetid: d1696305-b604-4fad-9f09-638878371412
ms.openlocfilehash: 4582b03844e1be3d4cf70bcc3fff1c3b66119ae3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258354"
---
# <a name="toolbar-tool-tips"></a>工具栏工具提示

工具提示是用途的当您将鼠标指针在按钮上的一小段时间时所显示的工具栏按钮的简短说明的小弹出窗口。 有一个工具栏由应用程序向导创建应用程序时，为您提供工具提示支持。 本文介绍了由应用程序向导和如何将工具提示支持添加到你的应用程序创建这两个工具提示支持。

本文包含以下内容：

- [激活工具提示](#_core_activating_tool_tips)

- [越过状态栏更新](#_core_fly_by_status_bar_updates)

##  <a name="_core_activating_tool_tips"></a> 激活工具提示

若要激活你的应用程序中的工具提示，则必须执行两项操作：

- 将 CBRS_TOOLTIPS 样式添加到其他样式 (如 WS_CHILD、 WS_VISIBLE，和另**CBRS_** 样式) 作为传递*dwStyle*参数[CToolBar::Create](../mfc/reference/ctoolbar-class.md#create)函数中或在[SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)。

- 下面的过程中所述，附加工具提示文本，包含工具栏命令的命令行提示的字符串资源到由换行符 ('\n') 分隔。 字符串资源共享的工具栏按钮的 ID。

#### <a name="to-add-the-tool-tip-text"></a>若要添加的工具提示文本

1. 编辑在工具栏编辑器工具栏上的，打开**工具栏按钮属性**给定按钮的窗口。

1. 在中**提示**框中，指定你想要在该按钮的工具提示中显示的文本。

> [!NOTE]
>  设置文本，如工具栏编辑器中的按钮属性替换以前的过程，必须在其中打开并编辑字符串资源。

如果使用已启用的工具提示的控件条具有在其上放置的子控件，控件条将显示每个控件条上的子控件的工具提示，只要它满足以下条件：

- 控件的 ID 不为-1。

- 具有相同的资源文件中的子控件 ID 的字符串表条目具有工具提示字符串。

##  <a name="_core_fly_by_status_bar_updates"></a> 越过状态栏更新

与工具提示相关的一个功能是"越过"状态栏更新。 默认情况下，状态栏上的消息描述特定工具栏按钮时激活该按钮。 通过在传递给样式的列表中包含 CBRS_FLYBY `CToolBar::Create`，可以有鼠标光标移到工具栏上，而无需实际激活按钮时，更新这些消息。

### <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [MFC 工具栏实现 （在工具栏上的概述信息）](../mfc/mfc-toolbar-implementation.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)并[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

- [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)

- [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)
