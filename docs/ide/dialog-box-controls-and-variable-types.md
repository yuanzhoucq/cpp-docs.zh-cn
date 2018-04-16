---
title: "对话框控件和变量类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 744b9da2db456a72ed386806d8a4aa34c5942f69
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-box-controls-and-variable-types"></a>对话框控件和变量类型
你可以使用[添加成员变量向导](../ide/add-member-variable-wizard.md)将成员变量添加到对话框控件使用 MFC 创建。 为其添加成员变量的控件的类型确定显示在对话框中的选项。  
  
 下表描述在 MFC 中受支持的所有对话框框控件类型和[对话框编辑器](../windows/dialog-editor.md)，及其可用类型和值。  
  
|控件|控件类型|控件变量类型|值的变量类型|最小/最大值 （只是值类型）|  
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|  
|动画控件|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|None;仅控件|不可用|  
|Button|按钮|[CButton](../mfc/reference/cbutton-class.md)|None;仅控件|不可用|  
|复选框|检查|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|最小值/最大值|  
|组合框|组合框|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字符数|  
|日期时间选取器控件|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值/最大值|  
|编辑框|编辑|[CEdit](../mfc/reference/cedit-class.md)|`CString`int、 UINT、 long、 DWORD，float、 double、 字节，简单地说，BOOL `COleDateTime`，或**COleCurrency**|最小值/最大值;某些支持最多个字符|  
|热键控件|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|None;仅控件|不可用|  
|列表框|列表框|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字符数|  
|列表控件|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|None;仅控件|不可用|  
|月历控件|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值/最大值|  
|进度控件|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|None;仅控件|不可用|  
|丰富编辑 2 控件|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字符数|  
|Rich Edit 控件|RICHEDIT|`CRichEditCtrl`|`CString`|最大字符数|  
|（垂直或水平滚动条|滚动条|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小值/最大值|  
|Slider 控件|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小值/最大值|  
|数值调节钮控件|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|None;仅控件|不可用|  
|Tab 控件|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|None;仅控件|不可用|  
|树控件|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|None;仅控件|不可用|  
  
## <a name="see-also"></a>请参阅  
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)