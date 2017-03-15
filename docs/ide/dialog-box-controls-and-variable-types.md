---
title: "对话框控件和变量类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "对话框控件, 成员变量"
  - "对话框控件, 变量类型"
  - "变量, 对话框控件成员变量"
ms.assetid: f9cd9cea-45a6-4349-8358-e5efbcdcff76
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 对话框控件和变量类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用[添加成员变量向导](../ide/add-member-variable-wizard.md)将成员变量添加到用 MFC 创建的对话框控件。  为其添加成员变量的控件类型决定出现在对话框中的选项。  
  
 下表描述 MFC 和[对话框编辑器](../mfc/dialog-editor.md)中支持的所有对话框控件类型及其可用的类型和值。  
  
|控件|控件类型|控件变量类型|值变量类型|最小值\/最大值（仅限值类型）|  
|--------|----------|------------|-----------|---------------------|  
|动画控件|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|无；仅为控件|不可用|  
|Button|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|无；仅为控件|不可用|  
|Check box|CHECK|[CButton](../mfc/reference/cbutton-class.md)|**BOOL**|最小值\/最大值|  
|Combo box|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|最大字符数|  
|日期时间选择器 \(Date Time Picker\) 控件|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|最小值\/最大值|  
|编辑框|EDIT|[CEdit](../mfc/reference/cedit-class.md)|`CString`、int、UINT、long、DWORD、float、double、BYTE、short、BOOL、`COleDateTime` 或 **COleCurrency**|最小值\/最大值；某些支持最大字符数|  
|热键 \(Hot Key\) 控件|msctls\_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|无；仅为控件|不可用|  
|列表框|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|最大字符数|  
|List 控件|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|无；仅为控件|不可用|  
|月历控件 \(Month Calendar Control\)|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|最小值\/最大值|  
|进度控件|msctls\_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|无；仅为控件|不可用|  
|Rich Edit 2.0 控件|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|最大字符数|  
|Rich Edit 控件|RICHEDIT|`CRichEditCtrl`|`CString`|最大字符数|  
|滚动条 \(Scroll Bar\)（垂直或水平）|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|最小值\/最大值|  
|滑块控件 \(Slider Control\)|msctls\_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|最小值\/最大值|  
|数值调节钮控件 \(Spin Control\)|msctls\_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|无；仅为控件|不可用|  
|选项卡控件 \(Tab Control\)|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|无；仅为控件|不可用|  
|树控件 \(Tree Control\)|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|无；仅为控件|不可用|  
  
## 请参阅  
 [添加成员变量](../ide/adding-a-member-variable-visual-cpp.md)