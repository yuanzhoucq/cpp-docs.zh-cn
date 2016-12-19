---
title: "CMFCHeaderCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCHeaderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCHeaderCtrl class"
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCHeaderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCHeaderCtrl` 选件类支持对标头控件的多个列。  
  
## 语法  
  
```  
class CMFCHeaderCtrl : public CHeaderCtrl  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCHeaderCtrl::CMFCHeaderCtrl](../Topic/CMFCHeaderCtrl::CMFCHeaderCtrl.md)|构造 `CMFCHeaderCtrl` 对象。|  
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCHeaderCtrl::EnableMultipleSort](../Topic/CMFCHeaderCtrl::EnableMultipleSort.md)|启用或禁用 *多列排序* 当前标头控件模式。|  
|[CMFCHeaderCtrl::GetColumnState](../Topic/CMFCHeaderCtrl::GetColumnState.md)|在升序或降序指示列是否未排序，或者排序。|  
|[CMFCHeaderCtrl::GetSortColumn](../Topic/CMFCHeaderCtrl::GetSortColumn.md)|检索第一个排序的列的从零开始的索引。标头控件的。|  
|`CMFCHeaderCtrl::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CMFCHeaderCtrl::IsAscending](../Topic/CMFCHeaderCtrl::IsAscending.md)|指示在标头控件的列是否在升序排序。|  
|[CMFCHeaderCtrl::IsDialogControl](../Topic/CMFCHeaderCtrl::IsDialogControl.md)|指示当前标头控件的父窗口是否为对话框。|  
|[CMFCHeaderCtrl::IsMultipleSort](../Topic/CMFCHeaderCtrl::IsMultipleSort.md)|指示当前标头控制是否在 *多个列排序* 模式。|  
|[CMFCHeaderCtrl::RemoveSortColumn](../Topic/CMFCHeaderCtrl::RemoveSortColumn.md)|从列表中移除指定的列排序列。|  
|[CMFCHeaderCtrl::SetSortColumn](../Topic/CMFCHeaderCtrl::SetSortColumn.md)|设置指定列的排序顺序。标头控件的。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCHeaderCtrl::OnDrawItem](../Topic/CMFCHeaderCtrl::OnDrawItem.md)|调用由框架绘制标头控件的列。|  
|[CMFCHeaderCtrl::OnDrawSortArrow](../Topic/CMFCHeaderCtrl::OnDrawSortArrow.md)|调用由框架绘制排序箭头。|  
|[CMFCHeaderCtrl::OnFillBackground](../Topic/CMFCHeaderCtrl::OnFillBackground.md)|调用framework加载标头控件的列的背景。|  
  
## 示例  
 下面的示例演示如何构造对象 `CMFCHeaderCtrl` 选件类，并且，如何启用 *多个列排序* 当前标头控件模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/CPP/cmfcheaderctrl-class_1.cpp)]  
  
## 备注  
 `CMFCHeaderCtrl` 选件类是在标头控件的列的排序箭头表示列排序。  使用 *多列排序* 模式，如果将父的列列表控件\([CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)\)可同时进行排序。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## 要求  
 **标头:** afxheaderctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)