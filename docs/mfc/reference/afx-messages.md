---
title: "AFX 消息 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SB_LINELEFT"
  - "SB_THUMBTRACK"
  - "AFX_TOOLTIP_TYPE_EDIT"
  - "AFX_WM_ON_HSCROLL"
  - "SB_PAGERIGHT"
  - "AFX_WM_RESETPROMPT"
  - "AFX_WM_CHANGE_RIBBON_CATEGORY"
  - "AFX_TOOLTIP_TYPE_MINIFRAME"
  - "AFX_WM_CUSTOMIZETOOLBAR"
  - "AFX_WM_CHANGE_ACTIVE_TAB"
  - "AFX_WM_ACCGETOBJECT"
  - "AFX_WM_TOOLBARMENU"
  - "AFX_TOOLTIP_TYPE_DOCKBAR"
  - "AFX_WM_CUSTOMIZEHELP"
  - "AFX_WM_ON_GET_TAB_TOOLTIP"
  - "AFX_WM_ON_RIBBON_CUSTOMIZE"
  - "AFX_WM_ON_DRAGCOMPLETE"
  - "AFX_WM_RESETTOOLBAR"
  - "AFX_WM_ON_MOVETOTABGROUP"
  - "AFX_WM_CHECKEMPTYMINIFRAME"
  - "AFX_WM_GETDOCUMENTCOLORS"
  - "SB_RIGHT"
  - "AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU"
  - "AFX_WM_ACCGETSTATE"
  - "SB_PAGELEFT"
  - "SB_ENDSCROLL"
  - "AFX_WM_ON_CANCELTABMOVE"
  - "AFX_TOOLTIP_TYPE_TAB"
  - "AFX_WM_WINDOW_HELP"
  - "AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM"
  - "AFX_WM_SHOWREGULARMENU"
  - "AFX_TOOLTIP_TYPE_TOOLBAR"
  - "AFX_WM_CHANGE_CURRENT_FOLDER"
  - "AFX_WM_UPDATETOOLTIPS"
  - "AFX_WM_ON_MOVE_TAB"
  - "AFX_WM_CHANGING_ACTIVE_TAB"
  - "AFX_WM_RESETMENU"
  - "AFX_WM_GETDRAGBOUNDS"
  - "AFX_WM_RESETCONTEXTMENU"
  - "AFX_TOOLTIP_TYPE_BUTTON"
  - "AFX_WM_ON_CLOSEPOPUPWINDOW"
  - "AFX_TOOLTIP_TYPE_TOOLBOX"
  - "AFX_WM_CHANGEVISUALMANAGER"
  - "SB_LINERIGHT"
  - "AFX_WM_ON_RENAME_TAB"
  - "AFX_TOOLTIP_TYPE_DEFAULT"
  - "AFX_WM_ON_TABGROUPMOUSEMOVE"
  - "SB_LEFT"
  - "AFX_WM_DELETETOOLBAR"
  - "AFX_WM_PROPERTY_CHANGED"
  - "AFX_TOOLTIP_TYPE_ALL"
  - "AFX_WM_ACCHITTEST"
  - "AFX_WM_ON_AFTER_SHELL_COMMAND"
  - "AFX_WM_ON_PRESS_CLOSE_BUTTON"
  - "AFX_WM_RESETKEYBOARD"
  - "AFX_WM_ON_MOVETABCOMPLETE"
  - "AFX_WM_CREATETOOLBAR"
  - "SB_THUMBPOSITION"
  - "AFX_WM_POSTSETPREVIEWFRAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFX 消息"
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# AFX 消息
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些消息使用 MFC。  
  
## 消息  
 下表列出了 MFC 库的消息：  
  
