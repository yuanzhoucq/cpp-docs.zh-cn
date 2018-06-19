---
title: 工具栏工具提示 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7024284a1be22aed211e8cf58f8366df88aa917
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383492"
---
# <a name="toolbar-tool-tips"></a>工具栏工具提示
工具提示是用途的小型弹出窗口，当你将鼠标放按钮上的一段时间内时所显示的工具栏按钮的简短说明。 当有一个工具栏由应用程序向导创建应用程序时，为你提供工具提示支持。 本文介绍了由应用程序向导和如何将工具提示支持添加到你的应用程序创建这两个工具提示支持。  
  
 本文包含以下内容：  
  
-   [激活工具提示](#_core_activating_tool_tips)  
  
-   [越过状态栏更新](#_core_fly_by_status_bar_updates)  
  
##  <a name="_core_activating_tool_tips"></a> 激活工具提示  
 若要激活你的应用程序中的工具提示，则必须执行两项操作：  
  
-   添加`CBRS_TOOLTIPS`对其他样式的样式 (如**WS_CHILD**， **WS_VISIBLE**，和其他**CBRS_** 样式) 作为传递`dwStyle`参数[CToolBar::Create](../mfc/reference/ctoolbar-class.md#create)函数或在[SetBarStyle](../mfc/reference/ccontrolbar-class.md#setbarstyle)。  
  
-   下面的过程中所述，追加换行符 (\n) 分隔到包含工具栏命令的命令行提示符的字符串资源的工具栏提示文本。 字符串资源共享工具栏按钮的 ID。  
  
#### <a name="to-add-the-tool-tip-text"></a>若要添加的工具提示文本  
  
1.  虽然你正在编辑在工具栏编辑器工具栏上的，打开**工具栏按钮属性**给定按钮的窗口。  
  
2.  在**提示**框中，指定你希望在该按钮的工具提示中显示的文本。  
  
> [!NOTE]
>  设置文本与工具栏编辑器中的按钮属性将替换以前的过程中，必须在其中打开并编辑的字符串资源。  
  
 如果具有启用的工具提示的控件条具有在其上放置的子控件，控件条将显示每个控件条上的子控件的工具提示，只要它满足以下条件：  
  
-   控件的 ID 不为-1。  
  
-   具有相同的 ID 在资源文件中的子控件的字符串表条目具有一个工具提示字符串。  
  
##  <a name="_core_fly_by_status_bar_updates"></a> 越过状态栏更新  
 与工具提示相关功能是"越过"状态栏更新。 默认情况下，状态栏上的消息描述仅特定工具栏按钮时激活该按钮。 通过包括`CBRS_FLYBY`列表中的样式传递给`CToolBar::Create`，你可以更新当鼠标光标传递到工具栏上，而无需实际激活按钮时，这些消息。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [MFC 工具栏实现 （在工具栏上的概述信息）](../mfc/mfc-toolbar-implementation.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类  
  
-   [使用工具栏控件](../mfc/working-with-the-toolbar-control.md)  
  
-   [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)

