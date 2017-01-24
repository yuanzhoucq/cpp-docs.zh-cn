---
title: "CDockingPanesRow Class | Microsoft Docs"
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
  - "CDockingPanesRow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockingPanesRow class"
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockingPanesRow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理位于停靠站点中同一水平或垂直行（列）的窗格的列表。  
  
## 语法  
  
```  
class CDockingPanesRow : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|`CDockingPanesRow::CDockingPanesRow`|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDockingPanesRow::AddPane](../Topic/CDockingPanesRow::AddPane.md)||  
|[CDockingPanesRow::AddPaneFromRow](../Topic/CDockingPanesRow::AddPaneFromRow.md)||  
|[CDockingPanesRow::ArrangePanes](../Topic/CDockingPanesRow::ArrangePanes.md)|根据指定边距和间距参数将窗格排成行。|  
|[CDockingPanesRow::CalcFixedLayout](../Topic/CDockingPanesRow::CalcFixedLayout.md)||  
|[CDockingPanesRow::Create](../Topic/CDockingPanesRow::Create.md)||  
|[CDockingPanesRow::ExpandStretchedPanes](../Topic/CDockingPanesRow::ExpandStretchedPanes.md)||  
|[CDockingPanesRow::ExpandStretchedPanesRect](../Topic/CDockingPanesRow::ExpandStretchedPanesRect.md)||  
|[CDockingPanesRow::FixupVirtualRects](../Topic/CDockingPanesRow::FixupVirtualRects.md)||  
|[CDockingPanesRow::GetAvailableLength](../Topic/CDockingPanesRow::GetAvailableLength.md)||  
|[CDockingPanesRow::GetAvailableSpace](../Topic/CDockingPanesRow::GetAvailableSpace.md)||  
|[CDockingPanesRow::GetClientRect](../Topic/CDockingPanesRow::GetClientRect.md)||  
|[CDockingPanesRow::GetDockSite](../Topic/CDockingPanesRow::GetDockSite.md)||  
|[CDockingPanesRow::GetExtraSpace](../Topic/CDockingPanesRow::GetExtraSpace.md)||  
|[CDockingPanesRow::GetGroupFromPane](../Topic/CDockingPanesRow::GetGroupFromPane.md)||  
|[CDockingPanesRow::GetID](../Topic/CDockingPanesRow::GetID.md)||  
|[CDockingPanesRow::GetMaxPaneSize](../Topic/CDockingPanesRow::GetMaxPaneSize.md)||  
|[CDockingPanesRow::GetPaneCount](../Topic/CDockingPanesRow::GetPaneCount.md)||  
|[CDockingPanesRow::GetPaneList](../Topic/CDockingPanesRow::GetPaneList.md)||  
|[CDockingPanesRow::GetRowAlignment](../Topic/CDockingPanesRow::GetRowAlignment.md)||  
|[CDockingPanesRow::GetRowHeight](../Topic/CDockingPanesRow::GetRowHeight.md)||  
|[CDockingPanesRow::GetRowOffset](../Topic/CDockingPanesRow::GetRowOffset.md)||  
|[CDockingPanesRow::GetVisibleCount](../Topic/CDockingPanesRow::GetVisibleCount.md)||  
|[CDockingPanesRow::GetWindowRect](../Topic/CDockingPanesRow::GetWindowRect.md)||  
|[CDockingPanesRow::HasPane](../Topic/CDockingPanesRow::HasPane.md)||  
|[CDockingPanesRow::IsEmpty](../Topic/CDockingPanesRow::IsEmpty.md)||  
|[CDockingPanesRow::IsExclusiveRow](../Topic/CDockingPanesRow::IsExclusiveRow.md)||  
|[CDockingPanesRow::IsHorizontal](../Topic/CDockingPanesRow::IsHorizontal.md)||  
|[CDockingPanesRow::IsVisible](../Topic/CDockingPanesRow::IsVisible.md)||  
|[CDockingPanesRow::Move](../Topic/CDockingPanesRow::Move.md)||  
|[CDockingPanesRow::MovePane](../Topic/CDockingPanesRow::MovePane.md)||  
|[CDockingPanesRow::OnResizePane](../Topic/CDockingPanesRow::OnResizePane.md)||  
|[CDockingPanesRow::RedrawAll](../Topic/CDockingPanesRow::RedrawAll.md)||  
|[CDockingPanesRow::RemovePane](../Topic/CDockingPanesRow::RemovePane.md)||  
|[CDockingPanesRow::ReplacePane](../Topic/CDockingPanesRow::ReplacePane.md)||  
|[CDockingPanesRow::RepositionPanes](../Topic/CDockingPanesRow::RepositionPanes.md)||  
|[CDockingPanesRow::Resize](../Topic/CDockingPanesRow::Resize.md)||  
|[CDockingPanesRow::ResizeByPaneDivider](../Topic/CDockingPanesRow::ResizeByPaneDivider.md)||  
|[CDockingPanesRow::ScreenToClient](../Topic/CDockingPanesRow::ScreenToClient.md)||  
|[CDockingPanesRow::SetExtra](../Topic/CDockingPanesRow::SetExtra.md)||  
|[CDockingPanesRow::ShowDockSiteRow](../Topic/CDockingPanesRow::ShowDockSiteRow.md)||  
|[CDockingPanesRow::ShowPane](../Topic/CDockingPanesRow::ShowPane.md)||  
|[CDockingPanesRow::UpdateVisibleState](../Topic/CDockingPanesRow::UpdateVisibleState.md)||  
  
## 备注  
 `CDockingPanesRow` 对象由停靠站点对象在内部创建。  
  
## 示例  
 下面的示例演示如何从 `CMFCAutoHideBar` 对象获取 `CDockingPanesRow` 对象。  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/CPP/cdockingpanesrow-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)  
  
## 要求  
 **标头：**afxDockingPanesRow.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CDockSite Class](../../mfc/reference/cdocksite-class.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)