---
title: "nested_scheduler_missing_detach 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::nested_scheduler_missing_detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nested_scheduler_missing_detach 类"
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# nested_scheduler_missing_detach 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类描述并发运行时检测到您忽略在通过 `Scheduler` 对象的 `Attach` 方法在附加至第二计划程序的上下文上调用 `CurrentScheduler::Detach` 方法时抛出的异常。  
  
## 语法  
  
```  
class nested_scheduler_missing_detach : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[nested\_scheduler\_missing\_detach::nested\_scheduler\_missing\_detach 构造函数](../Topic/nested_scheduler_missing_detach::nested_scheduler_missing_detach%20Constructor.md)|已重载。  构造 `nested_scheduler_missing_detach` 对象。|  
  
## 备注  
 仅当在另一个计划程序中嵌套计划程序，方法为在已由另一计划程序拥有或连接至另一计划程序的上下文中调用 `Scheduler` 对象的 `Attach` 方法时，才会引发该异常。  并发运行时在可以检测到有助于查找问题的方案时引发此异常。  并非每个实例忘记调用 `CurrentScheduler::Detach` 方法都一定会引发此异常。  
  
## 继承层次结构  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [CurrentScheduler::Detach 方法](../Topic/CurrentScheduler::Detach%20Method.md)   
 [Scheduler::Attach 方法](../Topic/Scheduler::Attach%20Method.md)