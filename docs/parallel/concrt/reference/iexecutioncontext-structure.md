---
title: "IExecutionContext 结构 | Microsoft Docs"
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
  - "concrtrm/concurrency::IExecutionContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IExecutionContext 结构"
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IExecutionContext 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

可以在指定虚拟处理器上运行并可以协作切换上下文的执行上下文的接口。  
  
## 语法  
  
```  
struct IExecutionContext;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IExecutionContext::Dispatch 方法](../Topic/IExecutionContext::Dispatch%20Method.md)|当线程代理开始执行特定的执行上下文时被调用的方法。  这应该是您计划程序的主工作者例程。|  
|[IExecutionContext::GetId 方法](../Topic/IExecutionContext::GetId%20Method.md)|返回执行上下文的唯一标识符。|  
|[IExecutionContext::GetProxy 方法](../Topic/IExecutionContext::GetProxy%20Method.md)|返回正在执行此上下文的线程代理的接口。|  
|[IExecutionContext::GetScheduler 方法](../Topic/IExecutionContext::GetScheduler%20Method.md)|返回此执行上下文所属的计划程序的接口。|  
|[IExecutionContext::SetProxy 方法](../Topic/IExecutionContext::SetProxy%20Method.md)|将线程代理与此执行上下文相关联。  在开始执行上下文的 `Dispatch` 方法之前，关联的线程代理会调用此方法。|  
  
## 备注  
 如果要实现与并发运行时资源管理器进行交互的自定义计划程序，您将需要实现 `IExecutionContext` 接口。  资源管理器创建的线程以计划程序的名义通过执行 `IExecutionContext::Dispatch` 方法执行工作。  
  
## 继承层次结构  
 `IExecutionContext`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IScheduler 结构](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IThreadProxy 结构](../../../parallel/concrt/reference/ithreadproxy-structure.md)