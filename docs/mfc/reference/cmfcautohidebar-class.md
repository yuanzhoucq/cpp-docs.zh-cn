---
title: "CMFCAutoHideBar Class | Microsoft Docs"
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
  - "CMFCAutoHideBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAutoHideToolBar class"
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCAutoHideBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCAutoHideBar` 类是实现自动隐藏功能的特殊工具栏类。  
  
## 语法  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](../Topic/CMFCAutoHideBar::CMFCAutoHideBar.md)||  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCAutoHideBar::AddAutoHideWindow](../Topic/CMFCAutoHideBar::AddAutoHideWindow.md)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](../Topic/CMFCAutoHideBar::AllowShowOnPaneMenu.md)|（重写 `CPane::AllowShowOnPaneMenu`。）|  
|[CMFCAutoHideBar::CalcFixedLayout](../Topic/CMFCAutoHideBar::CalcFixedLayout.md)|（重写 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)。）|  
|[CMFCAutoHideBar::Create](../Topic/CMFCAutoHideBar::Create.md)|创建功能区栏并将其附加到 [CPane](../../mfc/reference/cpane-class.md) 对象。  （重写 [CPane::Create](../Topic/CPane::Create.md)。）|  
|[CMFCAutoHideBar::GetFirstAHWindow](../Topic/CMFCAutoHideBar::GetFirstAHWindow.md)||  
|[CMFCAutoHideBar::GetVisibleCount](../Topic/CMFCAutoHideBar::GetVisibleCount.md)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](../Topic/CMFCAutoHideBar::OnShowControlBarMenu.md)|当即将显示特殊窗格菜单时由框架调用。  （重写 [CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)。）|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](../Topic/CMFCAutoHideBar::RemoveAutoHideWindow.md)||  
|[CMFCAutoHideBar::SetActiveInGroup](../Topic/CMFCAutoHideBar::SetActiveInGroup.md)|（重写 [CPane::SetActiveInGroup](../Topic/CPane::SetActiveInGroup.md)。）|  
|[CMFCAutoHideBar::SetRecentVisibleState](../Topic/CMFCAutoHideBar::SetRecentVisibleState.md)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](../Topic/CMFCAutoHideBar::ShowAutoHideWindow.md)||  
|[CMFCAutoHideBar::StretchPane](../Topic/CMFCAutoHideBar::StretchPane.md)|垂直或水平拉伸窗格。  （重写 [CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)。）|  
|[CMFCAutoHideBar::UnSetAutoHideMode](../Topic/CMFCAutoHideBar::UnSetAutoHideMode.md)||  
|[CMFCAutoHideBar::UpdateVisibleState](../Topic/CMFCAutoHideBar::UpdateVisibleState.md)||  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCAutoHideBar::m\_nShowAHWndDelay](../Topic/CMFCAutoHideBar::m_nShowAHWndDelay.md)|用户将鼠标光标置于 [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md) 上方的时刻与框架显示关联窗口的时刻之间的时间延迟。|  
  
## 备注  
 当用户将停靠窗格切换为自动隐藏模式时，框架会自动创建 `CMFCAutoHideBar` 对象。  它还会创建所需的 [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) 和 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) 对象。  每个 `CAutoHideDockSite` 对象都与单个 `CMFCAutoHideButton` 关联。  
  
 `CMFCAutoHideBar` 类在用户鼠标悬停在 `CMFCAutoHideButton` 上方时实现 `CAutoHideDockSite` 的显示。  当工具栏收到 WM\_MOUSEMOVE 消息时，`CMFCAutoHideBar` 会启动计时器。  当计时器完成时，它会向工具栏发送 WM\_TIMER 事件通知。  工具栏通过检查鼠标指针是否位于它在计时器启动时所处的相同自动隐藏按钮上，来处理此事件。  如果是，则显示附加的 `CAutoHideDockSite`。  
  
 可以通过设置 `m_nShowAHWndDelay` 来控制计时器延迟的长度。  默认值为 400 毫秒。  
  
## 示例  
 下列示例演示如何构造 `CMFCAutoHideBar` 对象并使用其 `GetDockSiteRow` 方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/CPP/cmfcautohidebar-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## 要求  
 **标头：**afxautohidebar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CAutoHideDockSite Class](../../mfc/reference/cautohidedocksite-class.md)   
 [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md)