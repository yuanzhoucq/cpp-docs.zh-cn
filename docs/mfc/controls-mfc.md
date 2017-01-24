---
title: "控件 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Windows 公共控件 [C++]"
  - "公共控件 [C++]"
  - "控件 [MFC]"
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 控件 (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控件是用户可与之交互以便输入或操作数据的对象。 它们通常显示在对话框中或工具栏上。 本主题介绍三种主要类型的控件：  
  
-   Windows 公共控件，包括所有者描述的控件  
  
-   ActiveX 控件  
  
-   由 Microsoft 基础类库 \(MFC\) 提供的其他控件类  
  
## Windows 公共控件  
 Windows 操作系统一直以来提供了许多 Windows 公共控件。 这些控件对象是可编程的，Visual C\+\+ 对话编辑器支持将其添加到你的对话框。 Microsoft 基础类库 \(MFC\) 提供封装各个控件的类，如表 [Windows 公共控件和 MFC 类](#_core_windows_common_controls_and_mfc_classes)所示。 （表中的某些项提供进一步描述它们的相关主题。 有关缺少主题的控件，请参阅 MFC 类的文档。）  
  
 类 [CWnd](../mfc/reference/cwnd-class.md) 是所有窗口类的基类，包括所有控件类。 以下环境支持 Windows 公共控件：  
  
-   Windows 95、Windows 98 和 Windows 2000  
  
-   Windows NT，3.51 版和更高版本  
  
-   Win32s，1.3 版（Visual C\+\+ 4.2 版和更高版本不支持 Win32s）  
  
 较旧的公共控件 — 复选框、组合框、编辑框、列表框、选项按钮、按键、滚动条控件和静态控件 — 都在早期版本的 Windows 中可用。  
  
## ActiveX 控件  
 ActiveX 控件（以前称为 OLE 控件）可在适用于 Windows 的应用程序的对话框中或在万维网上的 HTML 页面上使用。 有关详细信息，请参阅 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)。  
  
## 其他 MFC 控件类  
 除了封装所有 Windows 公共控件以及支持对你自己的 ActiveX 控件进行编程（或支持使用其他人提供的 ActiveX 控件）的类外，MFC 还提供下面这些属于自己的控件类：  
  
-   [CBitmapButton](../mfc/reference/cbitmapbutton-class.md)  
  
-   [CCheckListBox](../mfc/reference/cchecklistbox-class.md)  
  
-   [CDragListBox](../mfc/reference/cdraglistbox-class.md)  
  
##  <a name="_core_finding_information_about_windows_common_controls"></a> 查找有关 Windows 公共控件的信息  
 下表简要介绍每个 Windows 公共控件，包括控件的 MFC 包装类。  
  
### Windows 公共控件和 MFC 类  
  
|控件|MFC 类|描述|Windows 95 中的新增功能？|  
|--------|-----------|--------|------------------------|  
|[动画](../mfc/using-canimatectrl.md)|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|将显示 AVI 视频剪辑的连续帧|是|  
|按钮|[CButton](../mfc/reference/cbutton-class.md)|可导致操作的按键；也用于复选框、单选按钮和分组框。|No|  
|组合框|[CComboBox](../mfc/reference/ccombobox-class.md)|编辑框和列表框的组合|No|  
|[日期和时间选择器](../mfc/using-cdatetimectrl.md)|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|允许用户选择特定日期或时间值|是|  
|编辑框|[CEdit](../mfc/reference/cedit-class.md)|用于输入文本的框|No|  
|[扩展组合框](../mfc/using-ccomboboxex.md)|[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)|可显示图像的组合框控件|是|  
|[标题](../mfc/using-cheaderctrl.md)|[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)|在文本列上显示的按钮；控制显示文本的宽度|是|  
|[热键](../mfc/using-chotkeyctrl.md)|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|使用户能够创建“热键”快速执行操作的窗口|是|  
|[图像列表](../mfc/using-cimagelist.md)|[CImageList](../mfc/reference/cimagelist-class.md)|用于管理大型图标集或位图集的图像集合（图像列表不是控件；它支持由其他控件使用的列表）|是|  
|[list](../mfc/using-clistctrl.md)|[CListCtrl](../mfc/reference/clistctrl-class.md)|显示带有图标的文本列表的窗口|是|  
|列表框|[CListBox](../mfc/reference/clistbox-class.md)|包含字符串列表的框|No|  
|[月历](../mfc/using-cmonthcalctrl.md)|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|显示日期信息的控件|是|  
|[进度](../mfc/using-cprogressctrl.md)|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|指示较长操作进度的窗口|是|  
|[rebar](../mfc/using-crebarctrl.md)|[CRebarCtrl](../mfc/reference/crebarctrl-class.md)|包含控件形式的其他子窗口的工具栏|是|  
|[rich edit](../mfc/using-cricheditctrl.md)|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|用户可在其中进行字符和段落格式编辑的窗口（请参阅[与 Rich Edit 控件相关的类](../mfc/classes-related-to-rich-edit-controls.md)）|是|  
|滚动条|[CScrollBar](../mfc/reference/cscrollbar-class.md)|用作对话框内（而非窗口上）控件的滚动条|No|  
|[滑块](../mfc/using-csliderctrl.md)|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|包含具有可选刻度线的滑块控件的窗口|是|  
|[数值调节钮](../mfc/using-cspinbuttonctrl.md)|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|用户可通过单击来增加或减少值的箭头按钮对|是|  
|静态文本|[CStatic](../mfc/reference/cstatic-class.md)|为其他控件加标签的文本|No|  
|[状态栏](../mfc/using-cstatusbarctrl.md)|[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)|显示状态信息的窗口，类似于 MFC 类 `CStatusBar`|是|  
|[选项卡](../mfc/using-ctabctrl.md)|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|类似于笔记本中的分割线；用在“选项卡对话框”或属性表中|是|  
|[工具栏](../mfc/using-ctoolbarctrl.md)|[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)|带有生成命令按钮的窗口，类似于 MFC 类 `CToolBar`|是|  
|[工具提示](../mfc/using-ctooltipctrl.md)|[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)|描述工具栏按钮或其他工具用途的小型弹出窗口|是|  
|[树](../mfc/using-ctreectrl.md)|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|显示项的分层列表的窗口|是|  
  
### 你想进一步了解什么？  
  
-   单个控件：请参阅本主题中表 [Windows 公共控件与 MFC 类](#_core_windows_common_controls_and_mfc_classes)，了解所有控件的链接。  
  
-   [创建和使用控件](../mfc/making-and-using-controls.md)  
  
-   [使用对话框编辑器添加控件](../mfc/using-the-dialog-editor-to-add-controls.md)  
  
-   [手动添加控件到对话框](../mfc/adding-controls-by-hand.md)  
  
-   [从 MFC 控件类派生控件类](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [将公共控件用作子窗口](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [来自公共控件的通知](../mfc/receiving-notification-from-common-controls.md)  
  
-   [Add common controls to a dialog box（将公共控件添加到对话框）](../mfc/using-common-controls-in-a-dialog-box.md)。  
  
-   [从标准 Windows 控件派生控件](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [访问类型安全的对话框控件](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [接收来自公共控件的通知消息](../mfc/receiving-notification-from-common-controls.md)  
  
-   [示例](../mfc/common-control-sample-list.md)  
  
 有关 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 中 Windows 公共控件的信息，请参阅[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)。  
  
## 请参阅  
 [用户界面元素](../mfc/user-interface-elements-mfc.md)   
 [Dialog Editor](../mfc/dialog-editor.md)