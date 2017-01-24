---
title: "CDockingManager Class | Microsoft Docs"
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
  - "CDockingManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockingManager class"
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
caps.latest.revision: 37
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockingManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现核心的功能停靠在主框架窗口的控件的布局。  
  
## 语法  
  
```  
class CDockingManager : public CObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDockingManager::AddDockSite](../Topic/CDockingManager::AddDockSite.md)|创建一个停靠窗格并将其添加到控件条列表。|  
|[CDockingManager::AddHiddenMDITabbedBar](../Topic/CDockingManager::AddHiddenMDITabbedBar.md)|添加一个句柄栏窗格到隐藏的MDI选项卡式栏窗格中列出。|  
|[CDockingManager::AddMiniFrame](../Topic/CDockingManager::AddMiniFrame.md)|添加一个帧到要帧列表。|  
|[CDockingManager::AddPane](../Topic/CDockingManager::AddPane.md)|注册了停靠管理器的一个窗格。|  
|[CDockingManager::AdjustDockingLayout](../Topic/CDockingManager::AdjustDockingLayout.md)|重新调整所有窗格布局在框架窗口中。|  
|[CDockingManager::AdjustPaneFrames](../Topic/CDockingManager::AdjustPaneFrames.md)|导致 `WM_NCCALCSIZE` 消息发送到所有窗格和 `CPaneFrameWnd` 窗口。|  
|[CDockingManager::AdjustRectToClientArea](../Topic/CDockingManager::AdjustRectToClientArea.md)|调整矩形的对齐方式。|  
|[CDockingManager::AlignAutoHidePane](../Topic/CDockingManager::AlignAutoHidePane.md)|在窗口模式调整停靠窗格，以便它采用停靠站点括起来的帧的工作区的全角或高度。|  
|[CDockingManager::AutoHidePane](../Topic/CDockingManager::AutoHidePane.md)|创建一个窗口工具栏。|  
|[CDockingManager::BringBarsToTop](../Topic/CDockingManager::BringBarsToTop.md)|将具有指定的对齐方式在顶层的停靠条。|  
|[CDockingManager::BuildPanesMenu](../Topic/CDockingManager::BuildPanesMenu.md)|添加停靠窗格和工具栏的名称添加到菜单。|  
|[CDockingManager::CalcExpectedDockedRect](../Topic/CDockingManager::CalcExpectedDockedRect.md)|计算一停靠窗口的预期的矩形。|  
|[CDockingManager::Create](../Topic/CDockingManager::Create.md)|创建一个停靠管理器。|  
|[CDockingManager::DeterminePaneAndStatus](../Topic/CDockingManager::DeterminePaneAndStatus.md)|确定包含给定的点窗格及其停靠状态。|  
|[CDockingManager::DisableRestoreDockState](../Topic/CDockingManager::DisableRestoreDockState.md)|启用或禁用停靠格式是从注册表中。|  
|[CDockingManager::DockPane](../Topic/CDockingManager::DockPane.md)|停靠一个窗格到另一个窗格或到框架窗口。|  
|[CDockingManager::DockPaneLeftOf](../Topic/CDockingManager::DockPaneLeftOf.md)|在另一个窗格的停靠一个窗格。|  
|[CDockingManager::EnableAutoHidePanes](../Topic/CDockingManager::EnableAutoHidePanes.md)|启用窗格的停靠到主框架，创建停靠窗格，并将其添加到控件条列表。|  
|[CDockingManager::EnableDocking](../Topic/CDockingManager::EnableDocking.md)|创建一个停靠窗格并启用窗格的停靠到主框架。|  
|[CDockingManager::EnableDockSiteMenu](../Topic/CDockingManager::EnableDockSiteMenu.md)|打开显示在所有停靠窗格的声明一个弹出菜单中的其他按钮。|  
|[CDockingManager::EnablePaneContextMenu](../Topic/CDockingManager::EnablePaneContextMenu.md)|调用库显示了应用程序工具栏和停靠窗格中列出的某个特定的上下文菜单，当用户单击鼠标右键，而库处理WM\_CONTEXTMENU消息。|  
|[CDockingManager::FindDockSite](../Topic/CDockingManager::FindDockSite.md)|检索在指定的位置，并具有指定的对齐条窗格。|  
|[CDockingManager::FindDockSiteByPane](../Topic/CDockingManager::FindDockSiteByPane.md)|返回具有目标栏窗格的ID的栏窗格。|  
|[CDockingManager::FindPaneByID](../Topic/CDockingManager::FindPaneByID.md)|按指定的控件ID.查找一个窗格|  
|[CDockingManager::FixupVirtualRects](../Topic/CDockingManager::FixupVirtualRects.md)|提交所有当前工具栏位置。虚拟矩形。|  
|[CDockingManager::FrameFromPoint](../Topic/CDockingManager::FrameFromPoint.md)|返回包含给定的点的帧。|  
|[CDockingManager::GetClientAreaBounds](../Topic/CDockingManager::GetClientAreaBounds.md)|获取包含工作区的区域的矩形。|  
|[CDockingManager::GetDockingMode](../Topic/CDockingManager::GetDockingMode.md)|返回当前停靠模式。|  
|[CDockingManager::GetDockSiteFrameWnd](../Topic/CDockingManager::GetDockSiteFrameWnd.md)|获取一个指向父窗架。|  
|[CDockingManager::GetEnabledAutoHideAlignment](../Topic/CDockingManager::GetEnabledAutoHideAlignment.md)|返回窗格启用的对齐方式。|  
|[CDockingManager::GetMiniFrames](../Topic/CDockingManager::GetMiniFrames.md)|获取miniframes列表。|  
|[CDockingManager::GetOuterEdgeBounds](../Topic/CDockingManager::GetOuterEdgeBounds.md)|获取包含框架的外边缘的矩形。|  
|[CDockingManager::GetPaneList](../Topic/CDockingManager::GetPaneList.md)|返回属于停靠管理器窗格的列表。  这包括所有浮动窗格。|  
|[CDockingManager::GetSmartDockingManager](../Topic/CDockingManager::GetSmartDockingManager.md)|检索指向有关智能停靠管理器。|  
|[CDockingManager::GetSmartDockingManagerPermanent](../Topic/CDockingManager::GetSmartDockingManagerPermanent.md)|检索指向有关智能停靠管理器。|  
|[CDockingManager::GetSmartDockingParams](../Topic/CDockingManager::GetSmartDockingParams.md)|返回停靠管理器的智能停靠参数。|  
|[CDockingManager::GetSmartDockingTheme](../Topic/CDockingManager::GetSmartDockingTheme.md)|返回用于的主题显示智能标记停靠的静态方法。|  
|[CDockingManager::HideAutoHidePanes](../Topic/CDockingManager::HideAutoHidePanes.md)|隐藏窗口模式下的一个窗格。|  
|[CDockingManager::InsertDockSite](../Topic/CDockingManager::InsertDockSite.md)|创建一个停靠窗格并粘贴到控件条中列出。|  
|[CDockingManager::InsertPane](../Topic/CDockingManager::InsertPane.md)|一个控件窗格到控件中列出禁止插入。|  
|[CDockingManager::IsDockSiteMenu](../Topic/CDockingManager::IsDockSiteMenu.md)|指定弹出菜单是否在所有窗格的图例中突出显示。|  
|[CDockingManager::IsInAdjustLayout](../Topic/CDockingManager::IsInAdjustLayout.md)|确定是否调整所有窗格布局。|  
|[CDockingManager::IsOLEContainerMode](../Topic/CDockingManager::IsOLEContainerMode.md)|指定停靠管理器是否在OLE容器模式。|  
|[CDockingManager::IsPointNearDockSite](../Topic/CDockingManager::IsPointNearDockSite.md)|确定指定的点是否在停靠站点附近。|  
|[CDockingManager::IsPrintPreviewValid](../Topic/CDockingManager::IsPrintPreviewValid.md)|确定打印预览模式是否设置为。|  
|[CDockingManager::LoadState](../Topic/CDockingManager::LoadState.md)|从注册表中加载停靠管理器状态。|  
|[CDockingManager::LockUpdate](../Topic/CDockingManager::LockUpdate.md)|锁定特定窗口。|  
|[CDockingManager::OnActivateFrame](../Topic/CDockingManager::OnActivateFrame.md)|调用由结构，当框架窗口进行激活或停用。|  
|[CDockingManager::OnClosePopupMenu](../Topic/CDockingManager::OnClosePopupMenu.md)|调用由结构，当一个有效的弹出菜单操作WM\_DESTROY消息。|  
|[CDockingManager::OnMoveMiniFrame](../Topic/CDockingManager::OnMoveMiniFrame.md)|调用由框架移动和框架窗口。|  
|[CDockingManager::OnPaneContextMenu](../Topic/CDockingManager::OnPaneContextMenu.md)|调用由结构，在生成具有窗格中列出的菜单。|  
|[CDockingManager::PaneFromPoint](../Topic/CDockingManager::PaneFromPoint.md)|返回包含给定的点窗格。|  
|[CDockingManager::ProcessPaneContextMenuCommand](../Topic/CDockingManager::ProcessPaneContextMenuCommand.md)|调用由框架选中或清除指定的命令的复选框和重新计算一个显示窗格的格式。|  
|[CDockingManager::RecalcLayout](../Topic/CDockingManager::RecalcLayout.md)|计算控件的内部格式当前在控件的列表。|  
|[CDockingManager::ReleaseEmptyPaneContainers](../Topic/CDockingManager::ReleaseEmptyPaneContainers.md)|释放空窗格容器。|  
|[CDockingManager::RemoveHiddenMDITabbedBar](../Topic/CDockingManager::RemoveHiddenMDITabbedBar.md)|移除指定的隐藏栏窗格。|  
|[CDockingManager::RemoveMiniFrame](../Topic/CDockingManager::RemoveMiniFrame.md)|从要帧列表中移除指定的帧。|  
|[CDockingManager::RemovePaneFromDockManager](../Topic/CDockingManager::RemovePaneFromDockManager.md)|注销窗格和在停靠管理器的列表中移除。|  
|[CDockingManager::ReplacePane](../Topic/CDockingManager::ReplacePane.md)|在调用代码中将一个窗格。|  
|[CDockingManager::ResortMiniFramesForZOrder](../Topic/CDockingManager::ResortMiniFramesForZOrder.md)|依赖要帧列表的帧。|  
|[CDockingManager::SaveState](../Topic/CDockingManager::SaveState.md)|保存停靠管理器状态对注册表。|  
|[CDockingManager::SendMessageToMiniFrames](../Topic/CDockingManager::SendMessageToMiniFrames.md)|发送指定的信息到任何要帧。|  
|[CDockingManager::Serialize](../Topic/CDockingManager::Serialize.md)|编写存档的停靠管理器。  （重写 [CObject::Serialize](../Topic/CObject::Serialize.md)。）|  
|[CDockingManager::SetAutohideZOrder](../Topic/CDockingManager::SetAutohideZOrder.md)|设置控件条与指定的窗格的大小、宽度和高度。|  
|[CDockingManager::SetDockingMode](../Topic/CDockingManager::SetDockingMode.md)|设置停靠模式。|  
|[CDockingManager::SetDockState](../Topic/CDockingManager::SetDockState.md)|设置控件条、mini框架和窗口栏的停靠状态。|  
|[CDockingManager::SetPrintPreviewMode](../Topic/CDockingManager::SetPrintPreviewMode.md)|设置在打印预览中显示栏的打印预览模式。|  
|[CDockingManager::SetSmartDockingParams](../Topic/CDockingManager::SetSmartDockingParams.md)|设置定义智能停靠行为的参数。|  
|[CDockingManager::ShowDelayShowMiniFrames](../Topic/CDockingManager::ShowDelayShowMiniFrames.md)|显示或隐藏mini帧的窗口。|  
|[CDockingManager::ShowPanes](../Topic/CDockingManager::ShowPanes.md)|显示或隐藏控件和窗口栏的窗格。|  
|[CDockingManager::StartSDocking](../Topic/CDockingManager::StartSDocking.md)|根据智能停靠管理器的对齐方式启动指定窗口的智能停靠。|  
|[CDockingManager::StopSDocking](../Topic/CDockingManager::StopSDocking.md)|停止智能停靠。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CDockingManager::m\_bHideDockingBarsInContainerMode](../Topic/CDockingManager::m_bHideDockingBarsInContainerMode.md)|指定停靠管理器是否在OLE容器模式隐藏窗格。|  
|[CDockingManager::m\_dockModeGlobal](../Topic/CDockingManager::m_dockModeGlobal.md)|指定全局停靠模式。|  
|[CDockingManager::m\_nDockSensitivity](../Topic/CDockingManager::m_nDockSensitivity.md)|指定停靠区分。|  
|[CDockingManager::m\_nTimeOutBeforeDockingBarDock](../Topic/CDockingManager::m_nTimeOutBeforeDockingBarDock.md)|在停靠窗格在直接停靠模式之前，停靠以毫秒为单位指定时间。|  
|[CDockingManager::m\_nTimeOutBeforeToolBarDock](../Topic/CDockingManager::m_nTimeOutBeforeToolBarDock.md)|在工具栏停靠到主框架窗口之前，以毫秒为单位指定时间。|  
  
## 备注  
 主框架窗口自动创建并初始化此选件类。  
  
 停靠管理器对象保存在停靠格式所有窗格的列表，并属于主框架窗口所有 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) 窗口的列表。  
  
 `CDockingManager` 选件类实现自己可以使用查找窗格或 `CPaneFrameWnd` 窗口的服务。  因为它们在主框架窗口对象，包装您通常不直接调用这些服务。  有关更多信息，请参见 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)。  
  
## 自定义提示  
 以下提示应用于 `CDockingManager` 对象:  
  
-   [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) 支持这些停靠模式:  
  
    -   `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    -   `AFX_DOCK_TYPE::DT_STANDARD`  
  
    -   `AFX_DOCK_TYPE::DT_SMART`  
  
     这些停靠模式由 [CDockingManager::m\_dockModeGlobal](../Topic/CDockingManager::m_dockModeGlobal.md) 定义的和通过调用 [CDockingManager::SetDockingMode](../Topic/CDockingManager::SetDockingMode.md)设置。  
  
-   如果要创建非浮点数，不可调整大小的窗格中，调用 [CDockingManager::AddPane](../Topic/CDockingManager::AddPane.md) 方法。  此方法注册了停靠管理器窗格中，负责窗格的格式。  
  
## 示例  
 下面的示例在 `CDockingManager` 选件类演示如何使用各种方案配置 `CDockingManager` 对象。  此示例演示如何打开在所有停靠窗格的声明一个弹出菜单中的其他按钮以及如何设置对象的停靠模式。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/CPP/cdockingmanager-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## 要求  
 **标头:** afxDockingManager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)