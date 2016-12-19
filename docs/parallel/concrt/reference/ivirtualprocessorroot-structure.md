---
title: "IVirtualProcessorRoot 结构 | Microsoft Docs"
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
  - "concrtrm/concurrency::IVirtualProcessorRoot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IVirtualProcessorRoot 结构"
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IVirtualProcessorRoot 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

线程代理可在其中执行的硬件线程的抽象。  
  
## 语法  
  
```  
struct IVirtualProcessorRoot : public IExecutionResource;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IVirtualProcessorRoot::Activate 方法](../Topic/IVirtualProcessorRoot::Activate%20Method.md)|使与执行上下文接口 `pContext` 关联的线程代理在此虚拟处理根上开始执行。|  
|[IVirtualProcessorRoot::Deactivate 方法](../Topic/IVirtualProcessorRoot::Deactivate%20Method.md)|使当前正在此虚拟处理器根上执行的线程代理停止调度执行上下文。  线程代理将继续执行对 `Activate` 方法的调用。|  
|[IVirtualProcessorRoot::EnsureAllTasksVisible 方法](../Topic/IVirtualProcessorRoot::EnsureAllTasksVisible%20Method.md)|使存储在各个处理器内存层次结构中的数据对系统中的所有处理器均可见。  它确保了在方法返回之前对所有处理器都执行了全内存界定。|  
|[IVirtualProcessorRoot::GetId 方法](../Topic/IVirtualProcessorRoot::GetId%20Method.md)|返回虚拟处理器根的唯一标识符。|  
  
## 备注  
 每个虚拟处理器根均具有关联的执行资源。  `IVirtualProcessorRoot` 接口从 [IExecutionResource](../../../parallel/concrt/reference/iexecutionresource-structure.md) 接口继承。  多个虚拟处理器根可能对应于相同的基础硬件线程。  
  
 资源管理器向计划程序授予虚拟处理器跟，以对资源请求响应。  计划程序可以使用虚拟处理器根通过将其与执行上下文一起激活来执行工作。  
  
## 继承层次结构  
 [IExecutionResource](../../../parallel/concrt/reference/iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)