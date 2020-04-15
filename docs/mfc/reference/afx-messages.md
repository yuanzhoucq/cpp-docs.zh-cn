---
title: AFX 消息
ms.date: 11/04/2016
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
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363596"
---
# <a name="afx-messages"></a>AFX 消息

这些消息在 MFC 中使用。

## <a name="messages"></a>消息

下表列出了在 MFC 库中使用的消息：

||||||
|-|-|-|-|-|
|消息|说明|[在]*wParam*|*lParam* （除非另有说明，否则所有参数均处于[in]。|返回值|
|AFX_WM_ACCGETOBJECT|未使用。|未使用。|不适用。|不适用。|
|AFX_WM_ACCGETSTATE|用于辅助功能支持。 将此消息发送到`CMFCPopupMenu`或`CMFCRibbonPanelMenu`检索当前元素的状态。|元素的索引，可以是菜单按钮或分隔符。|未使用。|元素状态。 如果索引无效，则为 -1;如果菜单按钮没有特殊属性，则为 0。 否则，它是以下标志的组合：<br /><br /> 禁用TBBS_DISABLED = 项<br /><br /> TBBS_CHECKED = 项目已选中<br /><br /> TBBS_BUTTON = 该项目是标准按钮<br /><br /> 按下TBBS_PRESSED = 按钮<br /><br /> TBBS_INDETERMINATE = 未定义状态<br /><br /> TBBS_SEPARATOR - 而不是菜单按钮，此元素形成其他菜单项之间的分隔|
|AFX_WM_CHANGE_ACTIVE_TAB|框架将此消息发送到可调整大小的控制栏控件。 处理此消息以在用户更改活动`CMFCTabCtrl`选项卡时接收来自对象的通知。|选项卡的索引。|未使用。|零。|
|AFX_WM_CHANGE_CURRENT_FOLDER|当用户更改当前文件夹`CMFCShellListCtrl`时，框架会将此消息发送到 父级。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGEVISUALMANAGER|当用户更改当前可视化管理器时，框架会将此消息发送到所有框架窗口。 为了响应此消息，帧窗口重新计算其区域并根据需要调整其他参数。 如果需要有关此事件的通知，可以在应用程序中处理AFX_WM_CHANGEVISUALMANAGER消息。 您必须调用基类处理程序 （`OnChangeVisualManager`， 以确保框架对此事件的内部处理发生。|未使用。|未使用。|未使用。|
|AFX_WM_CHANGING_ACTIVE_TAB|发送到对象的父级`CMFCTabCtrl`。  如果要在用户重置选项卡时接收来自`CMFCTabCtrl`对象的通知，请处理此消息。|正在激活的选项卡的索引。|未使用。|零。|
|AFX_WM_CHECKEMPTYMINIFRAME|仅供内部使用。|不适用。|不适用。|不适用。|
|AFX_WM_CREATETOOLBAR|在`CMFCToolBarsListPropertyPage`自定义过程中用户创建新工具栏时发送。 您可以处理此消息以实例化自定义 CMFCToolBar 派生的对象。 如果处理此消息并创建自己的工具栏，请省略对默认处理程序的调用。|未使用。|指向包含工具栏名称的字符串的指针。|指向新创建的工具栏的指针。 NULL 表示工具栏创建已取消。|
|AFX_WM_CUSTOMIZEHELP|当用户按下 **"帮助"** 按钮或 F1`CMFCToolbarCustomize Dialog`键时，从自定义属性工作表发送到主框架窗口。|指定自定义属性表的活动页。|一个指向 `CMFCToolbarCustomize Dialog` 对象的指针。|Zero。|
|AFX_WM_CUSTOMIZETOOLBAR|发送`CMFCToolbarCustomize Dialog`此消息以通知父帧用户正在创建新工具栏。|当自定义启动时为 TRUE，自定义完成后 FALSE。|未使用。|Zero。|
|AFX_WM_DELETETOOLBAR|当用户要在自定义模式下删除工具栏时，发送到主框架窗口。<br /><br /> 处理此消息，当用户在自定义模式下删除工具栏时执行其他操作。 还应调用默认处理程序 （`OnToolbarDelete`， 删除工具栏。 默认处理程序返回一个值，指示是否可以删除工具栏。|未使用。|指向要删除`CMFCToolBar`的对象的指针。|如果无法删除工具栏，则非零;否则 0。|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`将此消息发送到主框架窗口以检索文档颜色。|未使用。|[进出]指向对象的指针`CList<COLORREF, COLORREF>`。|Zero。|
|AFX_WM_GETDRAGBOUNDS|仅供内部使用。|不适用。|不适用。|不适用。|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|当用户突出显示功能区列表项时发送到主框架窗口。|突出显示项的索引|指向`CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_AFTER_SHELL_COMMAND|当用户完成执行 shell `CMFCShellListCtrl` `CMFCShellTreeCtrl`命令时，已发送到 或 控件的父项。|用户执行的命令的 ID|未使用。|如果应用程序处理此消息，则应返回零。|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|框架在显示弹出菜单之前，会将此消息发送给功能区父级。 您可以随时处理此消息并修改弹出式菜单。|未使用。|指向`CMFCBaseRibbonElement`|未使用。|
|AFX_WM_ON_CANCELTABMOVE|仅供内部使用。|不适用。|不适用。||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|当用户更改活动功能区控制类别时，框架会将此消息发送到主框架。|未使用。|指向其类别已更改`CMFCRibbonBar`的 的指针。|未使用。|
|AFX_WM_ON_CLOSEPOPUPWINDOW|框架发送此消息以通知所有者`CMFCDesktopAlertWnd`窗口即将关闭。|未使用。|指向`CMFCDesktopAlertWnd`对象的指针。|未使用。|
|AFX_WM_ON_DRAGCOMPLETE|仅供内部使用。|不适用。|不适用。|不适用。|
|AFX_WM_ON_GET_TAB_TOOLTIP|如果启用了自定义工具提示，则当选项卡窗口要显示选项卡的工具提示时，发送到主框架窗口。|未使用。|指向结构的`CMFCTabToolTipInfo`指针。|未使用。|
|AFX_WM_ON_HSCROLL|发送到可调整大小的控制栏控件。 处理此消息，在选项卡式小`CMFCTabCtrl`部件水平滚动栏中发生滚动事件时接收来自对象的通知。|低阶单词指定指示用户滚动请求的滚动条值。  有关更多信息，请参见本主题中后面的表。|未使用。|零。|
|AFX_WM_ON_MOVE_TAB|当用户将选项卡拖动到新位置时，已发送到选项卡窗口的父级。|选项卡的原始位置的零基索引。|[出]选项卡的新位置的零基索引。|Zero。|
|AFX_WM_ON_MOVETABCOMPLETE|仅供内部使用。|不适用。|不适用。|不适用。|
|AFX_WM_ON_MOVETOTABGROUP|当用户将 MDI 子窗口从一个选项卡式组移动到另一个选项卡式组时，已发送到主框架窗口。|选项卡式窗口 （`CMFCTabCtrl`） 的句柄，从中删除 MDI 子窗口。|[出]已插入 MDI 子`CMFCTabCtrl`窗口的选项卡式窗口的句柄。|已忽略。|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|将用户单击控制栏`CDockablePane`标题上的 **"关闭**"按钮时发送到父级。|未使用。|指向可停靠窗格的指针，用户单击其"**关闭**"按钮。|如果窗格无法关闭，则为 TRUE;如果窗格无法关闭，则为 TRUE。否则 FALSE。|
|AFX_WM_ON_RENAME_TAB|在用户重命名可编辑选项卡后，发送到选项卡式窗口的父级。|重命名选项卡的零基索引。|[出]指向包含新选项卡名称的字符串的指针。|如果应用程序处理此消息，则非零;框架将禁止对`CMFCBaseTabCtrl::SetTabLabel`的调用。  如果返回零，则`CMFCBaseTabCtrl::SetTabLabel`由框架调用。|
|AFX_WM_ON_RIBBON_CUSTOMIZE|当用户开始自定义时发送到父框架。 如果要显示自己的自定义对话框，请处理此消息。|未使用。|指向要自定义的功能区控件的指针。|如果应用程序处理此消息并显示其自己的自定义对话框，则为非零。 如果应用程序返回零，框架将显示内置自定义对话框。|
|AFX_WM_ON_TABGROUPMOUSEMOVE|仅供内部使用。|不适用。|不适用。|不适用。|
|AFX_WM_POSTSETPREVIEWFRAME|已发送以通知主框架用户更改打印预览模式|TRUE 表示已设置打印预览模式。 FALSE 表示打印预览模式已关闭。|未使用。|未使用。|
|AFX_WM_PROPERTY_CHANGED|当用户更改所选属性的值时，将发送到属性`CMFCPropertyGridCtrl`网格控件 （ ） 的所有者。|属性列表的控制 ID。|指向已更改的属性的`CMFCPropertyGridProperty`指针 。|未使用。|
|AFX_WM_RESETCONTEXTMENU|当用户在自定义期间重置上下文菜单时发送到主框架窗口。|上下文菜单的资源 ID。|指向当前上下文菜单的指针`CMFCPopupMenu`。|未使用。|
|AFX_WM_RESETKEYBOARD|当用户在自定义期间重置所有键盘快捷键时，框架会将此消息发送到主框架窗口。|未使用。|未使用。|未使用。|
|AFX_WM_RESETMENU|当用户在自定义期间重置应用程序框架菜单时，框架会将此消息发送给菜单所有者（框架窗口）|菜单资源 ID。|未使用。|未使用。|
|AFX_WM_RESETPROMPT|当用户从工具栏自定义对话框重置工具栏时，框架将发送此消息。 默认处理程序显示一个消息框，询问用户是否要重置工具栏。|未使用。|未使用。|未使用。|
|AFX_WM_RESETTOOLBAR|当`CMFCToolBar`工具栏还原到其原始状态（即从资源加载）时，对象将发送此消息。 处理此消息以重新插入其类派生自`CMFCToolbarButton`的工具栏按钮。 有关详细信息，请参阅 `CMFCToolbarComboBoxButton`。|已还原状态的工具栏的资源 ID。|未使用。|Zero。|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`当用户单击常规菜单按钮时，对象会向其所有者发送此消息。 每次用户单击按钮时，您都`CMFCToolbarMenuButton`用于显示弹出菜单时处理此消息。|发送消息的按钮的命令 ID。|光标的屏幕坐标。 低阶单词指定 x 坐标。 高阶单词指定 y 坐标。|未使用。|
|AFX_WM_TOOLBARMENU|当用户释放鼠标的右键时，当鼠标指针位于窗格的客户端或非客户端区域时，发送到主框架窗口。|未使用。|鼠标指针的屏幕坐标。 低阶单词指定 x 坐标。 高阶单词指定 y 坐标。|如果应用程序处理此消息，则为零;如果应用程序处理此消息，则为零。否则，非零。|
|AFX_WM_UPDATETOOLTIPS|发送给所有工具提示所有者，以指示应重新创建其工具提示控件。|应处理此消息的控件的类型。 有关可能值的列表，请参阅本主题后面的表。|未使用。|未使用。|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`当用户单击 **"帮助"** 按钮时，将此消息发送到父帧，或者通过单击 **"帮助**标题"按钮或 F1 键进入帮助模式。|未使用。|指向 的实例的`CMFCWindowsManagerDialog`指针。|未使用。|

