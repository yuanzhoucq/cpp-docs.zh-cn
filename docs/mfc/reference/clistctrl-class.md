---
title: "CListCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListCtrl 类"
  - "list view controls"
  - "list view controls, CListCtrl 类"
  - "LVS_ICON"
  - "LVS_LIST"
  - "LVS_REPORT"
  - "LVS_SMALLICON"
  - "Windows common controls [C++], CListCtrl"
ms.assetid: fe08a1ca-4b05-4ff7-a12a-ee4c765a2197
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装功能“列表视图控件，”显示的项集合包含图标\(从图像列表\)和标签的每个。  
  
## 语法  
  
```  
class CListCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CListCtrl::CListCtrl](../Topic/CListCtrl::CListCtrl.md)|构造 `CListCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CListCtrl::ApproximateViewRect](../Topic/CListCtrl::ApproximateViewRect.md)|确定需要的宽度和高度显示列表视图控件中的项。|  
|[CListCtrl::Arrange](../Topic/CListCtrl::Arrange.md)|对齐网格中的项目。|  
|[CListCtrl::CancelEditLabel](../Topic/CListCtrl::CancelEditLabel.md)|取消编辑操作的项文本。|  
|[CListCtrl::Create](../Topic/CListCtrl::Create.md)|创建一个列表控件并将它附加到 `CListCtrl` 对象。|  
|[CListCtrl::CreateDragImage](../Topic/CListCtrl::CreateDragImage.md)|生成一个拖动图像为指定的项列表。|  
|[CListCtrl::CreateEx](../Topic/CListCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个列表控件并将它附加到 `CListCtrl` 对象。|  
|[CListCtrl::DeleteAllItems](../Topic/CListCtrl::DeleteAllItems.md)|从控件中删除所有项。|  
|[CListCtrl::DeleteColumn](../Topic/CListCtrl::DeleteColumn.md)|从列表视图控件中删除列。|  
|[CListCtrl::DeleteItem](../Topic/CListCtrl::DeleteItem.md)|从控件中删除项。|  
|[CListCtrl::DrawItem](../Topic/CListCtrl::DrawItem.md)|调用，当所有者描述控件中的可视方面是。|  
|[CListCtrl::EditLabel](../Topic/CListCtrl::EditLabel.md)|启动就地编辑项目的文本。|  
|[CListCtrl::EnableGroupView](../Topic/CListCtrl::EnableGroupView.md)|启用或禁用列表中的项是否查看控件显示为组。|  
|[CListCtrl::EnsureVisible](../Topic/CListCtrl::EnsureVisible.md)|确保项目可见。|  
|[CListCtrl::FindItem](../Topic/CListCtrl::FindItem.md)|搜索指定属性的列表视图项。|  
|[CListCtrl::GetBkColor](../Topic/CListCtrl::GetBkColor.md)|检索列表视图控件的背景色。|  
|[CListCtrl::GetBkImage](../Topic/CListCtrl::GetBkImage.md)|检索列表视图控件的当前背景图像。|  
|[CListCtrl::GetCallbackMask](../Topic/CListCtrl::GetCallbackMask.md)|检索列表视图控件的回调掩码。|  
|[CListCtrl::GetCheck](../Topic/CListCtrl::GetCheck.md)|检索状态图像的当前显示状态与项目。|  
|[CListCtrl::GetColumn](../Topic/CListCtrl::GetColumn.md)|检索控件的列的属性。|  
|[CListCtrl::GetColumnOrderArray](../Topic/CListCtrl::GetColumnOrderArray.md)|检索列顺序\(从左到右\)列表视图控件。|  
|[CListCtrl::GetColumnWidth](../Topic/CListCtrl::GetColumnWidth.md)|检索列的宽度在报表视图的或列表视图。|  
|[CListCtrl::GetCountPerPage](../Topic/CListCtrl::GetCountPerPage.md)|计算可能包含垂直列表视图控件项的数目。|  
|[CListCtrl::GetEditControl](../Topic/CListCtrl::GetEditControl.md)|检索使用的编辑控件中处理编辑项目的文本。|  
|[CListCtrl::GetEmptyText](../Topic/CListCtrl::GetEmptyText.md)|如果当前列表视图控件为空，则检索该字符串显示在中。|  
|[CListCtrl::GetExtendedStyle](../Topic/CListCtrl::GetExtendedStyle.md)|检索列表视图控件的当前扩展样式。|  
|[CListCtrl::GetFirstSelectedItemPosition](../Topic/CListCtrl::GetFirstSelectedItemPosition.md)|检索首先选定的位置列表在列表视图控件的视图项。|  
|[CListCtrl::GetFocusedGroup](../Topic/CListCtrl::GetFocusedGroup.md)|检索具有键盘焦点在当前列表视图控件组。|  
|[CListCtrl::GetGroupCount](../Topic/CListCtrl::GetGroupCount.md)|检索组的数量的当前列表视图控件的。|  
|[CListCtrl::GetGroupInfo](../Topic/CListCtrl::GetGroupInfo.md)|获取列表视图控件的指定组的信息。|  
|[CListCtrl::GetGroupInfoByIndex](../Topic/CListCtrl::GetGroupInfoByIndex.md)|检索有关指定组的信息的列表视图控件的。|  
|[CListCtrl::GetGroupMetrics](../Topic/CListCtrl::GetGroupMetrics.md)|检索组的指标。|  
|[CListCtrl::GetGroupRect](../Topic/CListCtrl::GetGroupRect.md)|检索指定的组的边框当前列表视图控件的。|  
|[CListCtrl::GetGroupState](../Topic/CListCtrl::GetGroupState.md)|检索指定的组的当前状态列表视图控件的。|  
|[CListCtrl::GetHeaderCtrl](../Topic/CListCtrl::GetHeaderCtrl.md)|检索列表视图控件的标头控件。|  
|[CListCtrl::GetHotCursor](../Topic/CListCtrl::GetHotCursor.md)|在快捷跟踪为列表视图控件时，启用检索使用的光标。|  
|[CListCtrl::GetHotItem](../Topic/CListCtrl::GetHotItem.md)|当前检索列表视图项在光标之下。|  
|[CListCtrl::GetHoverTime](../Topic/CListCtrl::GetHoverTime.md)|检索列表视图控件的当前悬停时间。|  
|[CListCtrl::GetImageList](../Topic/CListCtrl::GetImageList.md)|检索图像的处理列出用于绘制列表视图项。|  
|[CListCtrl::GetInsertMark](../Topic/CListCtrl::GetInsertMark.md)|检索插入标记的当前位置。|  
|[CListCtrl::GetInsertMarkColor](../Topic/CListCtrl::GetInsertMarkColor.md)|检索插入标记的当前颜色。|  
|[CListCtrl::GetInsertMarkRect](../Topic/CListCtrl::GetInsertMarkRect.md)|检索限制插入点的矩形。|  
|[CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)|检索列表视图项目的属性。|  
|[CListCtrl::GetItemCount](../Topic/CListCtrl::GetItemCount.md)|检索项的数目列表视图控件的。|  
|[CListCtrl::GetItemData](../Topic/CListCtrl::GetItemData.md)|检索该特定的值与项目。|  
|[CListCtrl::GetItemIndexRect](../Topic/CListCtrl::GetItemIndexRect.md)|检索一个子项的全部或部分的边框在当前列表视图控件的。|  
|[CListCtrl::GetItemPosition](../Topic/CListCtrl::GetItemPosition.md)|检索列表视图项的位置。|  
|[CListCtrl::GetItemRect](../Topic/CListCtrl::GetItemRect.md)|检索项目的边框。|  
|[CListCtrl::GetItemSpacing](../Topic/CListCtrl::GetItemSpacing.md)|计算项之间的间隔在当前列表视图控件。|  
|[CListCtrl::GetItemState](../Topic/CListCtrl::GetItemState.md)|检索列表视图项的状态。|  
|[CListCtrl::GetItemText](../Topic/CListCtrl::GetItemText.md)|检索列表视图项目或子项的文本。|  
|[CListCtrl::GetNextItem](../Topic/CListCtrl::GetNextItem.md)|搜索一个列表视图项与指定的属性以及对特定项的指定关系。|  
|[CListCtrl::GetNextItemIndex](../Topic/CListCtrl::GetNextItemIndex.md)|检索项的索引在具有指定的属性的当前列表视图控件的。|  
|[CListCtrl::GetNextSelectedItem](../Topic/CListCtrl::GetNextSelectedItem.md)|检索列表视图项目位置的索引，并且，接下来选定的位置列表重复查看项目。|  
|[CListCtrl::GetNumberOfWorkAreas](../Topic/CListCtrl::GetNumberOfWorkAreas.md)|检索操作范围的当前列表视图控件的。|  
|[CListCtrl::GetOrigin](../Topic/CListCtrl::GetOrigin.md)|检索列表视图控件的当前视图原点。|  
|[CListCtrl::GetOutlineColor](../Topic/CListCtrl::GetOutlineColor.md)|检索列表视图控件的边框的颜色。|  
|[CListCtrl::GetSelectedColumn](../Topic/CListCtrl::GetSelectedColumn.md)|检索当前所选列的索引在列表控件中。|  
|[CListCtrl::GetSelectedCount](../Topic/CListCtrl::GetSelectedCount.md)|检索选定项的数量列表视图控件的。|  
|[CListCtrl::GetSelectionMark](../Topic/CListCtrl::GetSelectionMark.md)|检索列表视图控件的选择标记。|  
|[CListCtrl::GetStringWidth](../Topic/CListCtrl::GetStringWidth.md)|命令式最小的列宽显示所有给定的字符串。|  
|[CListCtrl::GetSubItemRect](../Topic/CListCtrl::GetSubItemRect.md)|检索一个项的边框列表视图控件的。|  
|[CListCtrl::GetTextBkColor](../Topic/CListCtrl::GetTextBkColor.md)|检索列表视图控件的文本背景色。|  
|[CListCtrl::GetTextColor](../Topic/CListCtrl::GetTextColor.md)|检索列表视图控件的文本颜色。|  
|[CListCtrl::GetTileInfo](../Topic/CListCtrl::GetTileInfo.md)|检索有关个平铺的信息在列表视图控件。|  
|[CListCtrl::GetTileViewInfo](../Topic/CListCtrl::GetTileViewInfo.md)|检索有关列表视图控件的信息平铺视图。|  
|[CListCtrl::GetToolTips](../Topic/CListCtrl::GetToolTips.md)|检索列表视图控件使用显示工具提示的工具提示控件。|  
|[CListCtrl::GetTopIndex](../Topic/CListCtrl::GetTopIndex.md)|检索最顶层的可见项的索引。|  
|[CListCtrl::GetView](../Topic/CListCtrl::GetView.md)|获取列表视图控件的视图。|  
|[CListCtrl::GetViewRect](../Topic/CListCtrl::GetViewRect.md)|检索所有项目边框的列表视图控件的。|  
|[CListCtrl::GetWorkAreas](../Topic/CListCtrl::GetWorkAreas.md)|检索列表视图控件的当前工作区域。|  
|[CListCtrl::HasGroup](../Topic/CListCtrl::HasGroup.md)|确定列表视图控件是否具有指定的组。|  
|[CListCtrl::HitTest](../Topic/CListCtrl::HitTest.md)|确定列表视图项在指定的位置。|  
|[CListCtrl::InsertColumn](../Topic/CListCtrl::InsertColumn.md)|插入新列列表视图控件。|  
|[CListCtrl::InsertGroup](../Topic/CListCtrl::InsertGroup.md)|插入每组添加到列表视图控件。|  
|[CListCtrl::InsertGroupSorted](../Topic/CListCtrl::InsertGroupSorted.md)|指定的组添加到中的有序列表组的插入。|  
|[CListCtrl::InsertItem](../Topic/CListCtrl::InsertItem.md)|插入新项列表视图控件。|  
|[CListCtrl::InsertMarkHitTest](../Topic/CListCtrl::InsertMarkHitTest.md)|检索插入点最接近指定的点。|  
|[CListCtrl::IsGroupViewEnabled](../Topic/CListCtrl::IsGroupViewEnabled.md)|确定分组视图是否为列表视图控件启用。|  
|[CListCtrl::IsItemVisible](../Topic/CListCtrl::IsItemVisible.md)|指示当前列表视图控件的指定项目是否可见。|  
|[CListCtrl::MapIDToIndex](../Topic/CListCtrl::MapIDToIndex.md)|映射一个项目的唯一ID在当前列表视图控件的进行索引。|  
|[CListCtrl::MapIndexToID](../Topic/CListCtrl::MapIndexToID.md)|映射一个项的索引在当前列表视图控件的设置为唯一ID.|  
|[CListCtrl::MoveGroup](../Topic/CListCtrl::MoveGroup.md)|将指定的组。|  
|[CListCtrl::MoveItemToGroup](../Topic/CListCtrl::MoveItemToGroup.md)|将指定的组移动到列表视图控件的指定零基于索引。|  
|[CListCtrl::RedrawItems](../Topic/CListCtrl::RedrawItems.md)|强制列表视图控件重新绘制项的大小。|  
|[CListCtrl::RemoveAllGroups](../Topic/CListCtrl::RemoveAllGroups.md)|从列表视图控件移除所有组。|  
|[CListCtrl::RemoveGroup](../Topic/CListCtrl::RemoveGroup.md)|从列表视图控件中移除指定的组。|  
|[CListCtrl::Scroll](../Topic/CListCtrl::Scroll.md)|移动列表视图控件的内容。|  
|[CListCtrl::SetBkColor](../Topic/CListCtrl::SetBkColor.md)|设置列表视图控件的背景色。|  
|[CListCtrl::SetBkImage](../Topic/CListCtrl::SetBkImage.md)|设置列表视图控件的当前背景图像。|  
|[CListCtrl::SetCallbackMask](../Topic/CListCtrl::SetCallbackMask.md)|设置列表视图控件的回调掩码。|  
|[CListCtrl::SetCheck](../Topic/CListCtrl::SetCheck.md)|设置状态图像的当前显示状态与项目。|  
|[CListCtrl::SetColumn](../Topic/CListCtrl::SetColumn.md)|设置列表视图列的属性。|  
|[CListCtrl::SetColumnOrderArray](../Topic/CListCtrl::SetColumnOrderArray.md)|设置列顺序\(从左到右\)列表视图控件。|  
|[CListCtrl::SetColumnWidth](../Topic/CListCtrl::SetColumnWidth.md)|更改列的宽度在报表视图的或列表视图。|  
|[CListCtrl::SetExtendedStyle](../Topic/CListCtrl::SetExtendedStyle.md)|设置列表视图控件的当前扩展样式。|  
|[CListCtrl::SetGroupInfo](../Topic/CListCtrl::SetGroupInfo.md)|设置列表视图控件的指定组的信息。|  
|[CListCtrl::SetGroupMetrics](../Topic/CListCtrl::SetGroupMetrics.md)|设置列表视图控件组度量。|  
|[CListCtrl::SetHotCursor](../Topic/CListCtrl::SetHotCursor.md)|在快捷跟踪为列表视图控件时，启用设置的光标。|  
|[CListCtrl::SetHotItem](../Topic/CListCtrl::SetHotItem.md)|设置列表视图控件的当前快捷项目。|  
|[CListCtrl::SetHoverTime](../Topic/CListCtrl::SetHoverTime.md)|设置列表视图控件的当前悬停时间。|  
|[CListCtrl::SetIconSpacing](../Topic/CListCtrl::SetIconSpacing.md)|将图标之间的间隔在列表视图控件。|  
|[CListCtrl::SetImageList](../Topic/CListCtrl::SetImageList.md)|分配图像列表与list view控件。|  
|[CListCtrl::SetInfoTip](../Topic/CListCtrl::SetInfoTip.md)|设置工具提示文本。|  
|[CListCtrl::SetInsertMark](../Topic/CListCtrl::SetInsertMark.md)|将插入点移到所定义的位置。|  
|[CListCtrl::SetInsertMarkColor](../Topic/CListCtrl::SetInsertMarkColor.md)|设置的颜色插入点。|  
|[CListCtrl::SetItem](../Topic/CListCtrl::SetItem.md)|设置某些或所有列表视图项目的属性。|  
|[CListCtrl::SetItemCount](../Topic/CListCtrl::SetItemCount.md)|一个列表视图控件用于添加大量项做好准备。|  
|[CListCtrl::SetItemCountEx](../Topic/CListCtrl::SetItemCountEx.md)|设置虚拟的项计数列表视图控件。|  
|[CListCtrl::SetItemData](../Topic/CListCtrl::SetItemData.md)|设置项目的特定于应用程序的值。|  
|[CListCtrl::SetItemIndexState](../Topic/CListCtrl::SetItemIndexState.md)|设置一个项的状态在当前列表视图控件的。|  
|[CListCtrl::SetItemPosition](../Topic/CListCtrl::SetItemPosition.md)|将项移动到列表视图控件中的指定位置。|  
|[CListCtrl::SetItemState](../Topic/CListCtrl::SetItemState.md)|更改项目的状态在列表视图控件的。|  
|[CListCtrl::SetItemText](../Topic/CListCtrl::SetItemText.md)|更改列表视图项目或子项的文本。|  
|[CListCtrl::SetOutlineColor](../Topic/CListCtrl::SetOutlineColor.md)|设置列表视图控件的边框的颜色。|  
|[CListCtrl::SetSelectedColumn](../Topic/CListCtrl::SetSelectedColumn.md)|设置列表视图控件的选定列。|  
|[CListCtrl::SetSelectionMark](../Topic/CListCtrl::SetSelectionMark.md)|设置列表视图控件的选择标记。|  
|[CListCtrl::SetTextBkColor](../Topic/CListCtrl::SetTextBkColor.md)|设置文本的背景颜色列表视图控件的。|  
|[CListCtrl::SetTextColor](../Topic/CListCtrl::SetTextColor.md)|设置列表视图控件的文本颜色。|  
|[CListCtrl::SetTileInfo](../Topic/CListCtrl::SetTileInfo.md)|设置列表视图控件的平铺的信息。|  
|[CListCtrl::SetTileViewInfo](../Topic/CListCtrl::SetTileViewInfo.md)|设置列表视图控件使用平铺视图的信息。|  
|[CListCtrl::SetToolTips](../Topic/CListCtrl::SetToolTips.md)|设置列表视图控件将使用显示工具提示的工具提示控件。|  
|[CListCtrl::SetView](../Topic/CListCtrl::SetView.md)|设置列表视图控件的视图。|  
|[CListCtrl::SetWorkAreas](../Topic/CListCtrl::SetWorkAreas.md)|设置图标列表视图控件中显示的区域。|  
|[CListCtrl::SortGroups](../Topic/CListCtrl::SortGroups.md)|排序一个列表视图控件组与一个用户定义的函数。|  
|[CListCtrl::SortItems](../Topic/CListCtrl::SortItems.md)|使用应用程序定义的比较函数，排序列表视图项。|  
|[CListCtrl::SortItemsEx](../Topic/CListCtrl::SortItemsEx.md)|使用应用程序定义的比较函数，排序列表视图项。|  
|[CListCtrl::SubItemHitTest](../Topic/CListCtrl::SubItemHitTest.md)|确定列表视图项目，如果有，在特定位置。|  
|[CListCtrl::Update](../Topic/CListCtrl::Update.md)|强制该控件重新绘制一个指定项。|  
  
## 备注  
 除了图标和标签外，每个项可以在列中显示的信息在该图标和标签的右侧。  此控件\(并 `CListCtrl` 选件类\)若要在运行Windows 95 \/98和Windows NT 3.51版下的程序可用和更高版本。  
  
 下面是 `CListCtrl` 选件类的简要概述。  有关详细概念，讨论，请参见 [使用CListCtrl](../../mfc/using-clistctrl.md) 和 [控件](../../mfc/controls-mfc.md)。  
  
## 视图  
 列表视图控件可以显示其内容通过四种不同的方式，调用“视图”。  
  
-   图标视图  
  
     每个项显示为一个大型图标\(32 x 32像素\)与标签在其下方。  用户可以通过拖动项添加到列表视图窗口中的任意位置。  
  
-   小图标视图  
  
     每个项显示为一个小图标\(16 x 16像素\)与标签在右侧。  用户可以通过拖动项添加到列表视图窗口中的任意位置。  
  
-   列表视图  
  
     每个项显示为带有标签的一个小图标在右侧。  项目在列排列，则无法拖到列表视图窗口的任何位置。  
  
-   报告视图  
  
     每个项目中列都显示行，当附加信息排列右侧。  最左侧的列包含小图标和标签，因此，随后的列包含子项如指定由应用程序。  嵌入式标头控件\(选件类 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)\)实现这些列。  有关标头控件和列的更多信息在报表视图，请参见 [使用CListCtrl:将列添加到控件\(报告视图\)](../../mfc/adding-columns-to-the-control-report-view.md)。  
  
 另请参见:  
  
