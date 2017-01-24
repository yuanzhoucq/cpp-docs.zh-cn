---
title: "异步代理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "代理 [并发运行时]"
  - "异步代理"
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
caps.latest.revision: 15
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异步代理
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

异步代理（或只称作*代理*）是以异步方式与其他代理一起解决更大的计算任务的应用程序组件。  将代理看作具有设定的生命周期的任务。  例如，一个代理可能会从输入\/输出设备（如键盘、磁盘上的文件或网络连接）中读取数据，另一个代理可能会在数据变得可用时对该数据执行操作。  第一个代理通过消息传递来通知第二个代理有更多数据可用。  并发运行时任务计划程序提供了一个高效的机制，使代理能够以协作方式进行阻止和退出，而无需进行效率低下的抢占。  
  
 代理库定义了 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 类来表示异步代理。  `agent` 是一个声明虚拟方法 [concurrency::agent::run](../Topic/agent::run%20Method.md) 的抽象类。  `run` 方法执行代理所执行的任务。  由于 `run` 是抽象的，所以您必须在从 `agent` 派生的每个类中实现此方法。  
  
## 代理生命周期  
 代理具有设定的生命周期。  [concurrency::agent\_status](../Topic/agent_status%20Enumeration.md) 枚举定义代理的各种状态。  下图是一个状态图，它演示了代理如何从一种状态进入另一种状态。  在此图中，实线表示您从应用程序调用的方法；虚线表示从运行时调用的方法。  
  
 ![代理状态图](../../parallel/concrt/media/agentstate.png "AgentState")  
  
 下表描述了 `agent_status` 枚举中的每种状态。  
  
|代理状态|说明|  
|----------|--------|  
|`agent_created`|尚未计划代理的执行。|  
|`agent_runnable`|运行时正在计划代理的执行。|  
|`agent_started`|代理已启动并正在运行。|  
|`agent_done`|代理已完成。|  
|`agent_canceled`|代理在进入 `started` 状态之前已被取消。|  
  
 `agent_created` 是代理的初始状态，`agent_runnable` 和 `agent_started` 是活动状态，`agent_done` 和 `agent_canceled` 是最终状态。  
  
 使用 [concurrency::agent::status](../Topic/agent::status%20Method.md) 方法检索 `agent` 对象的当前状态。  尽管 `status` 方法是并发安全方法，但是当 `status` 方法返回时，代理的状态可能会发生变化。  例如，调用 `status` 方法时代理可能处于 `agent_started` 状态，但是，在 `status` 方法返回后，代理可能会进入 `agent_done` 状态。  
  
## 方法和功能  
 下表显示了属于 `agent` 类的某些重要方法。  有关所有 `agent` 类方法的更多信息，请参见 [agent 类](../../parallel/concrt/reference/agent-class.md)。  
  
|方法|说明|  
|--------|--------|  
|[start](../Topic/agent::start%20Method.md)|计划 `agent` 对象的执行，并将它设置为 `agent_runnable` 状态。|  
|[run](../Topic/agent::run%20Method.md)|执行要由 `agent` 对象执行的任务。|  
|[done](../Topic/agent::done%20Method.md)|使代理进入 `agent_done` 状态。|  
|[取消](../Topic/agent::cancel%20Method.md)|如果代理未启动，则此方法将取消执行代理，并将代理设置为 `agent_canceled` 状态。|  
|[status](../Topic/agent::status%20Method.md)|检索 `agent` 对象的当前状态。|  
|[wait](../Topic/agent::wait%20Method.md)|等待 `agent` 对象进入 `agent_done` 或 `agent_canceled` 状态。|  
|[wait\_for\_all](../Topic/agent::wait_for_all%20Method.md)|等待所有提供的 `agent` 对象进入 `agent_done` 或 `agent_canceled` 状态。|  
|[wait\_for\_one](../Topic/agent::wait_for_one%20Method.md)|等待至少一个提供的 `agent` 对象进入 `agent_done` 或 `agent_canceled` 状态。|  
  
 创建代理对象后，调用 [concurrency::agent::start](../Topic/agent::start%20Method.md) 方法来计划它的执行。  运行时在计划代理之后调用 `run` 方法，并将代理设置为 `agent_runnable` 状态。  
  
 运行时不会管理异步代理引发的异常。  有关异常处理和代理的更多信息，请参见[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
## 示例  
 有关演示如何创建基于代理的基本应用程序的示例，请参阅[演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)。  
  
## 请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)