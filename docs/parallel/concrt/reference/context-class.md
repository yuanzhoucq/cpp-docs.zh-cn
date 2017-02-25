---
title: "Context 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::Context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Context 类"
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# Context 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示执行上下文的抽象。  
  
## 语法  
  
```  
class Context;  
```  
  
## 成员  
  
### 受保护的构造函数  
  
|名称|描述|  
|--------|--------|  
|[Context::~Context 析构函数](../Topic/Context::~Context%20Destructor.md)||  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[Context::Block 方法](../Topic/Context::Block%20Method.md)|阻止当前上下文。|  
|[Context::CurrentContext 方法](../Topic/Context::CurrentContext%20Method.md)|返回指向当前上下文的指针。|  
|[Context::GetId 方法](../Topic/Context::GetId%20Method.md)|返回上下文所属的计划程序中唯一的该上下文的标识符。|  
|[Context::GetScheduleGroupId 方法](../Topic/Context::GetScheduleGroupId%20Method.md)|返回上下文当前正在处理的计划组的标识符。|  
|[Context::GetVirtualProcessorId 方法](../Topic/Context::GetVirtualProcessorId%20Method.md)|返回上下文当前正在执行的虚拟处理器的标识符。|  
|[Context::Id 方法](../Topic/Context::Id%20Method.md)|返回当前上下文所属的计划程序中唯一的该当前上下文的标识符。|  
|[Context::IsCurrentTaskCollectionCanceling 方法](../Topic/Context::IsCurrentTaskCollectionCanceling%20Method.md)|返回在当前上下文上正在执行内联的任务集合是否正在活动的取消的过程中（或不久将取消）的指示。|  
|[Context::IsSynchronouslyBlocked 方法](../Topic/Context::IsSynchronouslyBlocked%20Method.md)|确定上下文是否被同步阻止。  如果上下文显式执行导致阻塞的操作，则认为该上下文被同步阻止。|  
|[Context::Oversubscribe 方法](../Topic/Context::Oversubscribe%20Method.md)|调用在计划程序中的某个虚拟处理器上执行的上下文时，将额外的虚拟处理器插入该计划程序代码块的持续时间。|  
|[Context::ScheduleGroupId 方法](../Topic/Context::ScheduleGroupId%20Method.md)|返回当前上下文正在处理的计划组的标识符。|  
|[Context::Unblock 方法](../Topic/Context::Unblock%20Method.md)|取消阻止上下文并使其可运行。|  
|[Context::VirtualProcessorId 方法](../Topic/Context::VirtualProcessorId%20Method.md)|返回当前上下文正在执行的虚拟处理器的标识符。|  
|[Context::Yield 方法](../Topic/Context::Yield%20Method.md)|得到执行从而使另一上下文可能执行。  如果没有其他上下文可供执行，则计划程序可能会执行其他操作系统线程。|  
  
## 备注  
 并发运行时计划程序（请参见[计划程序](../../../parallel/concrt/reference/scheduler-class.md)）使用执行上下文来执行由您的应用程序对其进行排队的工作。  Win32 线程是执行上下文的示例 windows 操作系统的。  
  
 在任何时候，计划程序的并发级别等于通过资源管理器向它授予的虚拟处理器数。  虚拟处理器是处理资源的抽象，可映射到基础系统中的硬件线程。  在指定时间只有一个计划程序上下文可能会在虚拟处理器上执行。  
  
 计划程序本质是合作性的，如果它希望进入等待状态，正在执行上下文可能在任何时候产生不同上下文的虚拟处理器。  当等待条件满足之后，在虚拟处理器可用之前不会从开始执行它的计划程序恢复。  
  
## 继承层次结构  
 `Context`  
  
## 要求  
 **标头：**concrt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler 类](../../../parallel/concrt/reference/scheduler-class.md)   
 [任务计划程序](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)