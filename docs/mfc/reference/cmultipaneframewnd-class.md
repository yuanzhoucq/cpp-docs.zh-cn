---
title: "CMultiPaneFrameWnd Class | Microsoft Docs"
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
  - "CMultiPaneFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiPaneFrameWnd class"
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
caps.latest.revision: 36
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiPaneFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMultiPaneFrameWnd` 选件类扩展 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)。  它可以支持多个窗格。  而不是控件条的一个嵌入处理，`CMultiPaneFrameWnd` 包含使用户能够停靠一 `CMultiPaneFrameWnd` 到另一个和动态创建多个浮动的一 [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md) 对象，选项卡式窗口。  
  
## 语法  
  
```  
class CMultiPaneFrameWnd : public CPaneFrameWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMultiPaneFrameWnd::AddPane](../Topic/CMultiPaneFrameWnd::AddPane.md)|添加一个窗格。  （重写 [CPaneFrameWnd::AddPane](../Topic/CPaneFrameWnd::AddPane.md)。）|  
|[CMultiPaneFrameWnd::AddRecentPane](../Topic/CMultiPaneFrameWnd::AddRecentPane.md)||  
|[CMultiPaneFrameWnd::AdjustLayout](../Topic/CMultiPaneFrameWnd::AdjustLayout.md)|调整和框架窗口的格式。  （重写 [CPaneFrameWnd::AdjustLayout](../Topic/CPaneFrameWnd::AdjustLayout.md)。）|  
|[CMultiPaneFrameWnd::AdjustPaneFrames](../Topic/CMultiPaneFrameWnd::AdjustPaneFrames.md)|（重写 [CPaneFrameWnd::AdjustPaneFrames](../Topic/CPaneFrameWnd::AdjustPaneFrames.md)。）|  
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](../Topic/CMultiPaneFrameWnd::CalcExpectedDockedRect.md)|计算一停靠窗口的预期的矩形。  （重写 [CPaneFrameWnd::CalcExpectedDockedRect](../Topic/CPaneFrameWnd::CalcExpectedDockedRect.md)。）|  
|[CMultiPaneFrameWnd::CanBeAttached](../Topic/CMultiPaneFrameWnd::CanBeAttached.md)|确定当前窗格是否可以停靠到另一个窗格或框架窗口。  （重写 [CPaneFrameWnd::CanBeAttached](../Topic/CPaneFrameWnd::CanBeAttached.md)。）|  
|[CMultiPaneFrameWnd::CanBeDockedToPane](../Topic/CMultiPaneFrameWnd::CanBeDockedToPane.md)|确定和框架窗口是否可以停靠到窗格中。  （重写 [CPaneFrameWnd::CanBeDockedToPane](../Topic/CPaneFrameWnd::CanBeDockedToPane.md)。）|  
|[CMultiPaneFrameWnd::CheckGripperVisibility](../Topic/CMultiPaneFrameWnd::CheckGripperVisibility.md)|（重写 [CPaneFrameWnd::CheckGripperVisibility](../Topic/CPaneFrameWnd::CheckGripperVisibility.md)。）|  
|[CMultiPaneFrameWnd::CloseMiniFrame](../Topic/CMultiPaneFrameWnd::CloseMiniFrame.md)|（重写 `CPaneFrameWnd::CloseMiniFrame`。）|  
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](../Topic/CMultiPaneFrameWnd::ConvertToTabbedDocument.md)|转换窗格为选项卡式文档。  （重写 [CPaneFrameWnd::ConvertToTabbedDocument](../Topic/CPaneFrameWnd::ConvertToTabbedDocument.md)。）|  
|[CMultiPaneFrameWnd::DockFrame](../Topic/CMultiPaneFrameWnd::DockFrame.md)||  
|[CMultiPaneFrameWnd::DockPane](../Topic/CMultiPaneFrameWnd::DockPane.md)|停靠窗格。  （重写 [CPaneFrameWnd::DockPane](../Topic/CPaneFrameWnd::DockPane.md)。）|  
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](../Topic/CMultiPaneFrameWnd::DockRecentPaneToMainFrame.md)||  
|[CMultiPaneFrameWnd::GetCaptionText](../Topic/CMultiPaneFrameWnd::GetCaptionText.md)|返回标题文本。  （重写 [CPaneFrameWnd::GetCaptionText](../Topic/CPaneFrameWnd::GetCaptionText.md)。）|  
|[CMultiPaneFrameWnd::GetPaneContainerManager](../Topic/CMultiPaneFrameWnd::GetPaneContainerManager.md)|返回对内部容器管理器对象。|  
|[CMultiPaneFrameWnd::GetFirstVisiblePane](../Topic/CMultiPaneFrameWnd::GetFirstVisiblePane.md)|返回袖珍框架窗口中包含的第一个窗格可见。  （重写 [CPaneFrameWnd::GetFirstVisiblePane](../Topic/CPaneFrameWnd::GetFirstVisiblePane.md)。）|  
|[CMultiPaneFrameWnd::GetPane](../Topic/CMultiPaneFrameWnd::GetPane.md)|返回袖珍框架窗口中包含的窗格。  （重写 [CPaneFrameWnd::GetPane](../Topic/CPaneFrameWnd::GetPane.md)。）|  
|[CMultiPaneFrameWnd::GetPaneCount](../Topic/CMultiPaneFrameWnd::GetPaneCount.md)|返回袖珍框架窗口包含窗格的数目。  （重写 [CPaneFrameWnd::GetPaneCount](../Topic/CPaneFrameWnd::GetPaneCount.md)。）|  
|[CMultiPaneFrameWnd::GetVisiblePaneCount](../Topic/CMultiPaneFrameWnd::GetVisiblePaneCount.md)|返回袖珍框架窗口包含可见窗格的数目。  （重写 [CPaneFrameWnd::GetVisiblePaneCount](../Topic/CPaneFrameWnd::GetVisiblePaneCount.md)。）|  
|[CMultiPaneFrameWnd::InsertPane](../Topic/CMultiPaneFrameWnd::InsertPane.md)||  
|[CMultiPaneFrameWnd::LoadState](../Topic/CMultiPaneFrameWnd::LoadState.md)|从注册表填充窗格的状态。  （重写 [CPaneFrameWnd::LoadState](../Topic/CPaneFrameWnd::LoadState.md)。）|  
|[CMultiPaneFrameWnd::OnDockToRecentPos](../Topic/CMultiPaneFrameWnd::OnDockToRecentPos.md)|停靠和框架窗口在其新位置。  （重写 [CPaneFrameWnd::OnDockToRecentPos](../Topic/CPaneFrameWnd::OnDockToRecentPos.md)。）|  
|[CMultiPaneFrameWnd::OnKillRollUpTimer](../Topic/CMultiPaneFrameWnd::OnKillRollUpTimer.md)|停止汇总计时器。  （重写 [CPaneFrameWnd::OnKillRollUpTimer](../Topic/CPaneFrameWnd::OnKillRollUpTimer.md)。）|  
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](../Topic/CMultiPaneFrameWnd::OnPaneRecalcLayout.md)|调整一个窗格的格式袖珍框架窗口中。  （重写 [CPaneFrameWnd::OnPaneRecalcLayout](../Topic/CPaneFrameWnd::OnPaneRecalcLayout.md)。）|  
|[CMultiPaneFrameWnd::OnSetRollUpTimer](../Topic/CMultiPaneFrameWnd::OnSetRollUpTimer.md)|设置汇总计时器。  （重写 [CPaneFrameWnd::OnSetRollUpTimer](../Topic/CPaneFrameWnd::OnSetRollUpTimer.md)。）|  
|[CMultiPaneFrameWnd::OnShowPane](../Topic/CMultiPaneFrameWnd::OnShowPane.md)|调用由结构，当袖珍框架窗口的一个窗格隐藏或显示。  （重写 [CPaneFrameWnd::OnShowPane](../Topic/CPaneFrameWnd::OnShowPane.md)。）|  
|[CMultiPaneFrameWnd::PaneFromPoint](../Topic/CMultiPaneFrameWnd::PaneFromPoint.md)|如果它包含一个用户提供点袖珍框架窗口中，返回窗格。  （重写 [CPaneFrameWnd::PaneFromPoint](../Topic/CPaneFrameWnd::PaneFromPoint.md)。）|  
|[CMultiPaneFrameWnd::RemoveNonValidPanes](../Topic/CMultiPaneFrameWnd::RemoveNonValidPanes.md)|调用由结构移除非活动窗格。  （重写 [CPaneFrameWnd::RemoveNonValidPanes](../Topic/CPaneFrameWnd::RemoveNonValidPanes.md)。）|  
|[CMultiPaneFrameWnd::RemovePane](../Topic/CMultiPaneFrameWnd::RemovePane.md)|从和框架窗口移除窗格。  （重写 [CPaneFrameWnd::RemovePane](../Topic/CPaneFrameWnd::RemovePane.md)。）|  
|[CMultiPaneFrameWnd::ReplacePane](../Topic/CMultiPaneFrameWnd::ReplacePane.md)|在调用代码中将一个窗格。  （重写 [CPaneFrameWnd::ReplacePane](../Topic/CPaneFrameWnd::ReplacePane.md)。）|  
|[CMultiPaneFrameWnd::SaveState](../Topic/CMultiPaneFrameWnd::SaveState.md)|保存窗格的状态对注册表。  （重写 [CPaneFrameWnd::SaveState](../Topic/CPaneFrameWnd::SaveState.md)。）|  
|[CMultiPaneFrameWnd::Serialize](../Topic/CMultiPaneFrameWnd::Serialize.md)|（重写 `CPaneFrameWnd::Serialize`。）|  
|[CMultiPaneFrameWnd::SetDockState](../Topic/CMultiPaneFrameWnd::SetDockState.md)|设置停靠状态。  （重写 [CPaneFrameWnd::SetDockState](../Topic/CPaneFrameWnd::SetDockState.md)。）|  
|[CMultiPaneFrameWnd::SetLastFocusedPane](../Topic/CMultiPaneFrameWnd::SetLastFocusedPane.md)||  
|[CMultiPaneFrameWnd::SetPreDockState](../Topic/CMultiPaneFrameWnd::SetPreDockState.md)|将predocking的状态。  （重写 [CPaneFrameWnd::SetPreDockState](../Topic/CPaneFrameWnd::SetPreDockState.md)。）|  
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CMultiPaneFrameWnd::StoreRecentDockSiteInfo.md)|（重写 [CPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CPaneFrameWnd::StoreRecentDockSiteInfo.md)。）|  
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo.md)|（重写 [CPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CPaneFrameWnd::StoreRecentTabRelatedInfo.md)。）|  
  
## 备注  
 大多数本选件类重写方法的方法在 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md) 选件类。  
  
 如果窗格使用而不管其他停靠窗格的样式设置，该窗格到多窗格框架窗口，用户可以汇总窗口的 `AFX_CBRS_AUTO_ROLLUP` 样式和用户停靠。  
  
 框架自动创建一 `CMultiPaneFrameWnd` 对象，当用户浮动使用 `CBRS_FLOAT_MULTI` 样式的窗格。  
  
 有关动态选件派生类从 `CPaneFrameWnd` 选件类和创建该控件的信息，请参见 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。  
  
## 示例  
 下面的示例演示如何检索指向 `CMultiPaneFrameWnd` 对象。  此代码段是 [设置窗格大小示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/CPP/cmultipaneframewnd-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
 [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)  
  
## 要求  
 **标头:** afxMultiPaneFrameWnd.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)