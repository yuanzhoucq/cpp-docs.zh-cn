---
title: 控件类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: 79a71a4660cd49f85726d730c9fad0b2f10f83bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338163"
---
# <a name="control-classes"></a>控件类

控件类封装了各种范围为从静态文本控件与树控件的标准 Windows 控件。 此外，MFC 提供了一些新的控件，包括使用位图和控件条按钮。

控件的类名称以结尾"**Ctrl**"了新增的 Windows 95 和 Windows NT 版本 3.51。

## <a name="static-display-controls"></a>静态显示控件

[CStatic](../mfc/reference/cstatic-class.md)<br/>
一个静态显示窗口。 静态控件用于标签、 框中，或单独的对话框或窗口中的其他控件。 它们还可能会显示图形映像而不是文本或一个框。

## <a name="text-controls"></a>文本控件

[CEdit](../mfc/reference/cedit-class.md)<br/>
一个可编辑文本控件窗口。 编辑控件用于接受来自用户的文本输入。

[CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)<br/>
用于操作的 Internet 协议 (IP) 地址支持的编辑框。

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
用户可以输入以及编辑文本的控件。 与控件封装在不同`CEdit`，rich edit 控件支持的字符和段落格式设置和 OLE 对象。

## <a name="controls-that-represent-numbers"></a>表示的数字的控件

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
包含一个滑块，用户将移动以选择值或一组值的控件。

[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)<br/>
一对箭头按钮的用户可以单击要递增或递减值。

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
显示一个矩形，逐渐填充来显示从左到右，以指示操作的进度。

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
滚动条控件窗口。 此类提供滚动条，以用作对话框或窗口中，通过该用户可以指定一个范围内的位置中的控件的功能。

## <a name="buttons"></a>按钮

[CButton](../mfc/reference/cbutton-class.md)<br/>
按钮控件窗口。 此类提供一种编程接口下压按钮、 复选框，或在对话框或窗口中的单选按钮。

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
一个具有一个位图，而不是文本标题按钮。

## <a name="lists"></a>列表

[CListBox](../mfc/reference/clistbox-class.md)<br/>
一个列表框控件窗口。 列表框中显示用户可以查看和选择的项的列表。

[CDragListBox](../mfc/reference/cdraglistbox-class.md)<br/>
提供 Windows 列表框; 功能允许用户在列表框内移动文件名和字符串文本，如列表框项。 借助此功能的列表框可用于按顺序而非按字母顺序排列的项列表，例如在项目中包含路径或文件。

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
一个组合框控件窗口。 组合框由一个编辑控件和列表框组成。

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
通过为图像列表提供支持扩展组合框控件。

[CCheckListBox](../mfc/reference/cchecklistbox-class.md)<br/>
显示带复选框，用户可以选中或清除，每个项旁边的项列表。

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
显示项的集合，其中每个包括的一个图标和标签时，在文件资源管理器的方式类似于在右窗格中。

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
显示图标和标签的排列方式类似于左窗格中的文件资源管理器中的层次的列表。

## <a name="toolbars-and-status-bars"></a>工具栏和状态栏

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具栏公共控件的功能。 大多数 MFC 程序使用[CToolBar](../mfc/reference/ctoolbar-class.md)而不是此类。

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
水平窗口中，通常分为的窗格，在其中应用程序可显示状态信息。 大多数 MFC 程序使用[CStatusBar](../mfc/reference/cstatusbar-class.md)而不是此类。

## <a name="miscellaneous-controls"></a>其他控件

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
显示简单的视频剪辑。

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
一个小型的弹出窗口，显示的文本来描述应用程序中工具用途的单行。

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
支持一个扩展的编辑控件或一个简单日历界面控件，它允许用户选择特定日期或时间值。

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
显示标题或列的标签。

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
支持允许用户选择日期的简单日历界面控件。

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
具有选项卡上，用户单击，类似于笔记本中的分隔条的控件。

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
使用户能够创建热组合键，用户可以按操作更快地执行。

[CLinkCtrl](../mfc/reference/clinkctrl-class.md)<br/>
呈现标记向上文本，并启动合适的应用程序，当用户单击嵌入的链接。

[CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)<br/>
提供 MFC 窗口中的 WebBrowser ActiveX 控件功能。

## <a name="related-classes"></a>相关的类

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
提供 Windows 图像列表的功能。 图像列表将与列表控件和树控件一起使用。 它们还可以用于存储和存档一组大小相同的位图。

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
与 Windows 控件相关联的所有视图的基类。 根据控件的视图如下所述。

[CEditView](../mfc/reference/ceditview-class.md)<br/>
包含 Windows 标准的视图的编辑控件。

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
一个包含 Windows 丰富视图编辑控件。

[CListView](../mfc/reference/clistview-class.md)<br/>
一个包含 Windows 列表控件的视图。

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
一个包含 Windows 树控件的视图。

## <a name="see-also"></a>请参阅

[类概述](../mfc/class-library-overview.md)
