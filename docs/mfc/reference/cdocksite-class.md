---
title: "CDockSite Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockSite class"
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CDockSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 提供用于排列从 [CPane Class](../../mfc/reference/cpane-class.md)派生至多组行的窗格的功能。  
  
## 语法  
  
```  
class CDockSite: public CBasePane  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CDockSite::AddRow](../Topic/CDockSite::AddRow.md)||  
|[CDockSite::AdjustDockingLayout](../Topic/CDockSite::AdjustDockingLayout.md)|（替代 [CBasePane::AdjustDockingLayout](../Topic/CBasePane::AdjustDockingLayout.md)。）|  
|[CDockSite::AdjustLayout](../Topic/CDockSite::AdjustLayout.md)|（替代 [CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)。）|  
|[CDockSite::AlignDockSite](../Topic/CDockSite::AlignDockSite.md)||  
|[CDockSite::CalcFixedLayout](../Topic/CDockSite::CalcFixedLayout.md)|（替代 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。）|  
|[CDockSite::CanAcceptPane](../Topic/CDockSite::CanAcceptPane.md)|（替代 [CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)。）|  
|[CDockSite::CreateEx](../Topic/CDockSite::CreateEx.md)|（替代 [CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)。）|  
|[CDockSite::CreateRow](../Topic/CDockSite::CreateRow.md)||  
|[CDockSite::DockPane](../Topic/CDockSite::DockPane.md)|（替代 [CBasePane::DockPane](../Topic/CBasePane::DockPane.md)。）|  
|[CDockSite::DoesAllowDynInsertBefore](../Topic/CDockSite::DoesAllowDynInsertBefore.md)|（替代 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)。）|  
|[CDockSite::FindRowIndex](../Topic/CDockSite::FindRowIndex.md)||  
|[CDockSite::FixupVirtualRects](../Topic/CDockSite::FixupVirtualRects.md)||  
|[CDockSite::GetDockSiteID](../Topic/CDockSite::GetDockSiteID.md)||  
|[CDockSite::GetDockSiteRowsList](../Topic/CDockSite::GetDockSiteRowsList.md)||  
|[CDockSite::IsAccessibilityCompatible](../Topic/CDockSite::IsAccessibilityCompatible.md)|（重写 `CBasePane::IsAccessibilityCompatible`。）|  
|[CDockSite::IsDragMode](../Topic/CDockSite::IsDragMode.md)||  
|[CDockSite::IsLastRow](../Topic/CDockSite::IsLastRow.md)||  
|[CDockSite::IsRectWithinDockSite](../Topic/CDockSite::IsRectWithinDockSite.md)||  
|[CDockSite::IsResizable](../Topic/CDockSite::IsResizable.md)|（替代 [CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)。）|  
|[CDockSite::MovePane](../Topic/CDockSite::MovePane.md)||  
|[CDockSite::OnInsertRow](../Topic/CDockSite::OnInsertRow.md)||  
|[CDockSite::OnRemoveRow](../Topic/CDockSite::OnRemoveRow.md)||  
|[CDockSite::OnResizeRow](../Topic/CDockSite::OnResizeRow.md)||  
|[CDockSite::OnSetWindowPos](../Topic/CDockSite::OnSetWindowPos.md)||  
|[CDockSite::OnShowRow](../Topic/CDockSite::OnShowRow.md)||  
|[CDockSite::OnSizeParent](../Topic/CDockSite::OnSizeParent.md)||  
|[CDockSite::PaneFromPoint](../Topic/CDockSite::PaneFromPoint.md)|返回在停靠站点中给定参数指定的点处停靠的窗格。|  
|[CDockSite::DockPaneLeftOf](../Topic/CDockSite::DockPaneLeftOf.md)|将窗格停靠到另一个窗格的左侧。|  
|[CDockSite::FindPaneByID](../Topic/CDockSite::FindPaneByID.md)|返回由给定 ID 标识的窗格。|  
|[CDockSite::GetPaneList](../Topic/CDockSite::GetPaneList.md)|返回停靠在停靠站点的窗格列表。|  
|[CDockSite::RectSideFromPoint](../Topic/CDockSite::RectSideFromPoint.md)||  
|[CDockSite::RemovePane](../Topic/CDockSite::RemovePane.md)||  
|[CDockSite::RemoveRow](../Topic/CDockSite::RemoveRow.md)||  
|[CDockSite::ReplacePane](../Topic/CDockSite::ReplacePane.md)||  
|[CDockSite::RepositionPanes](../Topic/CDockSite::RepositionPanes.md)||  
|[CDockSite::ResizeDockSite](../Topic/CDockSite::ResizeDockSite.md)||  
|[CDockSite::ResizeRow](../Topic/CDockSite::ResizeRow.md)||  
|[CDockSite::ShowPane](../Topic/CDockSite::ShowPane.md)|显示窗格。|  
|[CDockSite::ShowRow](../Topic/CDockSite::ShowRow.md)||  
|[CDockSite::SwapRows](../Topic/CDockSite::SwapRows.md)||  
  
## 备注  
 当你调用 [CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md) 时，框架自动创建 `CDockSite` 对象。  停靠站点窗口位于主框架窗口上的工作区边缘。  
  
 一般无需调用停靠站点提供的服务，因为 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md) 会处理这些服务。  
  
## 示例  
 下面的示例演示如何创建 `CDockSite` 类的对象。  
  
 [!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/CPP/cdocksite-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## 要求  
 **标头：**afxDockSite.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)