---
title: "invalid_multiple_scheduling 类 | Microsoft Docs"
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
  - "concrt/concurrency::invalid_multiple_scheduling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_multiple_scheduling 类"
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_multiple_scheduling 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

介绍异常引发此类，在 `task_handle` 对象计划多次使用 `task_group` 的 `run` 方法时或没有介入的 `structured_task_group` 对象调用 `wait` 或 `run_and_wait` 方法。  
  
## 语法  
  
```  
class invalid_multiple_scheduling : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[invalid\_multiple\_scheduling::invalid\_multiple\_scheduling 构造函数](../Topic/invalid_multiple_scheduling::invalid_multiple_scheduling%20Constructor.md)|已重载。  构造 `invalid_multiple_scheduling` 对象。|  
  
## 继承层次结构  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_handle 类](../../../parallel/concrt/reference/task-handle-class.md)   
 [task\_group 类](../Topic/task_group%20Class.md)   
 [task\_group::run 方法](../Topic/task_group::run%20Method.md)   
 [task\_group::wait 方法](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait 方法](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group 类](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [structured\_task\_group::run 方法](../Topic/structured_task_group::run%20Method.md)   
 [structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)