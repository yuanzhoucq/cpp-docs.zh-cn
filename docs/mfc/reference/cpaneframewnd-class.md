---
title: "CPaneFrameWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaneFrameWnd.Serialize"
  - "CPaneFrameWnd.PreTranslateMessage"
  - "CPaneFrameWnd"
  - "CPaneFrameWnd::Serialize"
  - "PreTranslateMessage"
  - "CPaneFrameWnd::PreTranslateMessage"
  - "Serialize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneFrameWnd class"
  - "PreTranslateMessage method"
  - "Serialize method"
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CPaneFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 实现包含一个窗格的微型框架窗口。  此窗格填满窗口的工作区。  
  
## 语法  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPaneFrameWnd::AddPane](../Topic/CPaneFrameWnd::AddPane.md)|添加窗格。|  
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](../Topic/CPaneFrameWnd::AddRemovePaneFromGlobalList.md)|从全局列表添加或删除窗格。|  
|[CPaneFrameWnd::AdjustLayout](../Topic/CPaneFrameWnd::AdjustLayout.md)|调整微型框架窗口的布局。|  
|[CPaneFrameWnd::AdjustPaneFrames](../Topic/CPaneFrameWnd::AdjustPaneFrames.md)||  
|[CPaneFrameWnd::CalcBorderSize](../Topic/CPaneFrameWnd::CalcBorderSize.md)|计算微型框架窗口的边框大小。|  
|[CPaneFrameWnd::CalcExpectedDockedRect](../Topic/CPaneFrameWnd::CalcExpectedDockedRect.md)|计算停靠窗口的预期矩形。|  
|[CPaneFrameWnd::CanBeAttached](../Topic/CPaneFrameWnd::CanBeAttached.md)|确定是否可将当前窗格停靠到另一个窗格或框架窗口。|  
|[CPaneFrameWnd::CanBeDockedToPane](../Topic/CPaneFrameWnd::CanBeDockedToPane.md)|确定是否可将微型框架窗口停靠到窗格。|  
|[CPaneFrameWnd::CheckGripperVisibility](../Topic/CPaneFrameWnd::CheckGripperVisibility.md)||  
|[CPaneFrameWnd::ConvertToTabbedDocument](../Topic/CPaneFrameWnd::ConvertToTabbedDocument.md)|将窗格转换为选项卡式文档。|  
|[CPaneFrameWnd::Create](../Topic/CPaneFrameWnd::Create.md)|创建微型框架窗口，并将其附加到 `CPaneFrameWnd` 对象。|  
|[CPaneFrameWnd::CreateEx](../Topic/CPaneFrameWnd::CreateEx.md)|创建微型框架窗口，并将其附加到 `CPaneFrameWnd` 对象。|  
|[CPaneFrameWnd::DockPane](../Topic/CPaneFrameWnd::DockPane.md)|停靠窗格。|  
|[CPaneFrameWnd::FindFloatingPaneByID](../Topic/CPaneFrameWnd::FindFloatingPaneByID.md)|在浮动窗格的全局列表中查找具有指定控件 ID 的窗格。|  
|[CPaneFrameWnd::FrameFromPoint](../Topic/CPaneFrameWnd::FrameFromPoint.md)|查找包含用户提供的点的微型框架窗口。|  
|[CPaneFrameWnd::GetCaptionHeight](../Topic/CPaneFrameWnd::GetCaptionHeight.md)|返回微型框架窗口标题的高度。|  
|[CPaneFrameWnd::GetCaptionRect](../Topic/CPaneFrameWnd::GetCaptionRect.md)|计算微型框架窗口标题的边框矩形。|  
|[CPaneFrameWnd::GetCaptionText](../Topic/CPaneFrameWnd::GetCaptionText.md)|返回标题文本。|  
|[CPaneFrameWnd::GetDockingManager](../Topic/CPaneFrameWnd::GetDockingManager.md)||  
|[CPaneFrameWnd::GetDockingMode](../Topic/CPaneFrameWnd::GetDockingMode.md)|返回停靠模式。|  
|[CPaneFrameWnd::GetFirstVisiblePane](../Topic/CPaneFrameWnd::GetFirstVisiblePane.md)|返回包含在微型框架窗口中的第一个可见窗格。|  
|[CPaneFrameWnd::GetHotPoint](../Topic/CPaneFrameWnd::GetHotPoint.md)||  
|[CPaneFrameWnd::GetPane](../Topic/CPaneFrameWnd::GetPane.md)|返回包含在微型框架窗口中的窗格。|  
|[CPaneFrameWnd::GetPaneCount](../Topic/CPaneFrameWnd::GetPaneCount.md)|返回包含在微型框架窗口中的窗格数。|  
|[CPaneFrameWnd::GetParent](../Topic/CPaneFrameWnd::GetParent.md)||  
|[CPaneFrameWnd::GetPinState](../Topic/CPaneFrameWnd::GetPinState.md)||  
|[CPaneFrameWnd::GetRecentFloatingRect](../Topic/CPaneFrameWnd::GetRecentFloatingRect.md)||  
|[CPaneFrameWnd::GetVisiblePaneCount](../Topic/CPaneFrameWnd::GetVisiblePaneCount.md)|返回包含在微型框架窗口中的可见窗格数。|  
|[CPaneFrameWnd::HitTest](../Topic/CPaneFrameWnd::HitTest.md)|确定微型框架窗口的哪一部分位于给定点。|  
|[CPaneFrameWnd::IsCaptured](../Topic/CPaneFrameWnd::IsCaptured.md)||  
|[CPaneFrameWnd::IsDelayShow](../Topic/CPaneFrameWnd::IsDelayShow.md)||  
|[CPaneFrameWnd::IsRollDown](../Topic/CPaneFrameWnd::IsRollDown.md)|确定是否应下滚微型框架窗口。|  
|[CPaneFrameWnd::IsRollUp](../Topic/CPaneFrameWnd::IsRollUp.md)|确定是否应上滚微型框架窗口。|  
|[CPaneFrameWnd::KillDockingTimer](../Topic/CPaneFrameWnd::KillDockingTimer.md)|停止停靠计时器。|  
|[CPaneFrameWnd::LoadState](../Topic/CPaneFrameWnd::LoadState.md)|从注册表加载窗格的状态。|  
|[CPaneFrameWnd::OnBeforeDock](../Topic/CPaneFrameWnd::OnBeforeDock.md)|确定停靠是否可能。|  
|[CPaneFrameWnd::OnDockToRecentPos](../Topic/CPaneFrameWnd::OnDockToRecentPos.md)|将微型框架窗口停靠在其最新的位置。|  
|[CPaneFrameWnd::OnKillRollUpTimer](../Topic/CPaneFrameWnd::OnKillRollUpTimer.md)|停止汇总计时器。|  
|[CPaneFrameWnd::OnMovePane](../Topic/CPaneFrameWnd::OnMovePane.md)|按指定偏移量移动微型框架窗口。|  
|[CPaneFrameWnd::OnPaneRecalcLayout](../Topic/CPaneFrameWnd::OnPaneRecalcLayout.md)|调整包含的窗格的布局。|  
|[CPaneFrameWnd::OnSetRollUpTimer](../Topic/CPaneFrameWnd::OnSetRollUpTimer.md)|设置汇总计时器。|  
|[CPaneFrameWnd::OnShowPane](../Topic/CPaneFrameWnd::OnShowPane.md)|隐藏或显示微型框架窗口的窗格时，由框架进行调用。|  
|[CPaneFrameWnd::PaneFromPoint](../Topic/CPaneFrameWnd::PaneFromPoint.md)|如果窗格在微型框架窗口内包含用户提供的点，则返回窗格。|  
|[CPaneFrameWnd::Pin](../Topic/CPaneFrameWnd::Pin.md)||  
|`CPaneFrameWnd::PreTranslateMessage`|在窗口消息被发送到 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数之前，由 [CWinApp](../../mfc/reference/cwinapp-class.md) 类用于对该窗口消息进行转换。|  
|[CPaneFrameWnd::RedrawAll](../Topic/CPaneFrameWnd::RedrawAll.md)|重绘所有微型框架窗口。|  
|[CPaneFrameWnd::RemoveNonValidPanes](../Topic/CPaneFrameWnd::RemoveNonValidPanes.md)|由框架调用以删除非有效窗格。|  
|[CPaneFrameWnd::RemovePane](../Topic/CPaneFrameWnd::RemovePane.md)|从微型框架窗口删除窗格。|  
|[CPaneFrameWnd::ReplacePane](../Topic/CPaneFrameWnd::ReplacePane.md)|用一个窗格替换另一个窗格。|  
|[CPaneFrameWnd::SaveState](../Topic/CPaneFrameWnd::SaveState.md)|将窗格的状态保存到注册表。|  
|`CPaneFrameWnd::Serialize`|从存档读取该对象或将该对象写入存档。|  
|[CPaneFrameWnd::SetCaptionButtons](../Topic/CPaneFrameWnd::SetCaptionButtons.md)|设置标题按钮。|  
|[CPaneFrameWnd::SetDelayShow](../Topic/CPaneFrameWnd::SetDelayShow.md)||  
|[CPaneFrameWnd::SetDockingManager](../Topic/CPaneFrameWnd::SetDockingManager.md)||  
|[CPaneFrameWnd::SetDockingTimer](../Topic/CPaneFrameWnd::SetDockingTimer.md)|设置停靠计时器。|  
|[CPaneFrameWnd::SetDockState](../Topic/CPaneFrameWnd::SetDockState.md)|设置停靠状态。|  
|[CPaneFrameWnd::SetHotPoint](../Topic/CPaneFrameWnd::SetHotPoint.md)||  
|[CPaneFrameWnd::SetPreDockState](../Topic/CPaneFrameWnd::SetPreDockState.md)|由框架调用以设置预停靠状态。|  
|[CPaneFrameWnd::SizeToContent](../Topic/CPaneFrameWnd::SizeToContent.md)|调整微型框架窗口大小，使其大小等于包含窗格的大小。|  
|[CPaneFrameWnd::StartTearOff](../Topic/CPaneFrameWnd::StartTearOff.md)|移走菜单。|  
|[CPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CPaneFrameWnd::StoreRecentDockSiteInfo.md)||  
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CPaneFrameWnd::StoreRecentTabRelatedInfo.md)||  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CPaneFrameWnd::OnCheckRollState](../Topic/CPaneFrameWnd::OnCheckRollState.md)|确定是否应上滚或下滚微型框架窗口。|  
|[CPaneFrameWnd::OnDrawBorder](../Topic/CPaneFrameWnd::OnDrawBorder.md)|绘制微型框架窗口的边框。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPaneFrameWnd::m\_bUseSaveBits](../Topic/CPaneFrameWnd::m_bUseSaveBits.md)|指定是否注册具有 `CS_SAVEBITS` 类样式的窗口类。|  
  
## 备注  
 当窗格从停靠状态切换到浮动状态时，框架会自动创建 `CPaneFrameWnd` 对象。  
  
 可使用其可见内容（立即停靠）或拖动矩形（标准停靠）来拖动微型框架窗口。  微型框架的容器窗格的停靠模式确定微型框架的拖动行为。  有关详细信息，请参阅 [CBasePane::GetDockingMode](../Topic/CBasePane::GetDockingMode.md)。  
  
 微型框架窗口根据包含的窗格样式在标题上显示按钮。  如果可以关闭窗格 \([CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)\)，它将显示“关闭”按钮。  如果窗格具有 `AFX_CBRS_AUTO_ROLLUP` 样式，它将显示指针。  
  
 如果从 `CPaneFrameWnd` 派生类，则必须告诉框架如何创建类。  通过重写 [CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md) 创建类，或设置 `CPane::m_pMiniFrameRTC` 成员使其指向类的运行时类信息。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
## 要求  
 **标头：**afxPaneFrameWnd.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)