-   知识库文章Q250614:HOWTO:对CListCtrl的项目在"报告"视图  
  
-   知识库文章Q200054：PRB: OnTimer\(\) 没有为列表控件重复调用  
  
 控件的当前的样式列表视图确定当前视图。  有关这些样式及其用法的更多信息，请参见 [使用CListCtrl:更改列表控件样式](../../mfc/changing-list-control-styles.md)。  
  
## 扩展样式  
 除该标准列表外样式，`CListCtrl` 支持大量扩展样式的选件类，提供了丰富的功能。  此功能的一些示例包括:  
  
-   悬停选择  
  
     当启用，允许项目的自动选择，当光标保持在项目某个时间段时。  
  
-   虚拟列表视图  
  
     当启用，允许控件支持到 `DWORD` 项目。  这是通过将开销可能的托管项目数据从应用程序。  除项目选择和焦点信息，必须由应用程序管理所有项目信息。  有关更多信息，请参见 [使用CListCtrl:虚拟列表控件](../../mfc/virtual-list-controls.md)。  
  
-   一个和两单击启动  
  
     启用此功能，使显示项的快捷跟踪\(自动显示项文本\)和一个或两单击启动。  
  
-   拖放列排序  
  
     当启用，允许进行拖放重新排序列表视图控件中的列。  仅在报表视图。  
  
 有关使用这些新扩展样式的信息，请参见 [使用CListCtrl:更改列表控件样式](../../mfc/changing-list-control-styles.md)。  
  
