---
title: "improper_scheduler_detach 类 | Microsoft Docs"
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
  - "concrt/concurrency::improper_scheduler_detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_detach 类"
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# improper_scheduler_detach 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在 `CurrentScheduler::Detach` 调用方法使用 `Scheduler` 对象的 `Attach` 方法，未附加到任何计划程序的上下文中。  
  
## 语法  
  
```  
class improper_scheduler_detach : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[improper\_scheduler\_detach::improper\_scheduler\_detach 构造函数](../Topic/improper_scheduler_detach::improper_scheduler_detach%20Constructor.md)|已重载。  构造 `improper_scheduler_detach` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `improper_scheduler_detach`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [CurrentScheduler::Detach 方法](../Topic/CurrentScheduler::Detach%20Method.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)