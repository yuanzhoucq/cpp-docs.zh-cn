---
title: AFX 消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
dev_langs:
- C++
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cc11b3eb79f0d535775f073c772e40c4ed9e822c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355405"
---
# <a name="afx-messages"></a>AFX 消息
在 MFC 中使用这些消息。  
  
## <a name="messages"></a>消息  
 下表列出了在 MFC 库中使用的消息：  
  
||||||  
|-|-|-|-|-|  
|消息|描述|[in] `wParam`|`lParam` （所有参数都都 [in] 除非另行说明。）|返回值|  
|AFX_WM_ACCGETOBJECT|未使用。|未使用。|不适用。|不适用。|  
|AFX_WM_ACCGETSTATE|用于可访问性支持。 发送到此消息`CMFCPopupMenu`或`CMFCRibbonPanelMenu`检索的当前元素的状态。|元素，可以为一个菜单按钮或分隔符的索引。|未使用。|元素状态中。 如果该索引无效，则为-1 0 菜单按钮是否没有特殊特性。 否则，它是以下标志的组合：<br /><br /> TBBS_DISABLED — 项被禁用<br /><br /> TBBS_CHECKED-选中项<br /><br /> TBBS_BUTTON-表明它是标准按键<br /><br /> TBBS_PRESSED-按下按钮<br /><br /> TBBS_INDETERMINATE-未定义的状态<br /><br /> TBBS_SEPARATOR-而不是菜单按钮，此元素窗体的其他菜单项之间的分离|  
|AFX_WM_CHANGE_ACTIVE_TAB|框架将此消息发送到可调整大小控件栏控件。 处理此消息以接收来自通知`CMFCTabCtrl`对象时用户更改活动选项卡。|选项卡的索引。|未使用。|非零。|  
|AFX_WM_CHANGE_CURRENT_FOLDER|框架将此邮件发送到的父级`CMFCShellListCtrl`时用户已更改的当前文件夹。|未使用。|未使用。|未使用。|  
|AFX_WM_CHANGEVISUALMANAGER|在用户更改当前可视化管理器时，框架会将此消息发送到所有框架窗口。 响应此消息，框架窗口重新计算其区域，并根据需要调整其他参数。 如果你需要有关此事件通知，您可以在你的应用程序中处理 AFX_WM_CHANGEVISUALMANAGER 消息。 必须调用基类处理程序 (`OnChangeVisualManager`) 以确保框架的内部处理此事件发生。|未使用。|未使用。|未使用。|  
|AFX_WM_CHANGING_ACTIVE_TAB|发送到的父级`CMFCTabCtrl`对象。  处理此消息，如果你想要接收来自通知`CMFCTabCtrl`对象时用户重置选项卡。|正在激活选项卡的索引。|未使用。|非零。|  
|AFX_WM_CHECKEMPTYMINIFRAME|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX_WM_CREATETOOLBAR|从发送`CMFCToolBarsListPropertyPage`时用户可以在自定义过程创建一个新的工具栏。 你可以处理此消息实例化自定义的 CMFCToolBar 派生对象。 如果你处理此消息，并且创建您自己的工具栏，省略默认处理程序调用。|未使用。|指向包含的工具栏的名称的字符串的指针。|指向新创建的工具栏的指针。 NULL 指示工具栏创建已取消。|  
|AFX_WM_CUSTOMIZEHELP|从自定义属性表发送到主框架窗口`CMFCToolbarCustomize Dialog`当用户按**帮助**按钮或按 F1 键。|指定的活动页面的自定义属性表。|指向的指针`CMFCToolbarCustomize Dialog`对象。|为零。|  
|AFX_WM_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize Dialog`发送此消息，以通知父框架，用户为其创建一个新的工具栏。|`TRUE` 当启动自定义项时，`FALSE`完成自定义项。|未使用。|为零。|  
|AFX_WM_DELETETOOLBAR|当用户是将要删除自定义模式中的工具栏时，发送到主框架窗口。<br /><br /> 处理此消息以执行额外的操作，当用户中删除自定义模式中的工具栏。 你还应调用默认处理程序 (`OnToolbarDelete`)，并删除工具栏。 默认处理程序返回一个值，该值指示是否可以删除工具栏。|未使用。|指向`CMFCToolBar`要删除的对象。|如果无法删除一个工具栏，则不为否则为 0。|  
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` 将此消息发送到要检索的文档颜色的主框架窗口。|未使用。|[在中，out]指向`CList<COLORREF, COLORREF>`对象。|为零。|  
|AFX_WM_GETDRAGBOUNDS|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|用户突出显示功能区列表项时，发送到主框架窗口。|突出显示的项的索引|指向的指针 `CMFCBaseRibbonElement`|未使用。|  
|AFX_WM_ON_AFTER_SHELL_COMMAND|发送到的父级`CMFCShellListCtrl`或`CMFCShellTreeCtrl`控制用户完成执行 shell 命令。|用户执行的命令 ID|未使用。|如果应用程序将处理此消息，则应返回零。|  
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|显示弹出菜单之前，框架会将此邮件发送到功能区的父级。 可以处理此消息，还可以随时修改弹出菜单。|未使用。|指向的指针 `CMFCBaseRibbonElement`|未使用。|  
|AFX_WM_ON_CANCELTABMOVE|仅限内部使用。|不适用。|不适用。||  
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|在用户更改活动的功能区控件类别时，框架会将此消息发送到主框架。|未使用。|指向的指针`CMFCRibbonBar`其类别发生了更改。|未使用。|  
|AFX_WM_ON_CLOSEPOPUPWINDOW|框架发送此消息，以通知的所有者`CMFCDesktopAlertWnd`窗口是即将关闭。|未使用。|指向的指针`CMFCDesktopAlertWnd`对象。|未使用。|  
|AFX_WM_ON_DRAGCOMPLETE|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX_WM_ON_GET_TAB_TOOLTIP|选项卡窗口将要时显示的工具提示选项卡上，如果启用了自定义工具提示，则发送到主框架窗口。|未使用。|指向的指针`CMFCTabToolTipInfo`结构。|未使用。|  
|AFX_WM_ON_HSCROLL|发送到可调整大小控件栏控件。 处理此消息以接收来自通知`CMFCTabCtrl`对象中选项卡式小组件水平滚动条的滚动事件发生时。|低序位字指定滚动条值，该值指示用户的滚动请求。  有关更多信息，请参见本主题中后面的表。|未使用。|非零。|  
|AFX_WM_ON_MOVE_TAB|当用户将选项卡拖动到新位置，则发送到选项卡式窗口的父级。|在其原始位置的选项卡的从零开始的索引。|[out]在其新位置的选项卡的从零开始的索引。|为零。|  
|AFX_WM_ON_MOVETABCOMPLETE|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX_WM_ON_MOVETOTABGROUP|当用户将 MDI 子窗口从一个选项卡式组移到另一个，则发送到主框架窗口。|选项卡式窗口的句柄 (`CMFCTabCtrl`) 从已删除的 MDI 子窗口。|[out]选项卡式窗口的句柄 (`CMFCTabCtrl`) 到已插入 MDI 子窗口。|已忽略。|  
|AFX_WM_ON_PRESS_CLOSE_BUTTON|发送到的父级`CDockablePane`当用户单击**关闭**在标题控件条上的按钮。|未使用。|用户单击了在其上的可停靠窗格的指针**关闭**按钮。|`TRUE` 如果窗格中不能关闭;否则为 FALSE。|  
|AFX_WM_ON_RENAME_TAB|之后用户重命名一个可编辑的选项卡，则发送到选项卡式窗口的父级。|重命名选项卡的从零开始索引。|[out]指向包含新的选项卡名称的字符串的指针。|如果应用程序处理此消息; 非零框架将取消显示调用`CMFCBaseTabCtrl::SetTabLabel`。  如果返回零，然后`CMFCBaseTabCtrl::SetTabLabel`由框架调用。|  
|AFX_WM_ON_RIBBON_CUSTOMIZE|在用户开始自定义项时，发送到的父框架。 如果你想要显示你自己的自定义对话框，请处理此消息。|未使用。|指向要自定义功能区控件的指针。|如果应用程序处理此消息，并显示其自己的自定义对话框，则为非 0。 如果在应用程序返回零，则框架将显示内置的自定义对话框。|  
|AFX_WM_ON_TABGROUPMOUSEMOVE|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX_WM_POSTSETPREVIEWFRAME|发送通知的主框架用户更改的打印预览模式|`TRUE` 指示设置的打印预览模式。 `FALSE` 指示该打印预览模式处于关闭状态。|未使用。|未使用。|  
|AFX_WM_PROPERTY_CHANGED|发送到属性网格控件的所有者 (`CMFCPropertyGridCtrl`) 当用户更改所选属性的值。|属性列表控件 ID。|属性指向的指针 (`CMFCPropertyGridProperty`) 更改。|未使用。|  
|AFX_WM_RESETCONTEXTMENU|当用户重置中的自定义的上下文菜单时，发送到主框架窗口。|上下文菜单资源 ID。|指向当前的上下文菜单中， `CMFCPopupMenu`。|未使用。|  
|AFX_WM_RESETKEYBOARD|当用户在自定义期间重置所有键盘快捷键时，框架会将此消息发送到主框架窗口。|未使用。|未使用。|未使用。|  
|AFX_WM_RESETMENU|框架将此消息发送到的菜单所有者 （框架窗口） 时用户将重置应用程序框架菜单中的自定义|菜单资源 id。|未使用。|未使用。|  
|AFX_WM_RESETPROMPT|从工具栏中的工具栏上的用户重置自定义对话框时，框架将发送此消息。 默认处理程序会显示一个消息框，询问用户是否要重置此工具栏。|未使用。|未使用。|未使用。|  
|AFX_WM_RESETTOOLBAR|A`CMFCToolBar`对象将发送此消息，当一个工具栏还原到其原始状态，即，从资源加载。 处理此消息以重新插入其类派生自的工具栏按钮`CMFCToolbarButton`。 有关详细信息，请参阅`CMFCToolbarComboBoxButton`。|其状态已还原的工具栏的资源 ID。|未使用。|为零。|  
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` 用户单击常规菜单按钮时，对象会将此邮件发送给其所有者。 处理此消息使用每次`CMFCToolbarMenuButton`用户单击按钮时显示一个弹出菜单。|将消息发送的按钮命令 ID。|光标的屏幕坐标。 低序位字指定的 x 坐标。 高序位字指定的 y 坐标。|未使用。|  
|AFX_WM_TOOLBARMENU|当用户释放鼠标右键，鼠标指针在客户端或窗格中的非工作区时，发送到主框架窗口。|未使用。|鼠标指针的屏幕坐标。 低序位字指定的 x 坐标。 高序位字指定的 y 坐标。|如果应用程序将处理此消息; 则为零否则为则为非 0。|  
|AFX_WM_UPDATETOOLTIPS|发送到所有工具提示所有者以指示其工具提示控件应该重新创建。|应处理此消息的控件的类型。 请参阅有关的可能的值列表本主题后面的表。|未使用。|未使用。|  
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` 将此消息发送到的父框架中，当用户单击**帮助**按钮，或通过单击进入帮助模式**帮助**标题按钮或按 F1 键。|未使用。|指向的实例的指针`CMFCWindowsManagerDialog`。|未使用。|  
  
 下表显示的值的低位字`lParam`AFX_WM_HSCROLL 方法的参数：  
  
