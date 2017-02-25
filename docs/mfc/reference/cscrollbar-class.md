---
title: "CScrollBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CScrollBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件 [MFC], 滚动条"
  - "CScrollBar class"
  - "滚动条"
  - "SCROLLBAR window class"
  - "Windows common controls [C++], CScrollBar"
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CScrollBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows滚动条控件的功能。  
  
## 语法  
  
```  
class CScrollBar : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CScrollBar::CScrollBar](../Topic/CScrollBar::CScrollBar.md)|构造 `CScrollBar` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CScrollBar::Create](../Topic/CScrollBar::Create.md)|创建Windows滚动条并将它附加到 `CScrollBar` 对象。|  
|[CScrollBar::EnableScrollBar](../Topic/CScrollBar::EnableScrollBar.md)|启用或禁用滚动条的一个或两个箭头。|  
|[CScrollBar::GetScrollBarInfo](../Topic/CScrollBar::GetScrollBarInfo.md)|使用 `SCROLLBARINFO` 结构，检索有关滚动条的信息。|  
|[CScrollBar::GetScrollInfo](../Topic/CScrollBar::GetScrollInfo.md)|检索有关滚动条的信息。|  
|[CScrollBar::GetScrollLimit](../Topic/CScrollBar::GetScrollLimit.md)|检索滚动条的限制|  
|[CScrollBar::GetScrollPos](../Topic/CScrollBar::GetScrollPos.md)|检索滚动框中的当前位置。|  
|[CScrollBar::GetScrollRange](../Topic/CScrollBar::GetScrollRange.md)|检索特定滚动条的当前最小值和最大值滚动条位置。|  
|[CScrollBar::SetScrollInfo](../Topic/CScrollBar::SetScrollInfo.md)|设置有关滚动条的信息。|  
|[CScrollBar::SetScrollPos](../Topic/CScrollBar::SetScrollPos.md)|将滚动框中的当前位置。|  
|[CScrollBar::SetScrollRange](../Topic/CScrollBar::SetScrollRange.md)|设置特定滚动条的最小日期和最大位置值。|  
|[CScrollBar::ShowScrollBar](../Topic/CScrollBar::ShowScrollBar.md)|显示或隐藏滚动条。|  
  
## 备注  
 对两个步骤创建一个滚动条控件。  首先，调用构造函数 `CScrollBar` 构造 `CScrollBar` 对象，然后调用 [创建](../Topic/CScrollBar::Create.md) 成员函数创建Windows滚动条控件并将其附加到 `CScrollBar` 对象。  
  
 如果要创建在对话框中的一 `CScrollBar` 对象\(通过对话框资源\)，自动销毁 `CScrollBar`，当用户关闭对话框时。  
  
 如果在中创建的一 `CScrollBar` 对象，您可能还需要销毁它。  
  
 如果在堆栈上创建 `CScrollBar` 对象，自动销毁它。  使用 **new** 功能，如果要创建在堆的 `CScrollBar` 对象，则必须对对象的 **delete** 销毁它，当用户停止Windows滚动条时。  
  
 如果将在 `CScrollBar` 对象的任何内存，请重写 `CScrollBar` 析构函数进程分配。  
  
 有关使用 `CScrollBar`的相关信息，请参见 [控件](../../mfc/controls-mfc.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)