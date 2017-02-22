---
title: "CTreeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTreeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl class"
  - "directory lists"
  - "file lists [C++]"
  - "tree view controls"
ms.assetid: 96e20031-6161-4143-8c12-8d1816c66d90
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CTreeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见树视图控件的功能。  
  
## 语法  
  
```  
class CTreeCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CTreeCtrl::CTreeCtrl](../Topic/CTreeCtrl::CTreeCtrl.md)|构造 `CTreeCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTreeCtrl::Create](../Topic/CTreeCtrl::Create.md)|创建树视图控件并将它附加到 `CTreeCtrl` 对象。|  
|[CTreeCtrl::CreateDragImage](../Topic/CTreeCtrl::CreateDragImage.md)|创建指定的树视图的项拖动的位图。|  
|[CTreeCtrl::CreateEx](../Topic/CTreeCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个树控件并将它附加到 `CTreeCtrl` 对象。|  
|[CTreeCtrl::DeleteAllItems](../Topic/CTreeCtrl::DeleteAllItems.md)|删除在树视图控件中的所有项目。|  
|[CTreeCtrl::DeleteItem](../Topic/CTreeCtrl::DeleteItem.md)|删除在树视图控件的新项目。|  
|[CTreeCtrl::EditLabel](../Topic/CTreeCtrl::EditLabel.md)|就地编辑一个指定的树视图中的项。|  
|[CTreeCtrl::EndEditLabelNow](../Topic/CTreeCtrl::EndEditLabelNow.md)|移除在一个树视图项的标签的编辑操作在当前树视图控件的。|  
|[CTreeCtrl::EnsureVisible](../Topic/CTreeCtrl::EnsureVisible.md)|确保树视图项会显示在其树视图控件。|  
|[CTreeCtrl::Expand](../Topic/CTreeCtrl::Expand.md)|展开或折叠，指定的树视图项的子项。|  
|[CTreeCtrl::GetBkColor](../Topic/CTreeCtrl::GetBkColor.md)|检索该控件的当前背景色。|  
|[CTreeCtrl::GetCheck](../Topic/CTreeCtrl::GetCheck.md)|检索树控件项目的复选状态。|  
|[CTreeCtrl::GetChildItem](../Topic/CTreeCtrl::GetChildItem.md)|检索一个指定的树视图项的子级。|  
|[CTreeCtrl::GetCount](../Topic/CTreeCtrl::GetCount.md)|检索树项的数目与树视图控件。|  
|[CTreeCtrl::GetDropHilightItem](../Topic/CTreeCtrl::GetDropHilightItem.md)|检索拖放操作的目标。|  
|[CTreeCtrl::GetEditControl](../Topic/CTreeCtrl::GetEditControl.md)|检索使用的编辑控件中处理编辑器中指定的树视图项。|  
|[CTreeCtrl::GetExtendedStyle](../Topic/CTreeCtrl::GetExtendedStyle.md)|检索扩展样式当前树视图控件使用。|  
|[CTreeCtrl::GetFirstVisibleItem](../Topic/CTreeCtrl::GetFirstVisibleItem.md)|检索指定的树视图项目的第一个可见项。|  
|[CTreeCtrl::GetImageList](../Topic/CTreeCtrl::GetImageList.md)|检索图像的处理列出了与树视图控件。|  
|[CTreeCtrl::GetIndent](../Topic/CTreeCtrl::GetIndent.md)|从其父检索偏移量\(以像素为单位\)树视图项。|  
|[CTreeCtrl::GetInsertMarkColor](../Topic/CTreeCtrl::GetInsertMarkColor.md)|检索使用的颜色绘制树视图中插入标记。|  
|[CTreeCtrl::GetItem](../Topic/CTreeCtrl::GetItem.md)|检索一个指定的树视图项目的属性。|  
|[CTreeCtrl::GetItemData](../Topic/CTreeCtrl::GetItemData.md)|返回一个32位应用程序特定的值与项目。|  
|[CTreeCtrl::GetItemExpandedImageIndex](../Topic/CTreeCtrl::GetItemExpandedImageIndex.md)|检索图像的索引显示当前树视图控件的指定项目时在展开的状态。|  
|[CTreeCtrl::GetItemHeight](../Topic/CTreeCtrl::GetItemHeight.md)|检索树视图项的当前高度。|  
|[CTreeCtrl::GetItemImage](../Topic/CTreeCtrl::GetItemImage.md)|检索图像与项目。|  
|[CTreeCtrl::GetItemPartRect](../Topic/CTreeCtrl::GetItemPartRect.md)|检索一个指定项的指定部分的边框在当前树视图控件的。|  
|[CTreeCtrl::GetItemRect](../Topic/CTreeCtrl::GetItemRect.md)|检索树视图项的边框。|  
|[CTreeCtrl::GetItemState](../Topic/CTreeCtrl::GetItemState.md)|返回项目的状态。|  
|[CTreeCtrl::GetItemStateEx](../Topic/CTreeCtrl::GetItemStateEx.md)|检索指定项目的扩展的状态在当前树视图控件的。|  
|[CTreeCtrl::GetItemText](../Topic/CTreeCtrl::GetItemText.md)|返回项目的文本。|  
|[CTreeCtrl::GetLastVisibleItem](../Topic/CTreeCtrl::GetLastVisibleItem.md)|检索当前树视图控件中的最后一展开项。|  
|[CTreeCtrl::GetLineColor](../Topic/CTreeCtrl::GetLineColor.md)|检索树视图控件中当前行的颜色。|  
|[CTreeCtrl::GetNextItem](../Topic/CTreeCtrl::GetNextItem.md)|检索与指定关系的下一个树视图项。|  
|[CTreeCtrl::GetNextSiblingItem](../Topic/CTreeCtrl::GetNextSiblingItem.md)|检索指定的树视图中的项的下一个同级。|  
|[CTreeCtrl::GetNextVisibleItem](../Topic/CTreeCtrl::GetNextVisibleItem.md)|检索指定的树视图中的项的下一个可见项。|  
|[CTreeCtrl::GetParentItem](../Topic/CTreeCtrl::GetParentItem.md)|检索指定的树视图项的父级。|  
|[CTreeCtrl::GetPrevSiblingItem](../Topic/CTreeCtrl::GetPrevSiblingItem.md)|检索指定的树视图项的同级。|  
|[CTreeCtrl::GetPrevVisibleItem](../Topic/CTreeCtrl::GetPrevVisibleItem.md)|检索指定的树视图项的以前可见项。|  
|[CTreeCtrl::GetRootItem](../Topic/CTreeCtrl::GetRootItem.md)|检索指定的树视图项目的根。|  
|[CTreeCtrl::GetScrollTime](../Topic/CTreeCtrl::GetScrollTime.md)|检索树视图控件的最大滚动时间。|  
|[CTreeCtrl::GetSelectedCount](../Topic/CTreeCtrl::GetSelectedCount.md)|检索选定的项数在当前树视图控件的。|  
|[CTreeCtrl::GetSelectedItem](../Topic/CTreeCtrl::GetSelectedItem.md)|检索当前所选的树视图项。|  
|[CTreeCtrl::GetTextColor](../Topic/CTreeCtrl::GetTextColor.md)|检索控件中的当前文本颜色。|  
|[CTreeCtrl::GetToolTips](../Topic/CTreeCtrl::GetToolTips.md)|检索句柄树视图控件使用的子工具提示控件。|  
|[CTreeCtrl::GetVisibleCount](../Topic/CTreeCtrl::GetVisibleCount.md)|检索可见树项的数目与树视图控件。|  
|[CTreeCtrl::HitTest](../Topic/CTreeCtrl::HitTest.md)|返回游标的当前位置与 `CTreeCtrl` 对象相关。|  
|[CTreeCtrl::InsertItem](../Topic/CTreeCtrl::InsertItem.md)|插入新项树视图控件。|  
|[CTreeCtrl::ItemHasChildren](../Topic/CTreeCtrl::ItemHasChildren.md)|如果指定的项包含子项，返回非零。|  
|[CTreeCtrl::MapAccIdToItem](../Topic/CTreeCtrl::MapAccIdToItem.md)|映射指定的可访问性标识符处理对当前树视图控件的一个树视图项。|  
|[CTreeCtrl::MapItemToAccID](../Topic/CTreeCtrl::MapItemToAccID.md)|映射中指定的句柄在当前树视图控件的一个树视图项对辅助功能标识符。|  
|[CTreeCtrl::Select](../Topic/CTreeCtrl::Select.md)|选择，滚动到视图或重绘一个指定的树视图项。|  
|[CTreeCtrl::SelectDropTarget](../Topic/CTreeCtrl::SelectDropTarget.md)|重绘树项作为拖放操作的目标。|  
|[CTreeCtrl::SelectItem](../Topic/CTreeCtrl::SelectItem.md)|选择一个指定的树视图项。|  
|[CTreeCtrl::SelectSetFirstVisible](../Topic/CTreeCtrl::SelectSetFirstVisible.md)|选择一个指定的树视图项作为第一个可见项。|  
|[CTreeCtrl::SetAutoscrollInfo](../Topic/CTreeCtrl::SetAutoscrollInfo.md)|设置当前树视图控件的autoscroll速率。|  
|[CTreeCtrl::SetBkColor](../Topic/CTreeCtrl::SetBkColor.md)|设置控件的背景色。|  
|[CTreeCtrl::SetCheck](../Topic/CTreeCtrl::SetCheck.md)|设置树控件项目的复选状态。|  
|[CTreeCtrl::SetExtendedStyle](../Topic/CTreeCtrl::SetExtendedStyle.md)|设置当前树视图控件的扩展样式。|  
|[CTreeCtrl::SetImageList](../Topic/CTreeCtrl::SetImageList.md)|设置图像的处理列出了与树视图控件。|  
|[CTreeCtrl::SetIndent](../Topic/CTreeCtrl::SetIndent.md)|设置偏移量\(以像素为单位\)与其父的树视图项。|  
|[CTreeCtrl::SetInsertMark](../Topic/CTreeCtrl::SetInsertMark.md)|设置在树视图控件的插入标记。|  
|[CTreeCtrl::SetInsertMarkColor](../Topic/CTreeCtrl::SetInsertMarkColor.md)|设置用于的颜色绘制树视图中插入标记。|  
|[CTreeCtrl::SetItem](../Topic/CTreeCtrl::SetItem.md)|一个指定的树视图项目的属性。|  
|[CTreeCtrl::SetItemData](../Topic/CTreeCtrl::SetItemData.md)|将32位特定的值与项目。|  
|[CTreeCtrl::SetItemExpandedImageIndex](../Topic/CTreeCtrl::SetItemExpandedImageIndex.md)|设置图像的索引显示当前树视图控件的指定项目时在展开的状态。|  
|[CTreeCtrl::SetItemHeight](../Topic/CTreeCtrl::SetItemHeight.md)|设置树视图项的高度。|  
|[CTreeCtrl::SetItemImage](../Topic/CTreeCtrl::SetItemImage.md)|将图像与项目。|  
|[CTreeCtrl::SetItemState](../Topic/CTreeCtrl::SetItemState.md)|设置项的状态。|  
|[CTreeCtrl::SetItemStateEx](../Topic/CTreeCtrl::SetItemStateEx.md)|设置指定项目的扩展的状态在当前树视图控件的。|  
|[CTreeCtrl::SetItemText](../Topic/CTreeCtrl::SetItemText.md)|设置项目的文本。|  
|[CTreeCtrl::SetLineColor](../Topic/CTreeCtrl::SetLineColor.md)|设置树视图控件中当前行的颜色。|  
|[CTreeCtrl::SetScrollTime](../Topic/CTreeCtrl::SetScrollTime.md)|设置树视图控件的最大滚动时间。|  
|[CTreeCtrl::SetTextColor](../Topic/CTreeCtrl::SetTextColor.md)|设置控件的文本颜色。|  
|[CTreeCtrl::SetToolTips](../Topic/CTreeCtrl::SetToolTips.md)|设置树视图控件的子工具提示控件。|  
|[CTreeCtrl::ShowInfoTip](../Topic/CTreeCtrl::ShowInfoTip.md)|显示指定的信息提示在当前树视图控件。|  
|[CTreeCtrl::SortChildren](../Topic/CTreeCtrl::SortChildren.md)|排序特定父项的子级。|  
|[CTreeCtrl::SortChildrenCB](../Topic/CTreeCtrl::SortChildrenCB.md)|排序使用的项应用程序定义的排序功能特定父的子元素。|  
  
## 备注  
 “树视图控件”是显示分层列表项，例如在文档的标题，在索引的项或文件和目录磁盘上的窗口。  每个项目包括标签和可选数字复制的图像，因此，每个项目可能有子项列表与它。  通过单击项目，用户可以展开，然后折叠关联的列表子项。  
  
 此控件\(并 `CTreeCtrl` 选件类\)若要在运行Windows 98和Windows NT 4版下的程序可用和更高版本。  
  
 有关使用 `CTreeCtrl`的更多信息，请参见:  
  
-   [控件](../../mfc/controls-mfc.md)  
  
-   [使用CTreeCtrl](../../mfc/using-ctreectrl.md)  
  
-   在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的[树视图控件引用](http://msdn.microsoft.com/library/windows/desktop/bb759988)。  
  
-   知识库文章Q222905:HOWTO:显示CTreeCtrl的上下文菜单  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTreeCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例CMNCTRL1](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)