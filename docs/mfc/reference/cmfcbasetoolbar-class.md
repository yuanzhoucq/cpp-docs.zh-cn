---
title: "CMFCBaseToolBar Class | Microsoft Docs"
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
  - "CMFCBaseToolBar::CreateObject"
  - "~CMFCBaseToolBar"
  - "CMFCBaseToolBar"
  - "CMFCBaseToolBar::CMFCBaseToolBar"
  - "CMFCBaseToolBar::~CMFCBaseToolBar"
  - "CMFCBaseToolBar.~CMFCBaseToolBar"
  - "CreateObject"
  - "CMFCBaseToolBar.CMFCBaseToolBar"
  - "CMFCBaseToolBar.CreateObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCBaseToolBar destructor"
  - "CMFCBaseToolBar class"
  - "CMFCBaseToolBar class, 构造函数"
  - "CMFCBaseToolBar class, 析构函数"
  - "CreateObject method"
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCBaseToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

工具栏的基类。  
  
## 语法  
  
```  
class CMFCBaseToolBar : public CPane  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCBaseToolBar::CMFCBaseToolBar`|默认构造函数。|  
|`CMFCBaseToolBar::~CMFCBaseToolBar`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|`CMFCBaseToolBar::CreateObject`|用于由框架创建此选件类类型动态实例。|  
|[CMFCBaseToolBar::GetDockingMode](../Topic/CMFCBaseToolBar::GetDockingMode.md)|返回停靠模式。  （重写 [CBasePane::GetDockingMode](../Topic/CBasePane::GetDockingMode.md)。）|  
|[CMFCBaseToolBar::GetMinSize](../Topic/CMFCBaseToolBar::GetMinSize.md)|返回工具栏的最小尺寸。  （重写 [CPane::GetMinSize](../Topic/CPane::GetMinSize.md)。）|  
|[CMFCBaseToolBar::OnAfterChangeParent](../Topic/CMFCBaseToolBar::OnAfterChangeParent.md)|调用由框架在窗格中的父后更改。  （重写 [CBasePane::OnAfterChangeParent](../Topic/CBasePane::OnAfterChangeParent.md)。）|  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
## 要求  
 **标头:** afxbasetoolbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)