---
title: "CPaneDivider Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaneDivider"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneDivider class"
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CPaneDivider Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 `CPaneDivider` 选件类将两个窗格，拆分窗格的两组或从主框架窗口的工作区分隔窗格中的组。  
  
## 语法  
  
```  
class CPaneDivider : public CBasePane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CPaneDivider::CPaneDivider](../Topic/CPaneDivider::CPaneDivider.md)||  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPaneDivider::AddPaneContainer](../Topic/CPaneDivider::AddPaneContainer.md)||  
|[CPaneDivider::AddPane](../Topic/CPaneDivider::AddPane.md)||  
|[CPaneDivider::AddRecentPane](../Topic/CPaneDivider::AddRecentPane.md)||  
|[CPaneDivider::CalcExpectedDockedRect](../Topic/CPaneDivider::CalcExpectedDockedRect.md)||  
|[CPaneDivider::CalcFixedLayout](../Topic/CPaneDivider::CalcFixedLayout.md)|（重写 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。）|  
|[CPaneDivider::CheckVisibility](../Topic/CPaneDivider::CheckVisibility.md)||  
|[CPaneDivider::CreateEx](../Topic/CPaneDivider::CreateEx.md)|（重写 [CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)。）|  
|[CPaneDivider::DoesAllowDynInsertBefore](../Topic/CPaneDivider::DoesAllowDynInsertBefore.md)|（重写 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)。）|  
|[CPaneDivider::DoesContainFloatingPane](../Topic/CPaneDivider::DoesContainFloatingPane.md)||  
|[CPaneDivider::FindPaneContainer](../Topic/CPaneDivider::FindPaneContainer.md)||  
|[CPaneDivider::FindTabbedPane](../Topic/CPaneDivider::FindTabbedPane.md)||  
|[CPaneDivider::GetDefaultWidth](../Topic/CPaneDivider::GetDefaultWidth.md)||  
|[CPaneDivider::GetFirstPane](../Topic/CPaneDivider::GetFirstPane.md)||  
|[CPaneDivider::GetPaneDividerStyle](../Topic/CPaneDivider::GetPaneDividerStyle.md)||  
|[CPaneDivider::GetRootContainerRect](../Topic/CPaneDivider::GetRootContainerRect.md)||  
|[CPaneDivider::GetWidth](../Topic/CPaneDivider::GetWidth.md)||  
|[CPaneDivider::Init](../Topic/CPaneDivider::Init.md)||  
|[CPaneDivider::InsertPane](../Topic/CPaneDivider::InsertPane.md)||  
|[CPaneDivider::IsAutoHideMode](../Topic/CPaneDivider::IsAutoHideMode.md)|（重写 [CBasePane::IsAutoHideMode](../Topic/CBasePane::IsAutoHideMode.md)。）|  
|[CPaneDivider::IsDefault](../Topic/CPaneDivider::IsDefault.md)||  
|[CPaneDivider::IsHorizontal](../Topic/CPaneDivider::IsHorizontal.md)|（重写 [CBasePane::IsHorizontal](../Topic/CBasePane::IsHorizontal.md)。）|  
|[CPaneDivider::Move](../Topic/CPaneDivider::Move.md)||  
|[CPaneDivider::NotifyAboutRelease](../Topic/CPaneDivider::NotifyAboutRelease.md)||  
|[CPaneDivider::OnShowPane](../Topic/CPaneDivider::OnShowPane.md)||  
|[CPaneDivider::ReleaseEmptyPaneContainers](../Topic/CPaneDivider::ReleaseEmptyPaneContainers.md)||  
|[CPaneDivider::RemovePane](../Topic/CPaneDivider::RemovePane.md)||  
|[CPaneDivider::ReplacePane](../Topic/CPaneDivider::ReplacePane.md)||  
|[CPaneDivider::RepositionPanes](../Topic/CPaneDivider::RepositionPanes.md)||  
|[CPaneDivider::Serialize](../Topic/CPaneDivider::Serialize.md)|（重写 `CBasePane::Serialize`。）|  
|[CPaneDivider::SetAutoHideMode](../Topic/CPaneDivider::SetAutoHideMode.md)||  
|[CPaneDivider::SetPaneContainerManager](../Topic/CPaneDivider::SetPaneContainerManager.md)||  
|[CPaneDivider::ShowWindow](../Topic/CPaneDivider::ShowWindow.md)||  
|[CPaneDivider::StoreRecentDockSiteInfo](../Topic/CPaneDivider::StoreRecentDockSiteInfo.md)||  
|[CPaneDivider::StoreRecentTabRelatedInfo](../Topic/CPaneDivider::StoreRecentTabRelatedInfo.md)||  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CPaneDivider::GetPanes](../Topic/CPaneDivider::GetPanes.md)|返回位于 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)窗格的列表。  应为默认窗格分隔符仅调用此方法。|  
|[CPaneDivider::GetPaneDividers](../Topic/CPaneDivider::GetPaneDividers.md)|返回的窗格分隔列表驻留在 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)。  应为默认窗格分隔符仅调用此方法。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CPaneDivider::m\_nDefaultWidth](../Topic/CPaneDivider::m_nDefaultWidth.md)|在所有窗格分隔符像素为单位指定默认宽度在应用程序中。|  
|[CPaneDivider::m\_pSliderRTC](../Topic/CPaneDivider::m_pSliderRTC.md)|保存指向有关 `CPaneDivider`的运行时信息选件类派生的对象。|  
  
## 备注  
 在窗格停靠时，框架自动创建 `CPaneDivider` 对象。  
  
 具有窗格分隔的两种类型:  
  
-   在窗格的一组停靠在主框架窗口时，一边默认窗格分隔符创建。  默认窗格分隔符保存指向 [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md) 并重在窗格中的组的大多数操作方向\(例如调整窗格或停靠另一个窗格或容器\)。容器管理器。  每个停靠窗格维护指向其默认窗格分隔符。  
  
-   一个常规窗格分隔符分为容器的两个窗格。  有关更多信息，请参见 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)。  
  
## 示例  
 下面的示例演示如何从获取 `CWorkspaceBar` 对象的一 `CPaneDivider` 对象。  此代码段是 [MDI示例演示选项](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/CPP/cpanedivider-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPaneDivider](../../mfc/reference/cpanedivider-class.md)  
  
## 要求  
 **标头:** afxPaneDivider.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md)   
 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)   
 [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)