---
title: "CPaneContainerManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaneContainerManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneContainerManager class"
ms.assetid: 3d974c15-a62f-4648-bb5b-cc31ab7950af
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CPaneContainerManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPaneContainerManager` 选件类控制当前停靠格式的存储和显示。  
  
## 语法  
  
```  
class CPaneContainerManager : public CObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPaneContainerManager::AddPane](../Topic/CPaneContainerManager::AddPane.md)||  
|[CPaneContainerManager::AddPaneContainerManager](../Topic/CPaneContainerManager::AddPaneContainerManager.md)||  
|[CPaneContainerManager::AddPaneContainerManagerToDockablePane](../Topic/CPaneContainerManager::AddPaneContainerManagerToDockablePane.md)||  
|[CPaneContainerManager::AddPanesToList](../Topic/CPaneContainerManager::AddPanesToList.md)||  
|[CPaneContainerManager::AddPaneToList](../Topic/CPaneContainerManager::AddPaneToList.md)||  
|[CPaneContainerManager::AddPaneToRecentPaneContainer](../Topic/CPaneContainerManager::AddPaneToRecentPaneContainer.md)||  
|[CPaneContainerManager::CalcRects](../Topic/CPaneContainerManager::CalcRects.md)||  
|[CPaneContainerManager::CanBeAttached](../Topic/CPaneContainerManager::CanBeAttached.md)||  
|[CPaneContainerManager::CheckAndRemoveNonValidPane](../Topic/CPaneContainerManager::CheckAndRemoveNonValidPane.md)||  
|[CPaneContainerManager::CheckForMiniFrameAndCaption](../Topic/CPaneContainerManager::CheckForMiniFrameAndCaption.md)||  
|[CPaneContainerManager::Create](../Topic/CPaneContainerManager::Create.md)||  
|[CPaneContainerManager::DoesAllowDynInsertBefore](../Topic/CPaneContainerManager::DoesAllowDynInsertBefore.md)||  
|[CPaneContainerManager::DoesContainFloatingPane](../Topic/CPaneContainerManager::DoesContainFloatingPane.md)||  
|[CPaneContainerManager::EnableGrippers](../Topic/CPaneContainerManager::EnableGrippers.md)||  
|[CPaneContainerManager::FindPaneContainer](../Topic/CPaneContainerManager::FindPaneContainer.md)||  
|[CPaneContainerManager::FindTabbedPane](../Topic/CPaneContainerManager::FindTabbedPane.md)||  
|[CPaneContainerManager::GetAvailableSpace](../Topic/CPaneContainerManager::GetAvailableSpace.md)||  
|[CPaneContainerManager::GetDefaultPaneDivider](../Topic/CPaneContainerManager::GetDefaultPaneDivider.md)||  
|[CPaneContainerManager::GetDockSiteFrameWnd](../Topic/CPaneContainerManager::GetDockSiteFrameWnd.md)||  
|[CPaneContainerManager::GetFirstPane](../Topic/CPaneContainerManager::GetFirstPane.md)||  
|[CPaneContainerManager::GetFirstVisiblePane](../Topic/CPaneContainerManager::GetFirstVisiblePane.md)||  
|[CPaneContainerManager::GetMinMaxOffset](../Topic/CPaneContainerManager::GetMinMaxOffset.md)||  
|[CPaneContainerManager::GetMinSize](../Topic/CPaneContainerManager::GetMinSize.md)||  
|[CPaneContainerManager::GetNodeCount](../Topic/CPaneContainerManager::GetNodeCount.md)||  
|[CPaneContainerManager::GetPaneContainerRTC](../Topic/CPaneContainerManager::GetPaneContainerRTC.md)||  
|[CPaneContainerManager::GetPaneCount](../Topic/CPaneContainerManager::GetPaneCount.md)||  
|[CPaneContainerManager::GetTotalRefCount](../Topic/CPaneContainerManager::GetTotalRefCount.md)||  
|[CPaneContainerManager::GetVisiblePaneCount](../Topic/CPaneContainerManager::GetVisiblePaneCount.md)||  
|[CPaneContainerManager::GetWindowRect](../Topic/CPaneContainerManager::GetWindowRect.md)||  
|[CPaneContainerManager::HideAll](../Topic/CPaneContainerManager::HideAll.md)||  
|[CPaneContainerManager::InsertPane](../Topic/CPaneContainerManager::InsertPane.md)||  
|[CPaneContainerManager::IsAutoHideMode](../Topic/CPaneContainerManager::IsAutoHideMode.md)||  
|[CPaneContainerManager::IsEmpty](../Topic/CPaneContainerManager::IsEmpty.md)||  
|[CPaneContainerManager::IsRootPaneContainerVisible](../Topic/CPaneContainerManager::IsRootPaneContainerVisible.md)||  
|[CPaneContainerManager::NotifyPaneDivider](../Topic/CPaneContainerManager::NotifyPaneDivider.md)||  
|[CPaneContainerManager::OnPaneDividerMove](../Topic/CPaneContainerManager::OnPaneDividerMove.md)||  
|[CPaneContainerManager::OnShowPane](../Topic/CPaneContainerManager::OnShowPane.md)||  
|[CPaneContainerManager::PaneFromPoint](../Topic/CPaneContainerManager::PaneFromPoint.md)||  
|[CPaneContainerManager::ReleaseEmptyPaneContainers](../Topic/CPaneContainerManager::ReleaseEmptyPaneContainers.md)||  
|[CPaneContainerManager::RemoveAllPanesAndPaneDividers](../Topic/CPaneContainerManager::RemoveAllPanesAndPaneDividers.md)||  
|[CPaneContainerManager::RemoveNonValidPanes](../Topic/CPaneContainerManager::RemoveNonValidPanes.md)||  
|[CPaneContainerManager::RemovePaneDivider](../Topic/CPaneContainerManager::RemovePaneDivider.md)||  
|[CPaneContainerManager::RemovePaneFromPaneContainer](../Topic/CPaneContainerManager::RemovePaneFromPaneContainer.md)||  
|[CPaneContainerManager::ReplacePane](../Topic/CPaneContainerManager::ReplacePane.md)||  
|[CPaneContainerManager::ResizePaneContainers](../Topic/CPaneContainerManager::ResizePaneContainers.md)||  
|[CPaneContainerManager::Serialize](../Topic/CPaneContainerManager::Serialize.md)|读取或写入此对象从或对存档。  （重写 [CObject::Serialize](../Topic/CObject::Serialize.md)。）|  
|[CPaneContainerManager::SetDefaultPaneDividerForPanes](../Topic/CPaneContainerManager::SetDefaultPaneDividerForPanes.md)||  
|[CPaneContainerManager::SetPaneContainerRTC](../Topic/CPaneContainerManager::SetPaneContainerRTC.md)||  
|[CPaneContainerManager::SetResizeMode](../Topic/CPaneContainerManager::SetResizeMode.md)||  
|[CPaneContainerManager::StoreRecentDockSiteInfo](../Topic/CPaneContainerManager::StoreRecentDockSiteInfo.md)||  
  
### 备注  
 框架自动创建 `CPaneContainerManager` 对象实例并嵌入到 [CPaneDivider Class](../../mfc/reference/cpanedivider-class.md) 对象或到 [CMultiPaneFrameWnd Class](../../mfc/reference/cmultipaneframewnd-class.md) 对象。  
  
 `CPaneContainerManager` 选件类存储指向从 [CPaneContainer](../../mfc/reference/cpanecontainer-class.md) 对象编译二进制树的根。  
  
## 示例  
 下面的示例演示 `CPaneContainerManager` 对象演示如何获取对的引用。  此代码段是 [设置窗格大小示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_SetPaneSize#5](../../mfc/reference/codesnippet/CPP/cpanecontainermanager-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)  
  
## 要求  
 **标头:** afxpanecontainermanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)   
 [CPaneDivider Class](../../mfc/reference/cpanedivider-class.md)