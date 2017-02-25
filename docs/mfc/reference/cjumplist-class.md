---
title: "CJumpList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxadv/CJumpList"
  - "CJumpList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CJumpList class"
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CJumpList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当您在任务栏时，的图标右击 `CJumpList` 为要显示的快捷键的列表。  
  
## 语法  
  
```  
class CJumpList;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CJumpList::CJumpList](../Topic/CJumpList::CJumpList.md)|构造 `CJumpList` 对象。|  
|[CJumpList::~CJumpList](../Topic/CJumpList::~CJumpList.md)|销毁 `CJumpList` 对象。|  
  
|名称|说明|  
|--------|--------|  
|[CJumpList::AbortList](../Topic/CJumpList::AbortList.md)|中止一个生成列表的事务，而无需执行。|  
|[CJumpList::AddDestination](../Topic/CJumpList::AddDestination.md)|已重载。  添加到目标列表。|  
|[CJumpList::AddKnownCategory](../Topic/CJumpList::AddKnownCategory.md)|追加一个已知分类到列表。|  
|[CJumpList::AddTask](../Topic/CJumpList::AddTask.md)|已重载。  将项添加到规范任务类别。|  
|[CJumpList::AddTasks](../Topic/CJumpList::AddTasks.md)|将项添加到规范任务类别。|  
|[CJumpList::AddTaskSeparator](../Topic/CJumpList::AddTaskSeparator.md)|添加在任务之间的分隔符。|  
|[CJumpList::ClearAll](../Topic/CJumpList::ClearAll.md)|移除到目前为止已添加到 `CJumpList` 当前实例的所有任务和目标。|  
|[CJumpList::ClearAllDestinations](../Topic/CJumpList::ClearAllDestinations.md)|移除到目前为止已添加到 `CJumpList` 当前实例的所有目标。|  
|[CJumpList::CommitList](../Topic/CJumpList::CommitList.md)|关闭一个生成列表的事务并使报表到关联的存储区\(注册表在本例中。）|  
|[CJumpList::GetDestinationList](../Topic/CJumpList::GetDestinationList.md)|检索接口指针到目标列表。|  
|[CJumpList::GetMaxSlots](../Topic/CJumpList::GetMaxSlots.md)|检索项的最大数目，包括调用应用程序的目标菜单可以显示的类别标头。|  
|[CJumpList::GetRemovedItems](../Topic/CJumpList::GetRemovedItems.md)|返回表示移除的目标的某些项目。|  
|[CJumpList::InitializeList](../Topic/CJumpList::InitializeList.md)|启动一个生成列表的事务。|  
|[CJumpList::SetAppID](../Topic/CJumpList::SetAppID.md)|设置要生成的列表的应用程序用户模型ID。|  
  
## 继承层次结构  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## 要求  
 **标头:** afxadv.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)