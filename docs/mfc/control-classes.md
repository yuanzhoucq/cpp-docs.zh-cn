---
title: "控件类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.control
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 376fb3836d92a1fae348929a7faa49b44dfd866e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="control-classes"></a>控件类
控件类封装各种范围从静态文本控件到树控件的标准 Windows 控件。 此外，MFC 提供了一些新的控件，包括使用位图和控件条按钮。  
  
 其类名的结尾的控件"**Ctrl**"已在 Windows 95 和 Windows NT 版本 3.51 新。  
  
## <a name="static-display-controls"></a>静态显示控件  
 [CStatic](../mfc/reference/cstatic-class.md)  
 静态显示窗口。 静态控件用于框中，或单独的对话框或窗口中的其他控件标志。 它们还可能会显示图形图像而不是文本或框。  
  
## <a name="text-controls"></a>文本控件  
 [CEdit](../mfc/reference/cedit-class.md)  
 一个可编辑文本控件窗口。 编辑控件用于接受来自用户的文本输入。  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 支持的操作的 Internet 协议 (IP) 地址的编辑框。  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 一个用户可以输入和编辑文本的控件。 与控件封装在不同`CEdit`，rich edit 控件支持字符和段落格式设置和 OLE 对象。  
  
## <a name="controls-that-represent-numbers"></a>表示数字的控件  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 包含一个滑块，用户将移动以选择的值或组的值的控件。  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 箭头按钮对用户可以单击递增或递减值。  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 显示逐渐填充从左到右，以指示操作的进度的矩形。  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 滚动条控件窗口。 此类提供滚动条，以用作对话框或窗口中，通过该用户可以指定范围内的位置中的控件的功能。  
  
## <a name="buttons"></a>按钮  
 [CButton](../mfc/reference/cbutton-class.md)  
 按钮控件窗口。 此类提供下压按钮、 复选框，或在对话框或窗口中的单选按钮的编程接口。  
  
 [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
 一个具有一个位图，而不是文本标题按钮。  
  
## <a name="lists"></a>列表  
 [CListBox](../mfc/reference/clistbox-class.md)  
 列表框控件窗口。 列表框中显示用户可以查看和选择的项的列表。  
  
 [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
 提供 Windows 列表框; 的功能允许用户在列表框内移动文件名和字符串文本，如的列表框项。 使用这项功能的列表框可用于按字母顺序以外顺序中的项列表，如包括在项目中的路径名或文件。  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 组合框控件窗口。 组合框由编辑控件和列表框组成。  
  
 [CComboBoxEx](../mfc/reference/ccomboboxex-class.md)  
 通过为图像列表提供支持扩展组合框控件。  
  
 [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
 显示与该用户可以选中或清除，每个项旁边的复选框的项的列表。  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 显示的项，其中每个包括的一个图标和标签时，方式类似于右窗格中的文件资源管理器中的集合。  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 显示图标和标签排列方式类似于左窗格中的文件资源管理器中的分层的列表。  
  
## <a name="toolbars-and-status-bars"></a>工具栏和状态栏  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具栏公共控件的功能。 大多数 MFC 程序使用[CToolBar](../mfc/reference/ctoolbar-class.md)而不是此类。  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 水平窗口中，通常分为的窗格，应用程序可在其中显示状态信息。 大多数 MFC 程序使用[CStatusBar](../mfc/reference/cstatusbar-class.md)而不是此类。  
  
## <a name="miscellaneous-controls"></a>杂项控件  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 显示简单的视频剪辑。  
  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 显示的文本来描述应用程序中工具用途的单行一个小型弹出窗口。  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 支持扩展的编辑控件或一个简单的日历界面控件，允许用户选择特定日期或时间值。  
  
 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)  
 显示标题或列的标签。  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 支持一个简单的日历界面控件，它允许用户选择日期。  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 具有选项卡的用户可以单击，类似于笔记本中的分隔条的控件。  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 使用户能够创建热组合键，用户可以按操作更快地执行。  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 呈现标记向上文本，并启动相应的应用程序，当用户单击嵌入的链接。  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 提供 MFC 窗口中的 WebBrowser ActiveX 控件功能。  
  
## <a name="related-classes"></a>相关的类  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 提供 Windows 图像列表的功能。 图像列表将与列表控件和树控件一起使用。 它们还可以用于存储和存档一组大小相同的位图。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 与 Windows 控件关联的所有视图的基类。 基于控件的视图如下所述。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 一个包含 Windows 标准视图编辑控件。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 一个包含 Windows 丰富视图编辑控件。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 一个包含 Windows 列表控件的视图。  
  
 [Ctreeview 类](../mfc/reference/ctreeview-class.md)  
 一个包含 Windows 树控件的视图。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