||||||  
|-|-|-|-|-|  
|消息|说明|\[in\] `wParam`|除非另行说明`lParam` \(所有参数都为 \[in\] 。\)|返回值|  
|AFX\_WM\_ACCGETOBJECT|未使用。|未使用。|不适用。|不适用。|  
|AFX\_WM\_ACCGETSTATE|用于访问支持。  发送此信息对 `CMFCPopupMenu` 或 `CMFCRibbonPanelMenu` 检索当前元素的状态。|元素索引，可以为按钮或菜单分隔符。|未使用。|元素的状态。  如果索引无效则其值为\-1，如果菜单按钮没有特殊特性为0。  否则它是下列标记的组合：<br /><br /> TBBS\_DISABLED：项禁用服务<br /><br /> TBBS\_CHECKED \- 项检查<br /><br /> TBBS\_BUTTON \- 项是一个标准按钮<br /><br /> \- TBBS\_PRESSED 按钮<br /><br /> TBBS\_INDETERMINATE \- 未定义状态<br /><br /> TBBS\_SEPARATOR 菜单而不是按钮，此窗体分离其他菜单项之间的元素。|  
|AFX\_WM\_CHANGE\_ACTIVE\_TAB|框架发送此信息向可调整大小的控件条控件。  当用户更改活动选项卡，请处理此消息接收通知的 `CMFCTabCtrl` 对象。|标签的索引。|未使用。|非零值。|  
|AFX\_WM\_CHANGE\_CURRENT\_FOLDER|当用户更改当前文件夹时，框架将发送此信息对 `CMFCShellListCtrl` 父级。|未使用。|未使用。|未使用。|  
|AFX\_WM\_CHANGEVISUALMANAGER|当用户更改当前视觉管理器时，框架将发送此信息向所有框架窗口。  为了响应此消息，框架窗口需要重新计算其区域并调整其他参数。  如果需要，会通知此事件，您可以在应用程序中处理 AFX\_WM\_CHANGEVISUALMANAGER 消息。  必须调用基类处理程序 \(`OnChangeVisualManager`\) 以确保框架的内部处理时发生此事件。|未使用。|未使用。|未使用。|  
|AFX\_WM\_CHANGING\_ACTIVE\_TAB|发送到 `CMFCTabCtrl` 父对象。请处理此消息，当用户重置选项卡时，如果要从 `CMFCTabCtrl` 对象接收的通知。|激活选项卡的索引。|未使用。|非零值。|  
|AFX\_WM\_CHECKEMPTYMINIFRAME|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX\_WM\_CREATETOOLBAR|发送从 `CMFCToolBarsListPropertyPage`，当用户在自定义过程中创建新工具栏。  可以处理此消息以实例化自定义 CMFCToolBar 派生的对象。  如果处理此消息并创建自己工具栏，请省略调用默认处理程序。|未使用。|为工具栏包含名称的字符串的指针。|为新创建工具栏上的指针。  NULL 表示工具栏创建取消。|  
|AFX\_WM\_CUSTOMIZEHELP|发送到自定义属性表 `CMFCToolbarCustomize``Dialog`，则用户按 **帮助** 按钮或 F1 键的主框架窗口。|指定自定义属性表的活动页。|一个 `CMFCToolbarCustomize``Dialog` 对象的指针。|零。|  
|AFX\_WM\_CUSTOMIZETOOLBAR|`CMFCToolbarCustomize` `Dialog` 发送此信息通知父框架用户创建新工具栏。|`TRUE`，当自定义起始，`FALSE`，同时自定义完成。|未使用。|零。|  
|AFX\_WM\_DELETETOOLBAR|发送到主框架窗口，当用户要删除的自定义模式的工具栏。<br /><br /> 当用户删除自定义模式时，的工具栏中处理此消息采用其他操作。  还应调用默认处理程序 \(`OnToolbarDelete`\)，删除工具栏。  默认处理程序返回的值指示删除工具栏是可能的。|未使用。|指向要删除的`CMFCToolBar` 对象的指针。|非零则工具栏无法删除；否则 0。|  
|AFX\_WM\_GETDOCUMENTCOLORS|`CMFCColorMenuButton` 将此信息向主框架窗口检索文档颜色。|未使用。|\[in,out\] 指向 `CList<COLORREF, COLORREF>` 对象的指针。|零。|  
|AFX\_WM\_GETDRAGBOUNDS|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX\_WM\_HIGHLIGHT\_RIBBON\_LIST\_ITEM|发送到主框架窗口，则用户突出显示功能区的列表项。|选中高亮项的索引。|指向 `CMFCBaseRibbonElement`的指针。|未使用。|  
|AFX\_WM\_ON\_AFTER\_SHELL\_COMMAND|发送给 `CMFCShellListCtrl` 或 `CMFCShellTreeCtrl` 控件父级，当用户完成执行命令 shell。|用户执行命令的 ID|未使用。|如果应用程序进程此消息，则应返回零。|  
|AFX\_WM\_ON\_BEFORE\_SHOW\_RIBBON\_ITEM\_MENU|在显示弹出菜单之前，发送此信息向功能区框架的父级。  可以处理此消息并随时修改弹出菜单。|未使用。|指向 `CMFCBaseRibbonElement`的指针。|未使用。|  
|AFX\_WM\_ON\_CANCELTABMOVE|仅限内部使用。|不适用。|不适用。||  
|AFX\_WM\_ON\_CHANGE\_RIBBON\_CATEGORY|当用户更改功能区控件可用类别时，框架将发送此信息对主框架。|未使用。|为类别更改的 `CMFCRibbonBar` 的指针。|未使用。|  
|AFX\_WM\_ON\_CLOSEPOPUPWINDOW|框架发送此信息通知窗口将关闭 `CMFCDesktopAlertWnd` 的所有者。|未使用。|一个指向 `CMFCDesktopAlertWnd` 对象的指针。|未使用。|  
|AFX\_WM\_ON\_DRAGCOMPLETE|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX\_WM\_ON\_GET\_TAB\_TOOLTIP|发送到主框架窗口，则窗口将选项卡显示选项卡的工具提示，那么，如果自定义工具提示。|未使用。|指向 `CMFCTabToolTipInfo` 结构的指针。|未使用。|  
|AFX\_WM\_ON\_HSCROLL|发送对可调整大小的控件条控件。  当滚动事件，在选项卡式小组件水平滚动条时发生，请处理此消息接收通知的 `CMFCTabCtrl` 对象。|低序 Word 指定指示用户的滚动条滚动请求的值。有关更多信息，请参见本主题中后面的表。|未使用。|非零值。|  
|AFX\_WM\_ON\_MOVE\_TAB|发送给一个选项卡式窗口的父级，则用户将选项卡拖动到新位置。|选项卡的在原始位置从零开始的索引原始位置。|\[out\]选项卡的在原始位置从零开始的索引新位置。|零。|  
|AFX\_WM\_ON\_MOVETABCOMPLETE|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX\_WM\_ON\_MOVETOTABGROUP|发送到主框架窗口，则用户将从一个制表符分隔的 MDI 子窗口到另一个。|一个句柄 \(`CMFCTabCtrl`\) 类型的 MDI 子窗口被移除选项卡式窗口。|\[out\] 一个句柄 \(`CMFCTabCtrl`\) MDI 子窗口插入的选项卡式窗口。|已忽略。|  
|AFX\_WM\_ON\_PRESS\_CLOSE\_BUTTON|当用户单击按钮 **关闭** 对控件条的标题，发送到 `CDockablePane`。|未使用。|为用户单击按钮的 **关闭** 可停靠的窗格的指针。|`TRUE`，如果窗格不能关闭；否则为 false。|  
|AFX\_WM\_ON\_RENAME\_TAB|发送到选项卡式窗口父在用户后重命名可编辑的选项卡。|重命名的选项卡的从零开始的索引。|\[out\] 一个指向包含命名新标签的字符串的指针。|非零，如果应用程序的过程；此消息框架将取消调用 `CMFCBaseTabCtrl::SetTabLabel`。如果非零返回，则 `CMFCBaseTabCtrl::SetTabLabel` 由框架调用。|  
|AFX\_WM\_ON\_RIBBON\_CUSTOMIZE|当用户启动自定义项，发送对父帧。  如果希望查看自己的自定义对话框，请处理此消息。|未使用。|向功能区控件的指针将自定义。|非零，则应用程序进程此消息和显示自己的自定义对话框。  如果应用程序以返回零，框架将显示内置自定义对话框。|  
|AFX\_WM\_ON\_TABGROUPMOUSEMOVE|仅限内部使用。|不适用。|不适用。|不适用。|  
|AFX\_WM\_POSTSETPREVIEWFRAME|发送通知主框架用户更改打印预览模式|`TRUE` 指示打印预览模式设置。  `FALSE` 指示打印预览模式被关闭。|未使用。|未使用。|  
|AFX\_WM属性更改|发送到属性网格控件 \(`CMFCPropertyGridCtrl`的所有者，当用户更改选择的属性的值。|属性列表的控件ID。|与更改的属性 \(`CMFCProp``ertyGridProperty`\) 的指针。|未使用。|  
|AFX\_WM\_RESETCONTEXTMENU|发送到主框架窗口，如果用户在自定义上下文菜单时重置。|上下文菜单资源的资源 ID。|一个指向当前上下文的指针 `CMFCPopupMenu`。|未使用。|  
|AFX\_WM\_RESETKEYBOARD|如果用户在自定义时，重置所有键盘快捷框架发送此信息向主框架窗口。|未使用。|未使用。|未使用。|  
|AFX\_WM\_RESETMENU|当用户在自定义时重置应用程序帧菜单，框架发送此消息给菜单所有者（一个框架窗口） 。|菜单资源ID。|未使用。|未使用。|  
|AFX\_WM\_RESETPROMPT|当用户重置从工具栏的工具栏自定义对话框时，框架将发送此信息。  默认处理程序显示的消息询问用户是否希望重置工具栏。|未使用。|未使用。|未使用。|  
|AFX\_WM\_RESETTOOLBAR|当工具栏，还原为其原始状态，例如，加载从资源时，`CMFCToolBar` 对象将此信息。  处理此消息重新插入类从 `CMFCToolbarButton`派生的工具栏按钮。  有关详细信息，请参阅`CMFCToolbarComboBoxButton`。|状态还原工具栏的资源 ID。|未使用。|零。|  
|AFX\_WM\_SHOWREGULARMENU|当用户单击菜单，普通按钮时，`CMFCToolbarMenuButton` 对象将此信息转发给其所有者。  每次处理此消息使用 `CMFCToolbarMenuButton` 显示弹出菜单，当用户单击该按钮时。|发送按钮的命令 ID。|光标的屏幕坐标。  低序 Word 指定 x 坐标。  高位 Word 指定 y 坐标。|未使用。|  
|AFX\_WM\_TOOLBARMENU|发送到主框架窗口，当用户释放鼠标右键的，当鼠标指针向左、窗格的客户端或非客户端区域中。|未使用。|鼠标指针的屏幕坐标。  低序 Word 指定 x 坐标。  高位 Word 指定 y 坐标。|如果应用程序的过程为零；否则此消息为非零值。|  
|AFX\_WM\_UPDATETOOLTIPS|发送对所有工具提示指示所有者应重新创建这些控件的工具提示。|应处理此消息的控件的类型。  为可能值列表之后参见本表主题。|未使用。|未使用。|  
|AFX\_WM\_WINDOW\_HELP|`CMFCWindowsManagerDialog` 将此信息添加到父帧，当用户单击按钮时 **帮助**，或者通过单击标题 **帮助** 按钮或 F1 键访问帮助模式。|未使用。|对 `CMFCWindowsManagerDialog`实例的指针。|未使用。|  
  
 下表显示 AFX\_WM\_HSCROLL 方法的参数 `lParam` 的右下角 Word 的值：  
  
|||  
|-|-|  
|值|含义|  
|SB\_ENDSCROLL|用户结束卷。|  
|SB\_LEFT|用户滚动到左上角。|  
|SB\_RIGHT|对低权限的用户滚动。|  
|SB\_LINELEFT|用户用单位滚动的。|  
|SB\_LINERIGHT|用户滚动向右移动一个单元。|  
|SB\_PAGELEFT|用户通过左滚动窗口的宽度。|  
|SB\_PAGERIGHT|用户通过右滚动窗口的宽度。|  
|SB\_THUMBPOSITION|用户拖动滚动框 \(滚动块\) 并释放鼠标按钮。  高位 Word 指示拖动滚动框的位置在操作结束时。|  
|SB\_THUMBTRACK|用户拖动滚动框。  AFX\_WM\_ON\_HSCROLL 重复使用此信息发送值，直至用户释放鼠标按钮。  高位 Word 指示拖动滚动框的位置。|  
  
> [!NOTE]
>  如果低序单词是 SB\_THUMBPOSITION 或 SB\_THUMBTRACK，`lParam` 参数的高位 Word 指定滚动框的当前位置；否则，不使用此单词。  
  
 下表列出 AFX\_WM\_UPDATETOOLTIPS 消息的参数 `lParam` 的标志值：  
  
|||  
|-|-|  
|Flag|值|  
|AFX\_TOOLTIP\_TYPE\_DEFAULT|0x0001|  
|AFX\_TOOLTIP\_TYPE\_TOOLBAR|0x0002|  
|AFX\_TOOLTIP\_TYPE\_TAB|0x0004|  
|AFX\_TOOLTIP\_TYPE\_MINIFRAME|0x0008|  
|AFX\_TOOLTIP\_TYPE\_DOCKBAR|0x0010|  
|AFX\_TOOLTIP\_TYPE\_EDIT|0x0020|  
|AFX\_TOOLTIP\_TYPE\_BUTTON|0x0040|  
|AFX\_TOOLTIP\_TYPE\_TOOLBOX|0x0008|  
|AFX\_TOOLTIP\_TYPE\_ALL|0xFFFF|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)