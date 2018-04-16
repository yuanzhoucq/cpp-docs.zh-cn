---
title: "异步代理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c4ce3240041987a79657c7e8bf296f9e89acb7a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="asynchronous-agents"></a>异步代理
*异步代理*(或仅仅称为*代理*) 是一种应用程序组件，它以异步方式与其他代理一起解决较大的计算任务。 将代理视为具有设定的生命周期的任务。 例如，一个代理可能会阅读输入/输出设备 （例如键盘、 磁盘上的文件或网络连接） 和另一个代理中的数据可能对数据执行操作该变得可用。 第一个代理使用消息传递通知的第二个代理更多数据可用。 并发运行时任务计划程序提供了有效的机制，以使代理能够阻止和以协作方式退出而无需效率低下的抢占。  
  

 代理库定义[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)类来表示异步代理。 `agent`是一个抽象类来声明虚拟方法[concurrency::agent::run](reference/agent-class.md#run)。 `run`方法执行代理执行的任务。 因为`run`是抽象的则必须实现此方法在每个类都派生自`agent`。  
  
## <a name="agent-life-cycle"></a>代理生命周期  
 代理具有设定的生命周期。 [Concurrency:: agent_status](reference/concurrency-namespace-enums.md#agent_status)枚举定义代理的各种状态。 下图是显示了代理如何从一个状态到另一个状态图。 此图中，实线表示从你的应用程序; 调用的方法虚线表示在运行时中调用的方法。  
  
 ![代理状态图](../../parallel/concrt/media/agentstate.png "agentstate")  
  
 下表描述了在每个状态`agent_status`枚举。  
  
|代理状态|描述|  
|-----------------|-----------------|  
|`agent_created`|代理已不被计划执行。|  
|`agent_runnable`|运行时正在计划用于执行的代理。|  
|`agent_started`|代理已启动并正在运行。|  
|`agent_done`|代理已完成。|  
|`agent_canceled`|代理已取消它输入之前`started`状态。|  
  
 `agent_created`是代理的初始状态`agent_runnable`和`agent_started`是活动状态，和`agent_done`和`agent_canceled`是最终状态。  
  
 使用[concurrency::agent::status](reference/agent-class.md#status)方法来检索其中的当前状态`agent`对象。 尽管`status`方法是并发安全的代理的状态可能会发生变化时`status`方法返回。 例如，代理可能在`agent_started`状态时调用`status`方法，但移动到`agent_done`紧后面状态`status`方法返回。  

  
## <a name="methods-and-features"></a>方法和功能  
 下表显示了一些重要的方法属于`agent`类。 有关所有详细信息`agent`类方法，请参阅[代理类](../../parallel/concrt/reference/agent-class.md)。  
  
|方法|描述|  
|------------|-----------------|  
|[start](reference/agent-class.md#start)|计划`agent`对象的执行并将它设置为`agent_runnable`状态。|  
|[run](reference/agent-class.md#run)|执行要执行的任务`agent`对象。|  
|[完成](reference/agent-class.md#done)|将移动到代理`agent_done`状态。|  
|[取消](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|如果未启动代理，此方法取消执行的代理，并将其设置为`agent_canceled`状态。|  
|[status](reference/agent-class.md#status)|检索的当前状态`agent`对象。|  
|[等待](reference/agent-class.md#wait)|等待`agent`对象输入`agent_done`或`agent_canceled`状态。|  
|[wait_for_all](reference/agent-class.md#wait_for_all)|等待所有提供`agent`对象进入`agent_done`或`agent_canceled`状态。|  
|[wait_for_one](reference/agent-class.md#wait_for_one)|等待至少一个提供`agent`对象进入`agent_done`或`agent_canceled`状态。|  
  
 创建代理对象后，调用[concurrency::agent::start](reference/agent-class.md#start)方法来计划它的执行。 在运行时调用`run`方法后它安排代理并将其设置为`agent_runnable`状态。  
  
 运行时不管理异步代理引发的异常。 有关异常处理和代理的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
## <a name="example"></a>示例  
 有关演示如何创建基于代理的基本应用程序示例，请参阅[演练： 创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)。  
  
## <a name="see-also"></a>请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)

