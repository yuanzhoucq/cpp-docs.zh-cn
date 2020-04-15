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
ms.openlocfilehash: 1762931b75734801659fd6271377260bd0473614
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373461"
---
# <a name="toolbar-tool-tips"></a>工具栏工具提示

工具提示是微小的弹出窗口，当您将鼠标放在按钮上一段时间时，该窗口会简要说明工具栏按钮的用途。 当您使用具有工具栏的应用程序向导创建应用程序时，会为您提供工具提示支持。 本文介绍了应用程序向导创建的工具提示支持以及如何向应用程序添加工具提示支持。

本文介绍：

- [激活工具提示](#_core_activating_tool_tips)

- [飞天状态栏更新](#_core_fly_by_status_bar_updates)

## <a name="activating-tool-tips"></a><a name="_core_activating_tool_tips"></a>激活工具提示

要激活应用程序中的工具提示，必须执行以下两项操作：

- 将CBRS_TOOLTIPS样式添加到其他样式（如WS_CHILD、WS_VISIBLE和其他**CBRS_** 样式），作为*dwStyle*参数传递到[CToolBar：：创建](../mfc/reference/ctoolbar-class.md#create)函数或[SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)中。

- 如下所述，将工具栏提示文本（由换行符 （'\n'） 分隔到包含工具栏命令的命令行提示符的字符串资源。 字符串资源共享工具栏按钮的 ID。

#### <a name="to-add-the-tool-tip-text"></a>添加工具提示文本

1. 编辑工具栏编辑器中的工具栏时，打开给定按钮的**工具栏按钮属性**窗口。

1. 在 **"提示"** 框中，指定要显示在该按钮的工具提示中的文本。

> [!NOTE]
> 将文本设置为工具栏编辑器中的按钮属性将替换前一个过程，您必须在其中打开和编辑字符串资源。

如果启用了工具提示的控制栏上放置了子控件，则控制栏将显示控制栏上每个子控件的工具提示，只要它满足以下条件：

- 控件的 ID 不是 - 1。

- 与资源文件中的子控件具有相同 ID 的字符串表条目具有工具提示字符串。

## <a name="flyby-status-bar-updates"></a><a name="_core_fly_by_status_bar_updates"></a>飞天状态栏更新

与工具提示相关的功能是"飞天"状态栏更新。 默认情况下，状态栏上的消息仅描述激活按钮时的特定工具栏按钮。 通过在传递给`CToolBar::Create`的样式列表中包含CBRS_FLYBY，您可以在鼠标光标通过工具栏时更新这些消息，而无需实际激活按钮。

### <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [MFC 工具栏实现（工具栏概述信息）](../mfc/mfc-toolbar-implementation.md)

- [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类

- [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)

- [使用旧工具栏](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>另请参阅

[MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)
