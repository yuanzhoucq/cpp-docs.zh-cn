---
title: "task_completion_event 类 | Microsoft Docs"
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
  - "ppltasks/concurrency::task_completion_event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_completion_event 类"
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
caps.latest.revision: 11
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_completion_event 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

`task_completion_event` 类允许你延迟任务的执行，直到满足条件，或启动任务以响应外部事件。  
  
## 语法  
  
```  
template<  
   typename _ResultType  
>  
class task_completion_event;  
  
template<>  
class task_completion_event<void>;  
```  
  
#### 参数  
 `_ResultType`  
 此 `task_completion_event` 类的结果类型。  
  
 `T`  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[task\_completion\_event::task\_completion\_event 构造函数](../Topic/task_completion_event::task_completion_event%20Constructor.md)|构造 `task_completion_event` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[task\_completion\_event::set 方法](../Topic/task_completion_event::set%20Method.md)|已重载。  设置任务完成事件。|  
|[task\_completion\_event::set\_exception 方法](../Topic/task_completion_event::set_exception%20Method.md)|已重载。  将异常传播给所有与此事件关联的任务。|  
  
## 备注  
 当你的方案要求你创建能够完成的任务时，请使用从任务完成事件创建的任务，从而在将来的某个时刻可以安排执行它的继续。  `task_completion_event` 必须与你创建的任务具有相同类型，利用该类型的值调用任务完成事件上的设置方法将导致关联的任务完成，并会将该值作为其继续的结果提供。  
  
 如果任务完成事件永不发出信号，则从中创建的所有任务都将在析构时取消。  
  
 `task_completion_event` 行为与智能指针的行为类似，应按值传递。  
  
## 继承层次结构  
 `task_completion_event`  
  
## 要求  
 **标头：**ppltasks.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task Class](http://msdn.microsoft.com/zh-cn/5389e8a5-5038-40b6-844a-55e9b58ad35f)