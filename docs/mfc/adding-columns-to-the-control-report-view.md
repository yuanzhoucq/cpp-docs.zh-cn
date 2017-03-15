---
title: "向控件添加列（报表视图） | Microsoft Docs"
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
  - "CListCtrl 类, 添加列"
  - "CListCtrl 类, 报告查看器"
  - "列 [C++], 添加到 CListCtrl"
  - "CListCtrl 类中报告视图"
  - "视图, 报表"
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 向控件添加列（报表视图）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下过程适用于或 [CListView](../mfc/reference/clistview-class.md) [CListCtrl](../mfc/reference/clistctrl-class.md) 对象。  
  
 在列表控件在报表视图时，列中显示，提供组织每个列表项控件各个子项方法。  此组织 \+ 实施使用在一列在列表控件以及列表控件项的关联子项之间的一对一对应的通信。  子项有关的更多信息，请参见 [向控件添加项](../mfc/adding-items-to-the-control.md)。  一个列表控件的示例。报表的视图。在 Windows 95 和 Windows 98 Explorer 的详细信息视图提供。  第一列列出文件夹文件、图标和标签。  其他列中列出文件大小，文件类型，最后更新日期，依此类推。  
  
 即使该列可以随时添加到某个 List 控件中，列可见，只有当控件具有将置的 `LVS_REPORT` 样式位时。  
  
 每个列的列标记并允许用户调整列关联的标题项 \(参见 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) 对象。  
  
 如果列表控件支持报表视图，需要向每条可能的子项的列在列表控件项。  通过使用 [LV\_COLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743) 结构然后调用添加列。[InsertColumn](../Topic/CListCtrl::InsertColumn.md) 在添加必要的列后面 \(有时引用标题项\)，则可以重新排列它们。属于嵌入的标题控件的成员函数和样式。  有关更多信息，请参见 [顺序标题控件的项](../mfc/ordering-items-in-the-header-control.md)。  
  
> [!NOTE]
>  如果列表控件创建具有 **LVS\_NOCOLUMNHEADER** 样式，任何尝试插入一列将被忽略。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)