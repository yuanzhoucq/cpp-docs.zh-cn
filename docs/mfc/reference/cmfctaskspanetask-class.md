---
title: "CMFCTasksPaneTask Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPaneTask"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPaneTask class"
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCTasksPaneTask Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCTasksPaneTask` 选件类是表示任务窗格控件的帮助器选件类\([CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)任务）。  task对象在任务组\([CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)\)中表示一个项目。  每个任务可能具有框架执行的命令当用户单击任务与任务名称的左边的图标。  
  
## 语法  
  
```  
class CMFCTasksPaneTask : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPaneTask::CMFCTasksPaneTask](../Topic/CMFCTasksPaneTask::CMFCTasksPaneTask.md)|创建并初始化一个 `CMFCTasksPaneTask` 对象。|  
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPaneTask::SetACCData](../Topic/CMFCTasksPaneTask::SetACCData.md)|确定辅助功能数据为当前任务。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCTasksPaneTask::m\_bAutoDestroyWindow](../Topic/CMFCTasksPaneTask::m_bAutoDestroyWindow.md)|确定是否自动销毁任务。|  
|[CMFCTasksPaneTask::m\_bIsBold](../Topic/CMFCTasksPaneTask::m_bIsBold.md)|确定框架是否绘制以粗体文本的一个任务"标签下面。|  
|[CMFCTasksPaneTask::m\_dwUserData](../Topic/CMFCTasksPaneTask::m_dwUserData.md)|包含框架与任务的用户定义的数据。  如果任务没有关联的数据，设置为零。|  
|[CMFCTasksPaneTask::m\_hwndTask](../Topic/CMFCTasksPaneTask::m_hwndTask.md)|一个句柄任务。|  
|[CMFCTasksPaneTask::m\_nIcon](../Topic/CMFCTasksPaneTask::m_nIcon.md)|在该图像的索引框架在任务旁边显示的列表图像。|  
|[CMFCTasksPaneTask::m\_nWindowHeight](../Topic/CMFCTasksPaneTask::m_nWindowHeight.md)|任务"窗口的高度。  如果任务没有任务"窗口，此值为零。|  
|[CMFCTasksPaneTask::m\_pGroup](../Topic/CMFCTasksPaneTask::m_pGroup.md)|为 `CMFCTasksPaneTaskGroup` 的指针此任务属于。|  
|[CMFCTasksPaneTask::m\_rect](../Topic/CMFCTasksPaneTask::m_rect.md)|指定任务的边框。|  
|[CMFCTasksPaneTask::m\_strName](../Topic/CMFCTasksPaneTask::m_strName.md)|任务的名称。|  
|[CMFCTasksPaneTask::m\_uiCommandID](../Topic/CMFCTasksPaneTask::m_uiCommandID.md)|指定框架执行命令的命令ID用户何时单击任务。  如果此值不是有效的命令ID，任务被视为一个简单的标签。|  
  
## 备注  
 下图显示包含三个任务的任务组:  
  
 ![已展开的任务组](../../mfc/reference/media/nexttaskgrpexpand.png "NextTaskGrpExpand")  
  
> [!NOTE]
>  如果任务没有有效的命令ID，它被视为一个简单的标签。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)  
  
## 要求  
 **标头:** afxTasksPane.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)