下表显示了AFX_WM_HSCROLL方法的*lParam*参数的低字的值：

|||
|-|-|
|“值”|含义|
|SB_ENDSCROLL|用户结束滚动。|
|SB_LEFT|用户滚动到左上角。|
|SB_RIGHT|用户滚动到右下角。|
|SB_LINELEFT|用户滚动由一个单位左。|
|SB_LINERIGHT|用户按一个单位向右滚动。|
|SB_PAGELEFT|用户按窗口的宽度向左滚动。|
|SB_PAGERIGHT|用户按窗口的宽度向右滚动。|
|SB_THUMBPOSITION|用户已拖动滚动框（拇指）并释放鼠标按钮。 高阶单词指示滚动框在拖动操作结束时的位置。|
|SB_THUMBTRACK|用户正在拖动滚动框。 在用户释放鼠标按钮之前，使用此值重复发送AFX_WM_ON_HSCROLL消息。 高阶单词指示滚动框已拖动到的位置。|

> [!NOTE]
> 如果低阶词SB_THUMBPOSITION或SB_THUMBTRACK，*则 lParam*参数的高阶字指定滚动框的当前位置;否则，不使用这个词。

下表列出了 AFX_WM_UPDATETOOLTIPS消息的*lParam*参数的标志值：

|||
|-|-|
|标志|“值”|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
