---
title: "CHeaderCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHeaderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeaderCtrl class"
  - "header controls, CHeaderCtrl class"
  - "Windows common controls [C++], CHeaderCtrl"
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CHeaderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows公共标头控件的功能。  
  
## 语法  
  
```  
class CHeaderCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CHeaderCtrl::CHeaderCtrl](../Topic/CHeaderCtrl::CHeaderCtrl.md)|构造 `CHeaderCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CHeaderCtrl::ClearAllFilters](../Topic/CHeaderCtrl::ClearAllFilters.md)|清除标头控件的所有筛选器。|  
|[CHeaderCtrl::ClearFilter](../Topic/CHeaderCtrl::ClearFilter.md)|清除标头控件的筛选器。|  
|[CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md)|创建一个标头控件并将它附加到 `CHeaderCtrl` 对象。|  
|[CHeaderCtrl::CreateDragImage](../Topic/CHeaderCtrl::CreateDragImage.md)|创建项目的图像的一个透明的版本。标头控件中。|  
|[CHeaderCtrl::CreateEx](../Topic/CHeaderCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个标头控件并将它附加到 `CListCtrl` 对象。|  
|[CHeaderCtrl::DeleteItem](../Topic/CHeaderCtrl::DeleteItem.md)|从标头控件中删除项。|  
|[CHeaderCtrl::DrawItem](../Topic/CHeaderCtrl::DrawItem.md)|绘制标头控件中的指定项。|  
|[CHeaderCtrl::EditFilter](../Topic/CHeaderCtrl::EditFilter.md)|编辑标头控件的指定筛选器的开头。|  
|[CHeaderCtrl::GetBitmapMargin](../Topic/CHeaderCtrl::GetBitmapMargin.md)|检索位图边距的宽度。标头控件的。|  
|[CHeaderCtrl::GetFocusedItem](../Topic/CHeaderCtrl::GetFocusedItem.md)|获取项的标识符在具有焦点的当前标头控件的。|  
|[CHeaderCtrl::GetImageList](../Topic/CHeaderCtrl::GetImageList.md)|检索图像的处理列出用于绘制标头项。标头控件。|  
|[CHeaderCtrl::GetItem](../Topic/CHeaderCtrl::GetItem.md)|检索某个项的信息。标头控件。|  
|[CHeaderCtrl::GetItemCount](../Topic/CHeaderCtrl::GetItemCount.md)|检索项的计数在标头控件的。|  
|[CHeaderCtrl::GetItemDropDownRect](../Topic/CHeaderCtrl::GetItemDropDownRect.md)|获取指定的下拉式按钮的边框信息。标头控件。|  
|[CHeaderCtrl::GetItemRect](../Topic/CHeaderCtrl::GetItemRect.md)|检索特定项的边框在标头控件。|  
|[CHeaderCtrl::GetOrderArray](../Topic/CHeaderCtrl::GetOrderArray.md)|检索项目从左到右的顺序。标头控件的。|  
|[CHeaderCtrl::GetOverflowRect](../Topic/CHeaderCtrl::GetOverflowRect.md)|获取溢出按钮的边框当前标头控件的。|  
|[CHeaderCtrl::HitTest](../Topic/CHeaderCtrl::HitTest.md)|确定哪个标头项目，如果有，位于指定点。|  
|[CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md)|插入一个新项。标头控件。|  
|[CHeaderCtrl::Layout](../Topic/CHeaderCtrl::Layout.md)|检索一个标头控件的大小和位置在特定矩形中的。|  
|[CHeaderCtrl::OrderToIndex](../Topic/CHeaderCtrl::OrderToIndex.md)|检索基于其在标头控件的顺序的项的索引值。|  
|[CHeaderCtrl::SetBitmapMargin](../Topic/CHeaderCtrl::SetBitmapMargin.md)|设置位图边距的宽度。标头控件的。|  
|[CHeaderCtrl::SetFilterChangeTimeout](../Topic/CHeaderCtrl::SetFilterChangeTimeout.md)|将更改在筛选器特性和 `HDN_FILTERCHANGE` 通知发送的发生时间之间的超时间隔。|  
|[CHeaderCtrl::SetFocusedItem](../Topic/CHeaderCtrl::SetFocusedItem.md)|将焦点设置在当前标头控件的指定标头项目。|  
|[CHeaderCtrl::SetHotDivider](../Topic/CHeaderCtrl::SetHotDivider.md)|将标头项之间的分隔符指示标头项目的手动拖放。|  
|[CHeaderCtrl::SetImageList](../Topic/CHeaderCtrl::SetImageList.md)|分配图像列表。标头控件。|  
|[CHeaderCtrl::SetItem](../Topic/CHeaderCtrl::SetItem.md)|设置指定的项的属性。标头控件的。|  
|[CHeaderCtrl::SetOrderArray](../Topic/CHeaderCtrl::SetOrderArray.md)|设置项目从左到右的顺序。标头控件的。|  
  
## 备注  
 标头控件位于上通常确定设置文本或数字的列的窗口。  它包含每个列的标题，因此，它可以分成部件。  用户可以通过拖动分离部件将每一列的宽度的分隔符。  有关标头控件的说明，请参见 [标头控件](http://msdn.microsoft.com/library/windows/desktop/bb775238)。  
  
 此控件\(并 `CHeaderCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版和更高版本下的程序可用。  
  
 对于Windows 95或Internet Explorer 4.0公共控件添加的功能包括:  
  
-   标头项目自定义排序。  
  
-   标头项目拖放，重新排序的标头项目。  在创建 `CHeaderCtrl` 对象时，请使用 `HDS_DRAGDROP` 样式。  
  
-   标头列文本通常可以在列调整过程。  在创建 `CHeaderCtrl` 对象时，请使用 `HDS_FULLDRAG` 样式。  
  
-   标头快捷跟踪，显示标头项目，当指针悬停在它。  在创建 `CHeaderCtrl` 对象时，请使用 `HDS_HOTTRACK` 样式。  
  
-   图像列表支持。  标头项目可以包含在 `CImageList` 对象或文本存储的图像。  
  
 有关使用 `CHeaderCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CHeaderCtrl](../../mfc/using-cheaderctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## 要求  
 **标头:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CTabCtrl Class](../../mfc/reference/ctabctrl-class.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)