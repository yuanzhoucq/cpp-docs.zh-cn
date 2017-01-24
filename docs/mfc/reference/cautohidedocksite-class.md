---
title: "CAutoHideDockSite Class | Microsoft Docs"
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
  - "CAutoHideDockSite"
  - "AllowShowOnPaneMenu"
  - "CAutoHideDockSite::AllowShowOnPaneMenu"
  - "CAutoHideDockSite.AllowShowOnPaneMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AllowShowOnPaneMenu method"
  - "CAutoHideDockSite class"
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
caps.latest.revision: 32
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoHideDockSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CAutoHideDockSite` 实现自动隐藏停靠窗格扩展 [CDockSite Class](../../mfc/reference/cdocksite-class.md)。  
  
## 语法  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CAutoHideDockSite::CAutoHideDockSite`|构造 `CAutoHideDockSite` 对象。|  
|`CAutoHideDockSite::~CAutoHideDockSite`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|指示 `CAutoHideDockSite` 是否在窗格中显示菜单。|  
|[CAutoHideDockSite::CanAcceptPane](../Topic/CAutoHideDockSite::CanAcceptPane.md)|确定基本窗格对象是从 [CMFCAutoHideBar Class](../../mfc/reference/cmfcautohidebar-class.md)派生。|  
|[CAutoHideDockSite::DockPane](../Topic/CAutoHideDockSite::DockPane.md)|停靠一个窗格将此 `CAuotHideDockSite` 对象。|  
|[CAutoHideDockSite::GetAlignRect](../Topic/CAutoHideDockSite::GetAlignRect.md)|检索停靠站点的大小屏幕坐标。|  
|[CAutoHideDockSite::RepositionPanes](../Topic/CAutoHideDockSite::RepositionPanes.md)|重绘在 `CAutoHideDockSite` 的窗格与全局边距和按钮间隔。|  
|[CAutoHideDockSite::SetOffsetLeft](../Topic/CAutoHideDockSite::SetOffsetLeft.md)|在停靠条的左侧设置边距。|  
|[CAutoHideDockSite::SetOffsetRight](../Topic/CAutoHideDockSite::SetOffsetRight.md)|在停靠条的右侧设置边距。|  
|[CAutoHideDockSite::UnSetAutoHideMode](../Topic/CAutoHideDockSite::UnSetAutoHideMode.md)|调用对象的 [CMFCAutoHideBar::UnSetAutoHideMode](../Topic/CMFCAutoHideBar::UnSetAutoHideMode.md) 在 `CAutoHideDockSite`。|  
  
### 数据成员  
  
|||  
|-|-|  
|名称|说明|  
|[CAutoHideDockSite::m\_nExtraSpace](../Topic/CAutoHideDockSite::m_nExtraSpace.md)|定义空间的大小在工具栏和停靠栏的边缘之间。  此空间从左侧边缘或上边缘\)测量，根据停靠空间的对齐方式。|  
  
## 备注  
 当您调用 [CFrameWndEx::EnableAutoHidePanes](../Topic/CFrameWndEx::EnableAutoHidePanes.md)时，框架自动创建一 `CAutoHideDockSite` 对象。  在大多数情况下，您不必直接实例化或使用此选件类。  
  
 停靠条停靠窗格的左侧和 [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md)之间的左边的空白。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## 示例  
 下面的示例演示如何从 `CMFCAutoHideBar` 对象检索 `CAutoHideDockSite` 对象以及如何设置停靠栏的左右边距。  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/CPP/cautohidedocksite-class_1.cpp)]  
  
## 要求  
 **标头:** afxautohidedocksite.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockSite Class](../../mfc/reference/cdocksite-class.md)