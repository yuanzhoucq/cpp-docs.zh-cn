---
title: "CMFCListCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCListCtrl class"
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CMFCListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCListCtrl` 选件类通过支持 [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md)的高级标头控件功能扩展 [CListCtrl Class](../../mfc/reference/clistctrl-class.md) 选件类的功能。  
  
## 语法  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCListCtrl::EnableMarkSortedColumn](../Topic/CMFCListCtrl::EnableMarkSortedColumn.md)|启用能够用不同的背景色的排序的列。|  
|[CMFCListCtrl::EnableMultipleSort](../Topic/CMFCListCtrl::EnableMultipleSort.md)|启用多个排序模式。|  
|[CMFCListCtrl::GetHeaderCtrl](../Topic/CMFCListCtrl::GetHeaderCtrl.md)|返回对带下划线的标头控件。|  
|[CMFCListCtrl::IsMultipleSort](../Topic/CMFCListCtrl::IsMultipleSort.md)|检查列表控件是否在多个排序模式。|  
|[CMFCListCtrl::OnCompareItems](../Topic/CMFCListCtrl::OnCompareItems.md)|调用由框架，它在必须比较时两个列表控件项目。|  
|[CMFCListCtrl::OnGetCellBkColor](../Topic/CMFCListCtrl::OnGetCellBkColor.md)|调用由框架，则必须确定单个单元格的背景色。|  
|[CMFCListCtrl::OnGetCellFont](../Topic/CMFCListCtrl::OnGetCellFont.md)|调用由框架，则必须获取绘制的单元格的字体。|  
|[CMFCListCtrl::OnGetCellTextColor](../Topic/CMFCListCtrl::OnGetCellTextColor.md)|调用由框架，则必须确定单个单元格的文本颜色。|  
|[CMFCListCtrl::RemoveSortColumn](../Topic/CMFCListCtrl::RemoveSortColumn.md)|从排序的列列表中移除对列进行排序。|  
|[CMFCListCtrl::SetSortColumn](../Topic/CMFCListCtrl::SetSortColumn.md)|设置当前排序的列和排序顺序。|  
|[CMFCListCtrl::Sort](../Topic/CMFCListCtrl::Sort.md)|排序列表控件。|  
  
## 备注  
 `CMFCListCtrl` 为 [CListCtrl Class](../../mfc/reference/clistctrl-class.md) 选件类提供了两种增强功能。  首先，它表示列排序是一个可用选项通过自动绘制该标头的排序箭头。  其次，它支持同时对多个列中的数据。  
  
## 示例  
 下面的示例在 `CMFCListCtrl` 选件类演示如何使用各种方法。  此示例演示如何创建列表控件，插入列，插入项，请将项目的文本，并设置列表控件的字体。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/CPP/cmfclistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/CPP/cmfclistctrl-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
## 要求  
 **标头:** afxlistctrl.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)