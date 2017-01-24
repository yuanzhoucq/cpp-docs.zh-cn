---
title: "ScheduleGroup 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::ScheduleGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ScheduleGroup 类"
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ScheduleGroup 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示计划组的抽象。  计划组组织受益于在时间上（通过在移到另一个组之前执行同一组中另一个任务）或空间上（通过在同一 NUMA 节点或物理套接字上执行同一个组内的多项）紧密安排在一起的一组相关工作。  
  
## 语法  
  
```  
class ScheduleGroup;  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|描述|  
|--------|--------|  
|[ScheduleGroup::~ScheduleGroup 析构函数](../Topic/ScheduleGroup::~ScheduleGroup%20Destructor.md)||  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[ScheduleGroup::Id 方法](../Topic/ScheduleGroup::Id%20Method.md)|返回组所属的计划程序中唯一的该计划组的标识符。|  
|[ScheduleGroup::Reference 方法](../Topic/ScheduleGroup::Reference%20Method.md)|递增计划组的引用数。|  
|[ScheduleGroup::Release 方法](../Topic/ScheduleGroup::Release%20Method.md)|减少计划程序组的引用数。|  
|[ScheduleGroup::ScheduleTask 方法](../Topic/ScheduleGroup::ScheduleTask%20Method.md)|在计划组内安排轻量任务。|  
  
## 继承层次结构  
 `ScheduleGroup`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [CurrentScheduler 类](../../../parallel/concrt/reference/currentscheduler-class.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)