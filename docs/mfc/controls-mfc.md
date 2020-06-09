---
title: 控件 (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC]
- common controls [MFC]
- controls [MFC]
ms.assetid: b2842884-6435-4b8f-933b-21671bf8af95
ms.openlocfilehash: accbee66cdee4e7b849da2b034d253b1c206d8f1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617184"
---
# <a name="controls-mfc"></a>控件 (MFC)

控件是用户可与之交互以便输入或操作数据的对象。 它们通常显示在对话框中或工具栏上。 本主题介绍三种主要类型的控件：

- Windows 公共控件，包括所有者描述的控件

- ActiveX 控件

- 由 Microsoft 基础类库 (MFC) 提供的其他控件类

## <a name="windows-common-controls"></a>Windows 公共控件

Windows 操作系统一直以来提供了许多 Windows 公共控件。 这些控件对象是可编程的，Visual C++ 对话编辑器支持将其添加到你的对话框。 Microsoft 基础类库 (MFC) 提供封装各个控件的类，如表 [Windows 公共控件和 MFC 类](#_core_windows_common_controls_and_mfc_classes)所示。 （表中的某些项提供进一步描述它们的相关主题。 有关缺少主题的控件，请参阅 MFC 类的文档。）

类 [CWnd](reference/cwnd-class.md) 是所有窗口类的基类，包括所有控件类。

## <a name="activex-controls"></a>ActiveX 控件

ActiveX 控件（以前称为 OLE 控件）可在适用于 Windows 的应用程序的对话框中或在万维网上的 HTML 页面上使用。 有关详细信息，请参阅[MFC ActiveX 控件](mfc-activex-controls.md)。

## <a name="other-mfc-control-classes"></a>其他 MFC 控件类

除了封装所有 Windows 公共控件以及支持对你自己的 ActiveX 控件进行编程（或支持使用其他人提供的 ActiveX 控件）的类外，MFC 还提供下面这些属于自己的控件类：

- [CBitmapButton](reference/cbitmapbutton-class.md)

- [CCheckListBox](reference/cchecklistbox-class.md)

- [CDragListBox](reference/cdraglistbox-class.md)

## <a name="finding-information-about-windows-common-controls"></a><a name="_core_finding_information_about_windows_common_controls"></a> 查找有关 Windows 公共控件的信息

下表简要介绍每个 Windows 公共控件，包括控件的 MFC 包装类。

### <a name="windows-common-controls-and-mfc-classes"></a><a name="_core_windows_common_controls_and_mfc_classes"></a>Windows 公共控件和 MFC 类

|控制|MFC 类|描述|Windows 95 中的新增项|
|-------------|---------------|-----------------|------------------------|
|[效果](using-canimatectrl.md)|[CAnimateCtrl](reference/canimatectrl-class.md)|将显示 AVI 视频剪辑的连续帧|是|
|button|[CButton](reference/cbutton-class.md)|可导致操作的按键；也用于复选框、单选按钮和分组框。|否|
|组合框|[CComboBox](reference/ccombobox-class.md)|编辑框和列表框的组合|否|
|[日期和时间选择器](using-cdatetimectrl.md)|[CDateTimeCtrl](reference/cdatetimectrl-class.md)|允许用户选择特定日期或时间值|是|
|编辑框|[CEdit](reference/cedit-class.md)|用于输入文本的框|否|
|[扩展组合框](using-ccomboboxex.md)|[CComboBoxEx](reference/ccomboboxex-class.md)|可显示图像的组合框控件|是|
|[标头](using-cheaderctrl.md)|[CHeaderCtrl](reference/cheaderctrl-class.md)|在文本列上显示的按钮；控制显示文本的宽度|是|
|[热键](using-chotkeyctrl.md)|[CHotKeyCtrl](reference/chotkeyctrl-class.md)|使用户能够创建“热键”快速执行操作的窗口|是|
|[图像列表](using-cimagelist.md)|[CImageList](reference/cimagelist-class.md)|用于管理大型图标集或位图集的图像集合（图像列表不是控件；它支持由其他控件使用的列表）|是|
|[list](using-clistctrl.md)|[CListCtrl](reference/clistctrl-class.md)|显示带有图标的文本列表的窗口|是|
|列表框|[CListBox](reference/clistbox-class.md)|包含字符串列表的框|否|
|[月历](using-cmonthcalctrl.md)|[CMonthCalCtrl](reference/cmonthcalctrl-class.md)|显示日期信息的控件|是|
|[进度](using-cprogressctrl.md)|[CProgressCtrl](reference/cprogressctrl-class.md)|指示较长操作进度的窗口|是|
|[rebar](using-crebarctrl.md)|[CRebarCtrl](reference/crebarctrl-class.md)|包含控件形式的其他子窗口的工具栏|是|
|[rich edit](using-cricheditctrl.md)|[CRichEditCtrl](reference/cricheditctrl-class.md)|用户可在其中进行字符和段落格式编辑的窗口（请参阅 [与 Rich Edit 控件相关的类](classes-related-to-rich-edit-controls.md)）|是|
|滚动条|[CScrollBar](reference/cscrollbar-class.md)|用作对话框内（而非窗口上）控件的滚动条|否|
|[滑动](using-csliderctrl.md)|[CSliderCtrl](reference/csliderctrl-class.md)|包含具有可选刻度线的滑块控件的窗口|是|
|[数值调节钮](using-cspinbuttonctrl.md)|[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)|用户可通过单击来增加或减少值的箭头按钮对|是|
|静态文本|[CStatic](reference/cstatic-class.md)|为其他控件加标签的文本|否|
|[状态栏](using-cstatusbarctrl.md)|[CStatusBarCtrl](reference/cstatusbarctrl-class.md)|显示状态信息的窗口，类似于 MFC 类 `CStatusBar`|是|
|["选项卡](using-ctabctrl.md)|[CTabCtrl](reference/ctabctrl-class.md)|类似于笔记本中的分割线；用在“选项卡对话框”或属性表中|是|
|[toolbar](using-ctoolbarctrl.md)|[CToolBarCtrl](reference/ctoolbarctrl-class.md)|带有生成命令按钮的窗口，类似于 MFC 类 `CToolBar`|是|
|[工具提示](using-ctooltipctrl.md)|[CToolTipCtrl](reference/ctooltipctrl-class.md)|描述工具栏按钮或其他工具用途的小型弹出窗口|是|
|[tree](using-ctreectrl.md)|[CTreeCtrl](reference/ctreectrl-class.md)|显示项的分层列表的窗口|是|

### <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- 单个控件：请参阅本主题中表 [Windows 公共控件与 MFC 类](#_core_windows_common_controls_and_mfc_classes) ，了解所有控件的链接。

- [创建和使用控件](making-and-using-controls.md)

- [使用对话框编辑器添加控件](using-the-dialog-editor-to-add-controls.md)

- [手动添加控件到对话框](adding-controls-by-hand.md)

- [从 MFC 控件类派生控件类](deriving-controls-from-a-standard-control.md)

- [将公共控件用作子窗口](using-a-common-control-as-a-child-window.md)

- [来自公共控件的通知](receiving-notification-from-common-controls.md)

- [Add common controls to a dialog box（将公共控件添加到对话框）](using-common-controls-in-a-dialog-box.md)。

- [从标准 Windows 控件派生控件](deriving-controls-from-a-standard-control.md)

- [访问类型安全的对话框控件](type-safe-access-to-controls-in-a-dialog-box.md)

- [接收来自公共控件的通知消息](receiving-notification-from-common-controls.md)

- [示例](common-control-sample-list.md)

有关 Windows SDK 中的 Windows 公共控件的信息，请参阅[公共控件](/windows/win32/Controls/common-controls-intro)。

## <a name="see-also"></a>另请参阅

[用户界面元素](user-interface-elements-mfc.md)<br/>
[对话框编辑器](../windows/dialog-editor.md)
