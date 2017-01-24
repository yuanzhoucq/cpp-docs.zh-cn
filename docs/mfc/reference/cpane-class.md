---
title: "CPane Class | Microsoft Docs"
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
  - "CPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPane class"
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CPane` 选件类是 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)增强功能。  如果升级现有MFC项目，请在 `CPane`替换 `CControlBar` 所有匹配项。  
  
## 语法  
  
```  
class CPane : public CBasePane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CPane::~CPane`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPane::AdjustSizeImmediate](../Topic/CPane::AdjustSizeImmediate.md)|立即计算窗格的格式。|  
|[CPane::AllocElements](../Topic/CPane::AllocElements.md)|分配存储区以供内部使用。|  
|[CPane::AllowShowOnPaneMenu](../Topic/CPane::AllowShowOnPaneMenu.md)|指定窗格是在运行时生成的列表应用程序的窗格中。|  
|[CPane::CalcAvailableSize](../Topic/CPane::CalcAvailableSize.md)|的大小计算差异在指定的矩形和当前窗口矩形之间。|  
|[CPane::CalcInsideRect](../Topic/CPane::CalcInsideRect.md)|计算窗格中的矩形，考虑边框和手柄。|  
|[CPane::CalcRecentDockedRect](../Topic/CPane::CalcRecentDockedRect.md)|计算最近的停靠的矩形。|  
|[CPane::CalcSize](../Topic/CPane::CalcSize.md)|计算窗格的大小。|  
|[CPane::CanBeDocked](../Topic/CPane::CanBeDocked.md)|确定窗格是否可以停靠在指定的基本窗格。|  
|[CPane::CanBeTabbedDocument](../Topic/CPane::CanBeTabbedDocument.md)|确定窗格是否可以转换为选项卡式文档。|  
|[CPane::ConvertToTabbedDocument](../Topic/CPane::ConvertToTabbedDocument.md)|将停靠窗格为选项卡式文档。|  
|[CPane::CopyState](../Topic/CPane::CopyState.md)|复制窗格的状态。  （重写 [CBasePane::CopyState](../Topic/CBasePane::CopyState.md)。）|  
|[CPane::Create](../Topic/CPane::Create.md)|创建一个控件条并将它附加到 `CPane` 对象。|  
|[CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md)|创建一个浮动窗格中的和框架窗口。|  
|[CPane::CreateEx](../Topic/CPane::CreateEx.md)|创建一个控件条并将它附加到 `CPane` 对象。|  
|`CPane::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CPane::DockByMouse](../Topic/CPane::DockByMouse.md)|使用鼠标停靠方法，停靠一个窗格。|  
|[CPane::DockPane](../Topic/CPane::DockPane.md)|停靠浮动窗格到一个基本窗格。|  
|[CPane::DockPaneStandard](../Topic/CPane::DockPaneStandard.md)|使用大纲\(标准\)停靠，停靠一个窗格。|  
|[CPane::DockToFrameWindow](../Topic/CPane::DockToFrameWindow.md)|停靠一个窗格停靠到框架。  （重写 `CBasePane::DockToFrameWindow`。）|  
|[CPane::DoesAllowSiblingBars](../Topic/CPane::DoesAllowSiblingBars.md)|指示是否可以停靠另一个窗格在当前窗格停靠的同一行。|  
|[CPane::FloatPane](../Topic/CPane::FloatPane.md)|浮动窗格。|  
|[CPane::GetAvailableExpandSize](../Topic/CPane::GetAvailableExpandSize.md)|返回金额，以像素为单位\)，窗格可以展开。|  
|[CPane::GetAvailableStretchSize](../Topic/CPane::GetAvailableStretchSize.md)|返回金额，以像素为单位\)，窗格可以缩小。|  
|[CPane::GetBorders](../Topic/CPane::GetBorders.md)|返回窗格的边框的宽度。|  
|[CPane::GetClientHotSpot](../Topic/CPane::GetClientHotSpot.md)|返回窗格的 *作用点*。|  
|[CPane::GetDockSiteRow](../Topic/CPane::GetDockSiteRow.md)|返回窗格停靠的停靠行。|  
|[CPane::GetExclusiveRowMode](../Topic/CPane::GetExclusiveRowMode.md)|确定窗格是否在独占行模式。|  
|[CPane::GetHotSpot](../Topic/CPane::GetHotSpot.md)|返回在基础 `CMFCDragFrameImpl` 对象存储的作用点。|  
|[CPane::GetMinSize](../Topic/CPane::GetMinSize.md)|检索窗格的最小值允许的范围。|  
|[CPane::GetPaneName](../Topic/CPane::GetPaneName.md)|检索窗格的标题。|  
|`CPane::GetResizeStep`|内部使用。|  
|`CPane::GetThisClass`|用于由框架获取指向与此选件类类型的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 对象。|  
|[CPane::GetVirtualRect](../Topic/CPane::GetVirtualRect.md)|检索窗格的 *虚拟矩形*。|  
|[CPane::IsChangeState](../Topic/CPane::IsChangeState.md)|在窗格中移动，此方法分析窗格的位置相对于其他窗格，停靠行和和框架窗口，并返回相应的 `AFX_CS_STATUS` 值。|  
|[CPane::IsDragMode](../Topic/CPane::IsDragMode.md)|指定窗格是否已拖动。|  
|[CPane::IsInFloatingMultiPaneFrameWnd](../Topic/CPane::IsInFloatingMultiPaneFrameWnd.md)|指定窗格是否在多窗格框架窗口。  （重写 `CBasePane::IsInFloatingMultiPaneFrameWnd`。）|  
|[CPane::IsLeftOf](../Topic/CPane::IsLeftOf.md)|确定是否窗格左侧\(如\)所指定的矩形。|  
|[CPane::IsResizable](../Topic/CPane::IsResizable.md)|确定窗格是否可调整大小。  （重写 [CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)。）|  
|[CPane::IsTabbed](../Topic/CPane::IsTabbed.md)|确定窗格是在一个选项卡式窗口的选项卡控件插入了。  （重写 [CBasePane::IsTabbed](../Topic/CBasePane::IsTabbed.md)。）|  
|[CPane::LoadState](../Topic/CPane::LoadState.md)|从注册表填充窗格的状态。  （重写 [CBasePane::LoadState](../Topic/CBasePane::LoadState.md)。）|  
|[CPane::MoveByAlignment](../Topic/CPane::MoveByAlignment.md)|该指定的量移动窗格和虚拟矩形。|  
|[CPane::MovePane](../Topic/CPane::MovePane.md)|移动窗格更改为指定的矩形。|  
|[CPane::OnAfterChangeParent](../Topic/CPane::OnAfterChangeParent.md)|调用由结构，在窗格的父级更改为。|  
|[CPane::OnBeforeChangeParent](../Topic/CPane::OnBeforeChangeParent.md)|调用由结构，在窗格的父会发生更改。|  
|[CPane::OnPressCloseButton](../Topic/CPane::OnPressCloseButton.md)|调用由结构，当用户选择中的"关闭"窗格中。|  
|`CPane::OnProcessDblClk`|内部使用。|  
|[CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)|调用由结构，在特定窗格菜单中显示。|  
|[CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)|调用由结构，在特定窗格菜单中显示。|  
|`CPane::PrepareToDock`|内部使用。|  
|[CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)|计算窗格的格式信息。  （重写 [CBasePane::RecalcLayout](../Topic/CBasePane::RecalcLayout.md)。）|  
|[CPane::SaveState](../Topic/CPane::SaveState.md)|保存窗格的状态对注册表。  （重写 [CBasePane::SaveState](../Topic/CBasePane::SaveState.md)。）|  
|[CPane::SetActiveInGroup](../Topic/CPane::SetActiveInGroup.md)|标记窗格为活动分配。|  
|[CPane::SetBorders](../Topic/CPane::SetBorders.md)|设置窗格的边框值。|  
|[CPane::SetClientHotSpot](../Topic/CPane::SetClientHotSpot.md)|设置窗格的作用点。|  
|[CPane::SetDockState](../Topic/CPane::SetDockState.md)|停靠窗格的还原状态信息。|  
|[CPane::SetExclusiveRowMode](../Topic/CPane::SetExclusiveRowMode.md)|启动或禁用独占行模式。|  
|[CPane::SetMiniFrameRTC](../Topic/CPane::SetMiniFrameRTC.md)|设置默认和框架窗口的运行时选件类信息。|  
|[CPane::SetMinSize](../Topic/CPane::SetMinSize.md)|设置窗格的最小值允许的范围。|  
|[CPane::SetVirtualRect](../Topic/CPane::SetVirtualRect.md)|设置窗格的 *虚拟矩形*。|  
|[CPane::StretchPaneDeferWndPos](../Topic/CPane::StretchPaneDeferWndPos.md)|拉伸窗格垂直或水平基于停靠样式。|  
|[CPane::ToggleAutoHide](../Topic/CPane::ToggleAutoHide.md)|触发器自动隐藏模式。|  
|[CPane::UndockPane](../Topic/CPane::UndockPane.md)|从其当前停靠的停靠站点、默认滑块或服务器框架窗口移除窗格。  （重写 [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)。）|  
|[CPane::UpdateVirtualRect](../Topic/CPane::UpdateVirtualRect.md)|更新虚拟矩形。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CPane::OnAfterDock](../Topic/CPane::OnAfterDock.md)|调用由结构，当窗格停靠的。|  
|[CPane::OnAfterFloat](../Topic/CPane::OnAfterFloat.md)|调用由结构，在窗格中浮动的。|  
|[CPane::OnBeforeDock](../Topic/CPane::OnBeforeDock.md)|调用由结构，当窗格将停靠。|  
|[CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md)|调用由结构，当窗格将浮动。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPane::m\_bHandleMinSize](../Topic/CPane::m_bHandleMinSize.md)|启用一致处理窗格的最小尺寸。|  
|[CPane::m\_recentDockInfo](../Topic/CPane::m_recentDockInfo.md)|包含新停靠信息。|  
  
## 备注  
 通常，`CPane` 对象不直接实例化。  如果需要具有停靠函数的一个窗格，请从 [CDockablePane](../../mfc/reference/cdockablepane-class.md)派生您的对象。  如果需要工具栏功能，从 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)派生您的对象。  
  
 当从 `CPane`派生时选件类，它在 [CDockSite](../../mfc/reference/cdocksite-class.md) 可以停靠，并在 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)可以将浮动。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## 要求  
 **标头:** afxPane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)