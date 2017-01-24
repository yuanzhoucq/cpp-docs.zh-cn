---
title: "IThreadProxy 结构 | Microsoft Docs"
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
  - "concrtrm/concurrency::IThreadProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IThreadProxy 结构"
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
caps.latest.revision: 21
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IThreadProxy 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

执行线程的抽象。  根据您创建的计划程序的 `SchedulerType` 策略密钥，资源管理器将授予您由普通的 Win32 线程或用户模式计划 \(UMS\) 线程支持的线程代理。  UMS 线程在版本为 Windows 7 或更高版本的 64 位操作系统上支持。  
  
## 语法  
  
```  
struct IThreadProxy;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IThreadProxy::GetId 方法](../Topic/IThreadProxy::GetId%20Method.md)|返回线程代理的唯一标识符。|  
|[IThreadProxy::SwitchOut 方法](../Topic/IThreadProxy::SwitchOut%20Method.md)|分离基础虚拟处理器根的上下文。|  
|[IThreadProxy::SwitchTo 方法](../Topic/IThreadProxy::SwitchTo%20Method.md)|执行从当前执行上下文到另一个上下文的协作上下文切换。|  
|[IThreadProxy::YieldToSystem 方法](../Topic/IThreadProxy::YieldToSystem%20Method.md)|导致调用线程执行准备好在当前处理器上运行的另一个线程。  由操作系统选择要执行的下个线程。|  
  
## 备注  
 线程代理耦合到由接口 `IExecutionContext` 表示的执行上下文，作为调度工作的方式。  
  
## 继承层次结构  
 `IThreadProxy`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IExecutionContext 结构](../../../parallel/concrt/reference/iexecutioncontext-structure.md)   
 [IScheduler 结构](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IVirtualProcessorRoot 结构](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)