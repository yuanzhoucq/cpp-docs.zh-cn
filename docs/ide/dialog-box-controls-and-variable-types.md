---
title: 对话框控件和变量类型
ms.date: 11/04/2016
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
ms.openlocfilehash: efacd6382d5773c4c47896a99910d9fe9934397a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600108"
---
# <a name="dialog-box-controls-and-variable-types"></a>对话框控件和变量类型

可使用[添加成员变量向导](../ide/add-member-variable-wizard.md)，将成员变量添加到使用 MFC 创建的对话框控件中。 为其添加成员变量的控件类型决定了对话框中显示的选项。

下表介绍了 MFC 和[对话框编辑器](../windows/dialog-editor.md)中支持的所有对话框控件类型及其可用类型和值。

|控件|控件类型|控件变量类型|值变量类型|最小值/最大值（仅限值类型）|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|动画控件|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|无；仅控件|不可用|
|Button|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|无；仅控件|不可用|
|复选框|CHECK|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|最小值/最大值|
|组合框|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字符数|
|日期时间选择器控件|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值/最大值|
|编辑框|编辑|[CEdit](../mfc/reference/cedit-class.md)|`CString`、int、UINT、long、DWORD、float、double、BYTE、short、BOOL、`COleDateTime` 或 COleCurrency|最小值/最大值；某些支持最大字符数|
|热键控件|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|无；仅控件|不可用|
|列表框|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字符数|
|列表控件|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|无；仅控件|不可用|
|月历控件|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值/最大值|
|进度控件|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|无；仅控件|不可用|
|Rich Edit 2 控件|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字符数|
|Rich Edit 控件|RICHEDIT|`CRichEditCtrl`|`CString`|最大字符数|
|滚动条（垂直或水平）|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小值/最大值|
|Slider 控件|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小值/最大值|
|数值调节钮控件|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|无；仅控件|不可用|
|Tab 控件|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|无；仅控件|不可用|
|树控件|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|无；仅控件|不可用|

## <a name="see-also"></a>请参阅

[添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)