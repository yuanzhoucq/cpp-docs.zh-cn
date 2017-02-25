---
title: "CMFCTasksPaneTaskGroup Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPaneTaskGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPaneTaskGroup class"
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCTasksPaneTaskGroup Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCTasksPaneTaskGroup` 选件类是 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) 控件使用的帮助器选件类。  类型 `CMFCTasksPaneTaskGroup` Objects表示 *任务组*。  任务组是框架在单独的框中显示具有折叠按钮的项列表。  框能有一个可选说明\(组名称）。  如果组处于折叠状态，任务列表不可见。  
  
## 语法  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](../Topic/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup.md)|构造 `CMFCTasksPaneTaskGroup` 对象。|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPaneTaskGroup::SetACCData](../Topic/CMFCTasksPaneTaskGroup::SetACCData.md)|确定当前任务组的可访问性数据。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPaneTaskGroup::m\_bIsBottom](../Topic/CMFCTasksPaneTaskGroup::m_bIsBottom.md)|确定任务组是否对齐任务窗格控件的底部。|  
|[CMFCTasksPaneTaskGroup::m\_bIsCollapsed](../Topic/CMFCTasksPaneTaskGroup::m_bIsCollapsed.md)|确定任务组是否已折叠。|  
|[CMFCTasksPaneTaskGroup::m\_bIsSpecial](../Topic/CMFCTasksPaneTaskGroup::m_bIsSpecial.md)|确定任务组是否是 *特定的。*该框架在不同颜色的特定说明。|  
|[CMFCTasksPaneTaskGroup::m\_lstTasks](../Topic/CMFCTasksPaneTaskGroup::m_lstTasks.md)|包含内部列表任务。|  
|[CMFCTasksPaneTaskGroup::m\_rect](../Topic/CMFCTasksPaneTaskGroup::m_rect.md)|指定组说明的边框。|  
|[CMFCTasksPaneTaskGroup::m\_rectGroup](../Topic/CMFCTasksPaneTaskGroup::m_rectGroup.md)|指定组的边框。|  
|[CMFCTasksPaneTaskGroup::m\_strName](../Topic/CMFCTasksPaneTaskGroup::m_strName.md)|指定组的名称。|  
  
## 备注  
 下图显示了扩展的任务组:  
  
 ![已展开的任务组](../../mfc/reference/media/nexttaskgrpexpand.png "NextTaskGrpExpand")  
  
 下面的插图显示了折叠的任务组:  
  
 ![已折叠的任务组](../../mfc/reference/media/nexttaskgrpcollapse.png "NextTaskGrpCollapse")  
  
 下面的插图显示了任务组，而无需声明:  
  
 ![无标题的任务组](../../mfc/reference/media/nexttaskgrpnocapt.png "NextTaskGrpNoCapt")  
  
 下图显示了两个任务组。  第一个任务组将指示为特定通过设置为 `TRUE`的 `m_bIsSpecial` 标志，而第二个任务组不是特定的。  请注意第一个任务组的说明如何比第二个任务组暗:  
  
 ![特殊任务组](../../mfc/reference/media/nexttaskgrpspecial.png "NextTaskGrpSpecial")  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## 要求  
 **标头:** afxTasksPane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPane Class](../../mfc/reference/cmfctaskspane-class.md)   
 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)