## 项目和子项  
 在列表视图控件的每个项目包括图标\(从图像列表\)，标签、一个当前状态和一个应用程序定义的值\(称为“项目数据”）。  一个或多个子项还可以与每个项目。  “子项”是，在报表视图中，在列中显示项目中的图标和标签的右侧的字符串。  在列表视图控件的所有项都必须有子项的相同数量。  
  
 选件类 **CListCtrl** 用于插入，删除，找到并修改这些项提供了多种功能。  有关更多信息，请参见 [CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)、 [CListCtrl::InsertItem](../Topic/CListCtrl::InsertItem.md)和 [CListCtrl::FindItem](../Topic/CListCtrl::FindItem.md)、 [使用CListCtrl:向控件添加项](../../mfc/adding-items-to-the-control.md)和 [使用CListCtrl:移动，使，排序和查找列表控件](../../mfc/scrolling-arranging-sorting-and-finding-in-list-controls.md)。  
  
 默认情况下，列表视图控件绑定到存储项的图标和文本属性负责。  但是，除这些项目类型，选件类 `CListCtrl` 支持“回调项目”。“回调项目”是应用程序的列表视图项目而不是控件—存储文本，图标或两个。  回调掩码用于指定哪些项属性\(文本和图标\)提供应用程序。  如果应用程序使用回调项目，必须能够提供文本和图标属性在要求。  当您的应用程序中维护某些此信息时，回调项目很有用。  有关更多信息，请参见 [使用CListCtrl:回调项目和回调掩码](../../mfc/callback-items-and-the-callback-mask.md)。  
  
## 图像列表  
 图标、标头项图像和应用定义的状态为列表视图项在多个包含图像列表\(实现由选件类 [CImageList](../../mfc/reference/cimagelist-class.md)\)，生成和分配到列表视图控件。  每个列表视图控件可以包含图像的四种不同类型的列表:  
  
-   大图标  
  
     使用在图标视图对于大型图标。  
  
-   小图标  
  
     使用在小图标，列表，并报告用于图标视图中图标的较小版本的视图。  
  
-   应用程序定义的状态  
  
     包含状态图像，在项目的图标旁边显示指示一个应用程序定义的状态。  
  
-   Header item  
  
     使用在报表视图用于显示每个标头控制的项的小图像。  
  
 默认情况下，那么，当销毁时，列表视图控件在销毁图像列表分配给它;但是，可以通过销毁每个图像来自定义此行为列表，当不再使用对象时它，如应用程序依赖于开发人员。  有关更多信息，请参见 [使用CListCtrl:列表项，并且图像列表](../../mfc/list-items-and-image-lists.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [MFC示例ROWLIST](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)