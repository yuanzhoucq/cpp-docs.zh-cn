---
title: "控件类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.control"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按钮, MFC 控件类"
  - "控件类"
  - "控件类, MFC"
  - "控件 [C++], MFC 控件类"
  - "控件 [MFC]"
  - "列表框, MFC 控件类"
  - "静态显示控件"
  - "文本, 控制输入"
  - "用户输入, MFC 控件类"
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 控件类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控件封装类范围从静态文本控件的标准 Windows 控件添加到控件树。  此外，MFC 提供一些新控件，包括按钮的位图以及控件条。  
  
 类名“**Ctrl**”结尾的控件是中的新 Windows 95 和 Windows NT 3.51 版。  
  
## 静态显示控件  
 [CStatic](../mfc/reference/cstatic-class.md)  
 静态显示窗口。  静态控件用于标记，将或分隔在对话框或窗口中其他控件"  它们还显示图形图像而不是文本或复选框。  
  
## 文本控件  
 [CEdit](../mfc/reference/cedit-class.md)  
 编辑 Text 控件窗口。  编辑控件用于接受用户输入的文本。  
  
 [CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)  
 支持操作的 Internet 协议 \(IP\) 地址一个编辑框。  
  
 [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)  
 用户可以输入和编辑文本的控件。  不同于由 `CEdit`封装的控件，为 Rich Edit 控件支持字符和段落格式和 OLE 对象。  
  
## 表示数字的控件  
 [CSliderCtrl](../mfc/reference/csliderctrl-class.md)  
 滑块包含的控件，用户移动选定值或值集。  
  
 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)  
 用户可以单击来递增或递减值的一对箭头按钮。  
  
 [CProgressCtrl](../mfc/reference/cprogressctrl-class.md)  
 从左到右显示逐渐填充指示操作进度的矩形。  
  
 [CScrollBar](../mfc/reference/cscrollbar-class.md)  
 滚动条控件窗口。  类提供一滚动条的功能，用作在对话框或窗口的控件，用户可以指定范围内的某个位置。  
  
## 按钮  
 [CButton](../mfc/reference/cbutton-class.md)  
 按钮控件窗口。  类提供一个按钮、复选框和单选按钮提供了一个编程接口在对话框或窗口。  
  
 [C位图按钮](../mfc/reference/cbitmapbutton-class.md)  
 使用位图的按钮而不是文本标题。  
  
## 列表  
 [CListBox](../mfc/reference/clistbox-class.md)  
 列表框控制窗口。  列表框显示用户可以显示和选择的项列表。  
  
 [C拖动列表框](../mfc/reference/cdraglistbox-class.md)  
 提供 Windows 列表框生成的功能；允许用户移动列表框项，例如文件名和字符串，在列表框中。  列表框提供此功能为项列表是有用的 \(按字母顺序之外，如包括路径名或文件的项目中。  
  
 [CComboBox](../mfc/reference/ccombobox-class.md)  
 组合框控件窗口。  组合框包含一个编辑控件以及列表框。  
  
 [C组合框前](../mfc/reference/ccomboboxex-class.md)  
 通过为图像列表提供支持扩展组合框控件。  
  
 [C检查列表框](../mfc/reference/cchecklistbox-class.md)  
 单击每一项旁边显示项列表与复选框的，用户可以选中或清除。，  
  
 [CListCtrl](../mfc/reference/clistctrl-class.md)  
 显示项的集合，包括图标和标签的每个，某些文件类似于资源管理器右窗格。  
  
 [CTreeCtrl](../mfc/reference/ctreectrl-class.md)  
 图标显示一个分层列表，并将标签的一些文件类似于资源管理器左窗格。  
  
## 工具栏和状态栏  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具栏公共控件的功能。  大多数 MFC 程序使用 [CToolBar](../mfc/reference/ctoolbar-class.md) 而不是此类。  
  
 [CStatusBarCtrl（C状态栏按Ctrl）](../mfc/reference/cstatusbarctrl-class.md)  
 水平的 Windows，通常分为窗格，应用程序可在其中显示状态信息。  大多数 MFC 程序使用 [CStatusBar](../mfc/reference/cstatusbar-class.md) 而不是此类。  
  
## 混合控件  
 [CAnimateCtrl](../mfc/reference/canimatectrl-class.md)  
 显示简单的视频剪辑。  
  
 [CToolTipCtrl（C工具提示按Ctrl）](../mfc/reference/ctooltipctrl-class.md)  
 描述显示工具的用途单行文本。应用程序的小型弹出窗口。  
  
 [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)  
 支持扩展编辑控件或简单的日历控件接口，允许用户选择特定日期或时间值。  
  
 [C的头部Ctrl](../mfc/reference/cheaderctrl-class.md)  
 显示标题或列标签的。  
  
 [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)  
 支持允许用户选择日期的日历接口的简单控件。  
  
 [CTabCtrl](../mfc/reference/ctabctrl-class.md)  
 具有用户可以单击的选项卡的控件，类似于笔记本中的分隔。  
  
 [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)  
 允许用户创建一热组合键，用户可以按快速执行操作。  
  
 [CLinkCtrl](../mfc/reference/clinkctrl-class.md)  
 不同的文本 renders 和启动相应的应用程序，用户单击嵌入链接。  
  
 [CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)  
 提供 MFC 窗口中的 WebBrowser ActiveX 控件功能。  
  
## 相关类  
 [C图像列表](../mfc/reference/cimagelist-class.md)  
 提供 Windows 图像列表的功能。  图像列表与控件列表和树控件。  它们还可以用于存储和存档一组相同大小的位图。  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 所有基的类演示与 Windows 控件。  根据视图控件的下面。  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 包含一个标准 Windows 编辑控件的视图。  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 包含丰富 Windows 编辑控件的视图。  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Windows 包含一个列表控件的视图。  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 窗口包含一个树控件的视图。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)