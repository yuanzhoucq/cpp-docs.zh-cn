---
title: "CTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabCtrl class"
  - "CTabCtrl class, 公共控件"
  - "选项卡控件"
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常用的选项控件的功能。  
  
## 语法  
  
```  
class CTabCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CTabCtrl::CTabCtrl](../Topic/CTabCtrl::CTabCtrl.md)|构造 `CTabCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTabCtrl::AdjustRect](../Topic/CTabCtrl::AdjustRect.md)|计算选项卡控件的生成显示区域窗口矩形或计算将对应于特定的显示区域的窗口矩形。|  
|[CTabCtrl::Create](../Topic/CTabCtrl::Create.md)|创建一个选项卡控件并将它附加到 `CTabCtrl` 对象的实例。|  
|[CTabCtrl::CreateEx](../Topic/CTabCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个选项卡控件并将它附加到 `CTabCtrl` 对象的实例。|  
|[CTabCtrl::DeleteAllItems](../Topic/CTabCtrl::DeleteAllItems.md)|从的选项卡控件中移除所有项。|  
|[CTabCtrl::DeleteItem](../Topic/CTabCtrl::DeleteItem.md)|从的选项卡控件移除项。|  
|[CTabCtrl::DeselectAll](../Topic/CTabCtrl::DeselectAll.md)|重置在选项卡控件的项目中，清除按下的任何名称。|  
|[CTabCtrl::DrawItem](../Topic/CTabCtrl::DrawItem.md)|绘制选项卡控件的指定项目。|  
|[CTabCtrl::GetCurFocus](../Topic/CTabCtrl::GetCurFocus.md)|检索与tab控件的当前焦点的选项。|  
|[CTabCtrl::GetCurSel](../Topic/CTabCtrl::GetCurSel.md)|确定在选项卡控件的当前选定的选项。|  
|[CTabCtrl::GetExtendedStyle](../Topic/CTabCtrl::GetExtendedStyle.md)|检索为选项卡控件是当前正在使用的扩展样式。|  
|[CTabCtrl::GetImageList](../Topic/CTabCtrl::GetImageList.md)|检索图像列表与tab控件。|  
|[CTabCtrl::GetItem](../Topic/CTabCtrl::GetItem.md)|检索有关可选的信息在选项卡控件。|  
|[CTabCtrl::GetItemCount](../Topic/CTabCtrl::GetItemCount.md)|检索选项卡数在选项卡控件的。|  
|[CTabCtrl::GetItemRect](../Topic/CTabCtrl::GetItemRect.md)|检索一个选项的边框在选项卡控件。|  
|[CTabCtrl::GetItemState](../Topic/CTabCtrl::GetItemState.md)|检索指示的选项卡控件项的状态。|  
|[CTabCtrl::GetRowCount](../Topic/CTabCtrl::GetRowCount.md)|检索当前行数选项在选项卡控件的。|  
|[CTabCtrl::GetToolTips](../Topic/CTabCtrl::GetToolTips.md)|检索工具提示控件中处理与tab控件。|  
|[CTabCtrl::HighlightItem](../Topic/CTabCtrl::HighlightItem.md)|设置选项卡项的突出显示状态。|  
|[CTabCtrl::HitTest](../Topic/CTabCtrl::HitTest.md)|确定哪个选项，如果有，在指定的屏幕位置。|  
|[CTabCtrl::InsertItem](../Topic/CTabCtrl::InsertItem.md)|插入新选项卡在选项卡控件。|  
|[CTabCtrl::RemoveImage](../Topic/CTabCtrl::RemoveImage.md)|从的选项卡控件的图像移除图像列表。|  
|[CTabCtrl::SetCurFocus](../Topic/CTabCtrl::SetCurFocus.md)|将焦点设置在选项卡控件的指定选项。|  
|[CTabCtrl::SetCurSel](../Topic/CTabCtrl::SetCurSel.md)|选择在选项卡控件的一个选项。|  
|[CTabCtrl::SetExtendedStyle](../Topic/CTabCtrl::SetExtendedStyle.md)|设置选项卡控件的扩展样式。|  
|[CTabCtrl::SetImageList](../Topic/CTabCtrl::SetImageList.md)|分配图像列表与选项卡控件。|  
|[CTabCtrl::SetItem](../Topic/CTabCtrl::SetItem.md)|设置某些或所有选项卡的属性。|  
|[CTabCtrl::SetItemExtra](../Topic/CTabCtrl::SetItemExtra.md)|设置字节数每个用于在选项卡控件的应用程序定义的数据保留的选项。|  
|[CTabCtrl::SetItemSize](../Topic/CTabCtrl::SetItemSize.md)|设置项目的宽度和高度。|  
|[CTabCtrl::SetItemState](../Topic/CTabCtrl::SetItemState.md)|设置指示的选项卡控件项的状态。|  
|[CTabCtrl::SetMinTabWidth](../Topic/CTabCtrl::SetMinTabWidth.md)|设置项目的最小宽度在选项卡控件的。|  
|[CTabCtrl::SetPadding](../Topic/CTabCtrl::SetPadding.md)|在每个选项的图标和标签设置周围的空间量\(空白\)在选项卡控件。|  
|[CTabCtrl::SetToolTips](../Topic/CTabCtrl::SetToolTips.md)|分配工具提示控件到选项卡控件。|  
  
## 备注  
 “选项”控件类似于笔记本中的分隔卡或档案柜的标签。  通过使用选项卡控件，应用程序可以为窗口或对话框的相同区域定义多个页。  每页包括一组信息或应用程序显示控件的一组用户何时选择相应的选项。  选项卡控件的一种特殊类型的显示类似于按钮的选项。  单击按钮应立即执行命令而不是显示页。  
  
 此控件\(并 `CTabCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 有关使用 `CTabCtrl`的更多信息，请参见 [控件](../../mfc/controls-mfc.md) 和 [使用CTabCtrl](../../mfc/using-ctabctrl.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CHeaderCtrl Class](../../mfc/reference/cheaderctrl-class.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)