|||  
|-|-|  
|值|含义|  
|SB_ENDSCROLL|用户结束滚动。|  
|SB_LEFT|用户滚动到左上角。|  
|SB_RIGHT|用户滚动到右下角。|  
|SB_LINELEFT|用户滚动一个单元的左侧。|  
|SB_LINERIGHT|用户向一个单元的右滚动。|  
|SB_PAGELEFT|用户滚动左窗口的宽度。|  
|SB_PAGERIGHT|用户向右滚动的窗口的宽度。|  
|SB_THUMBPOSITION|用户拖动滚动框 （缩略图），并释放鼠标按钮。 高序位字指示在拖动操作结束时滚动框的位置。|  
|SB_THUMBTRACK|用户正在拖动滚动框。 此值，直到用户释放鼠标按钮会重复发送 AFX_WM_ON_HSCROLL 消息。 高序位字指示已向其拖动到滚动框的位置。|  
  
> [!NOTE]
>  高序位字`lParam`参数指定滚动框的当前位置，如果低序位字是 SB_THUMBPOSITION 或 SB_THUMBTRACK; 否则，不使用该单词。  
  
 下表列出的标志值`lParam`AFX_WM_UPDATETOOLTIPS 消息参数：  
  
|||  
|-|-|  
|Flag|值|  
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|  
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|  
|AFX_TOOLTIP_TYPE_TAB|0x0004|  
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|  
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|  
|AFX_TOOLTIP_TYPE_EDIT|0x0020|  
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|  
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|  
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|  
  
## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
