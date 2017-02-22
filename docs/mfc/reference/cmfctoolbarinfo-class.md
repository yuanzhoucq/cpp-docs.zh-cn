---
title: "CMFCToolBarInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarInfo class"
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCToolBarInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

包含工具栏图像资源ID在各种状态。  `CMFCToolBarInfo` 是用作 [CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md) 方法参数的帮助器选件类。  
  
## 语法  
  
```  
class CMFCToolBarInfo  
```  
  
## 成员  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCToolBarInfo::m\_uiColdResID](../Topic/CMFCToolBarInfo::m_uiColdResID.md)|包含常规工具栏位图的资源ID \(冷\)工具栏图像。|  
|[CMFCToolBarInfo::m\_uiDisabledResID](../Topic/CMFCToolBarInfo::m_uiDisabledResID.md)|包含禁用工具栏图像工具栏位图的资源ID。|  
|[CMFCToolBarInfo::m\_uiHotResID](../Topic/CMFCToolBarInfo::m_uiHotResID.md)|包含选定的工具栏位图的资源ID \(快捷\)工具栏图像。|  
|[CMFCToolBarInfo::m\_uiLargeColdResID](../Topic/CMFCToolBarInfo::m_uiLargeColdResID.md)|包含大，常规工具栏图像工具栏位图的资源ID。|  
|[CMFCToolBarInfo::m\_uiLargeDisabledResID](../Topic/CMFCToolBarInfo::m_uiLargeDisabledResID.md)|包含大，禁用工具栏图像工具栏位图的资源ID。|  
|[CMFCToolBarInfo::m\_uiLargeHotResID](../Topic/CMFCToolBarInfo::m_uiLargeHotResID.md)|包含用工具栏位图的资源ID，选定的工具栏图像。|  
|[CMFCToolBarInfo::m\_uiMenuDisabledResID](../Topic/CMFCToolBarInfo::m_uiMenuDisabledResID.md)|包含禁用菜单图像工具栏位图的资源ID。|  
|[CMFCToolBarInfo::m\_uiMenuResID](../Topic/CMFCToolBarInfo::m_uiMenuResID.md)|菜单包含图像工具栏位图的资源ID。|  
  
## 备注  
 完整的工具栏位图包括小型的工具栏图像\(按钮\)的固定大小。  每个资源ID在的 `CMFCToolBarInfo` 对象存储是例如在一个状态包含在内工具栏图像的位图\(，选定的，禁用的，用或菜单图像）。  
  
## 继承层次结构  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## 要求  
 **标头:** afxtoolbar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md)