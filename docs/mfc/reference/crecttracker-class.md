---
title: "CRectTracker Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRectTracker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRectTracker class"
  - "displaying items"
  - "resizing items"
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CRectTracker Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要授予project中显示，移动和调整大小以不同的方式。  
  
## 语法  
  
```  
  
class CRectTracker  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CRectTracker::CRectTracker](../Topic/CRectTracker::CRectTracker.md)|构造 `CRectTracker` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CRectTracker::AdjustRect](../Topic/CRectTracker::AdjustRect.md)|调用，而该矩形调整大小。|  
|[CRectTracker::Draw](../Topic/CRectTracker::Draw.md)|呈现矩形。|  
|[CRectTracker::DrawTrackerRect](../Topic/CRectTracker::DrawTrackerRect.md)|调用，同时还 `CRectTracker` 对象的边框。|  
|[CRectTracker::GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)|页中获取 `CRectTracker`项目的掩码的大小调整句柄。|  
|[CRectTracker::GetTrueRect](../Topic/CRectTracker::GetTrueRect.md)|返回宽度，并且高度矩形，包括大小调整句柄。|  
|[CRectTracker::HitTest](../Topic/CRectTracker::HitTest.md)|返回游标的当前位置与 `CRectTracker` 对象相关。|  
|[CRectTracker::NormalizeHit](../Topic/CRectTracker::NormalizeHit.md)|规范化命中测试代码。|  
|[CRectTracker::OnChangedRect](../Topic/CRectTracker::OnChangedRect.md)|调用，而该矩形已调整大小或移动的。|  
|[CRectTracker::SetCursor](../Topic/CRectTracker::SetCursor.md)|根据在矩形的位置设置光标。|  
|[CRectTracker::Track](../Topic/CRectTracker::Track.md)|允许用户操作矩形。|  
|[CRectTracker::TrackRubberBand](../Topic/CRectTracker::TrackRubberBand.md)|向用户为“橡胶带区”中选择。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CRectTracker::m\_nHandleSize](../Topic/CRectTracker::m_nHandleSize.md)|确定大小调整句柄。|  
|[CRectTracker::m\_nStyle](../Topic/CRectTracker::m_nStyle.md)|TRACKER的当前样式。|  
|[CRectTracker::m\_rect](../Topic/CRectTracker::m_rect.md)|当前位置\(以像素为单位\)矩形。|  
|[CRectTracker::m\_sizeMin](../Topic/CRectTracker::m_sizeMin.md)|确定最小矩形的宽度和高度。|  
  
## 备注  
 `CRectTracker` 没有基类。  
  
 通过使用图形界面，尽管 `CRectTracker` 选件类旨在允许用户与OLE项进行交互，其使用不限于OLE启用的应用程序。  可以使用就好像它是这样的用户界面需要。  
  
 `CRectTracker` 边框可以修复或虚线。  可以为项目指定一个阴影边框或复盖率在一个阴影的模式指示该项目的不同状态。  您可以将八调整在项目的外部或内部边框的句柄。  （对于大小调整句柄的说明，请参见 [GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)。）最后，在调整过程中，`CRectTracker` 允许您更改项目的orientation。  
  
 若要使用 `CRectTracker`，请构造 `CRectTracker` 对象并指定显示状态初始化。  然后可以使用此接口为用户提供在OLE项的当前状态的可视反馈与 `CRectTracker` 对象。  
  
 有关使用 `CRectTracker`的更多信息，请参见文章 [TRACKER](../../mfc/trackers.md)。  
  
## 继承层次结构  
 `CRectTracker`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC TRACKER示例](../../top/visual-cpp-samples.md)   
 [MFC示例DRAWCLI](../../top/visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleResizeBar Class](../../mfc/reference/coleresizebar-class.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)   
 [CRectTracker::GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)