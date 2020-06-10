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
ms.openlocfilehash: 277802bff3e4833396c4bf114ff8880fcd26343d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623005"
---
# <a name="control-classes"></a>控件类

控件类封装多种标准 Windows 控件，范围从静态文本控件到树控件。 此外，MFC 还提供一些新控件，其中包括带有位图和控件条的按钮。

其类名称以 "**Ctrl**" 结尾的控件在 Windows 95 和 windows NT 版本3.51 中是新增的。

## <a name="static-display-controls"></a>静态显示控件

[CStatic](reference/cstatic-class.md)<br/>
静态显示窗口。 静态控件用于在对话框或窗口中标记、框或分隔其他控件。 它们还可能显示图形图像而不是文本或框。

## <a name="text-controls"></a>文本控件

[CEdit](reference/cedit-class.md)<br/>
可编辑文本控件窗口。 编辑控件用于接受来自用户的文本输入。

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
支持编辑框来处理 Internet 协议（IP）地址。

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
用户可在其中输入和编辑文本的控件。 与中封装的控件不同 `CEdit` ，富编辑控件支持字符和段落格式设置以及 OLE 对象。

## <a name="controls-that-represent-numbers"></a>表示数字的控件

[CSliderCtrl](reference/csliderctrl-class.md)<br/>
包含滑块的控件，用户可在该控件中选择一个值或一组值。

[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
一对箭头按钮，用户可以单击该按钮来递增或递减值。

[CProgressCtrl](reference/cprogressctrl-class.md)<br/>
显示一个从左到右逐渐填充的矩形，用于指示操作的进度。

[CScrollBar](reference/cscrollbar-class.md)<br/>
滚动条控件窗口。 类提供滚动条的功能，以用作对话框或窗口中的控件，用户可以通过该滚动条指定范围内的位置。

## <a name="buttons"></a>按钮

[CButton](reference/cbutton-class.md)<br/>
按钮控件窗口。 类为对话框或窗口中的按钮、复选框或单选按钮提供编程接口。

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
带有位图而不是文本标题的按钮。

## <a name="lists"></a>列表

[CListBox](reference/clistbox-class.md)<br/>
列表框控件窗口。 列表框显示用户可以查看和选择的项的列表。

[CDragListBox](reference/cdraglistbox-class.md)<br/>
提供 Windows 列表框的功能;允许用户在列表框中移动列表框项，例如文件名和字符串文字。 具有此功能的列表框对项列表的使用方式不同于按字母顺序排列的顺序，如在项目中包含路径名或文件。

[CComboBox](reference/ccombobox-class.md)<br/>
组合框控件窗口。 组合框由编辑控件和列表框组成。

[CComboBoxEx](reference/ccomboboxex-class.md)<br/>
通过为图像列表提供支持扩展组合框控件。

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
显示具有复选框的项的列表，用户可以选中或清除每个项旁边的复选框。

[CListCtrl](reference/clistctrl-class.md)<br/>
显示项的集合，每个项都包含一个图标和一个标签，其方式类似于文件资源管理器的右窗格。

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
显示以类似于文件资源管理器左窗格的方式排列的图标和标签的层次结构列表。

## <a name="toolbars-and-status-bars"></a>工具栏和状态栏

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
提供 Windows 工具栏公共控件的功能。 大多数 MFC 程序使用[CToolBar](reference/ctoolbar-class.md) ，而不是此类。

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
水平窗口，通常分为窗格，应用程序可以在其中显示状态信息。 大多数 MFC 程序使用[CStatusBar](reference/cstatusbar-class.md) ，而不是此类。

## <a name="miscellaneous-controls"></a>其他控件

[CAnimateCtrl](reference/canimatectrl-class.md)<br/>
显示一个简单的视频剪辑。

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
一个小的弹出窗口，显示说明应用程序中工具用途的单行文本。

[CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
支持扩展编辑控件或简单的日历界面控件，允许用户选择特定日期或时间值。

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
显示列的标题或标签。

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
支持允许用户选择日期的简单日历界面控件。

[CTabCtrl](reference/ctabctrl-class.md)<br/>
具有用户可单击的选项卡的控件，类似于笔记本中的分隔线。

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
允许用户创建一个热键组合，用户可以按此组合来快速执行操作。

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
当用户单击嵌入的链接时，呈现标记的文本并启动相应的应用程序。

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
提供 MFC 窗口中的 WebBrowser ActiveX 控件功能。

## <a name="related-classes"></a>相关类

[CImageList](reference/cimagelist-class.md)<br/>
提供 Windows 图像列表的功能。 图像列表将与列表控件和树控件一起使用。 它们还可以用于存储和存档一组大小相同的位图。

[CCtrlView](reference/cctrlview-class.md)<br/>
与 Windows 控件关联的所有视图的基类。 下面介绍了基于控件的视图。

[CEditView](reference/ceditview-class.md)<br/>
包含 Windows 标准编辑控件的视图。

[CRichEditView](reference/cricheditview-class.md)<br/>
包含 Windows rich edit 控件的视图。

[CListView](reference/clistview-class.md)<br/>
包含 Windows 列表控件的视图。

[CTreeView](reference/ctreeview-class.md)<br/>
包含 Windows 树控件的视图。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
