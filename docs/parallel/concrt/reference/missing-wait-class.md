---
title: "missing_wait 类 | Microsoft Docs"
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
  - "concrt/concurrency::missing_wait"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "missing_wait 类"
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# missing_wait 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

此类描述如果引发了异常，则对任务进行时仍调度到对象的析构函数执行的 `task_group` 或 `structured_task_group` 对象。  ，如果析构函数到达由于展开，因为异常的堆栈此异常不会引发异常。  
  
## 语法  
  
```  
class missing_wait : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[missing\_wait::missing\_wait 构造函数](../Topic/missing_wait::missing_wait%20Constructor.md)|已重载。  构造 `missing_wait` 对象。|  
  
## 备注  
 异常流不存在，您有责任在允许析构 `task_group` 或 `structured_task_group` 对象之前，调用对象的 `wait` 或 `run_and_wait` 方法。  运行时引发该异常表明您忘记了调用 `wait` 或 `run_and_wait` 方法。  
  
## 继承层次结构  
 `exception`  
  
 `missing_wait`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group 类](../Topic/task_group%20Class.md)   
 [task\_group::wait 方法](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait 方法](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group 类](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [structured\_task\_group::wait 方法](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait 方法](../Topic/structured_task_group::run_and_wait%20Method.md)