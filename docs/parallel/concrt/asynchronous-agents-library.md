---
title: "异步代理库 | Microsoft Docs"
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
  - "代理库"
  - "异步代理库"
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异步代理库
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

异步代理库 (或只是 *代理库*) 提供了编程模型，您可以提高启用并发的应用程序开发的可靠性。 代理库是一个 c + + 模板库，以促进基于角色的编程模型和进程内消息传递，以粗粒度的数据流和流水线操作任务。 代理库构建在并发运行时计划和资源管理组件上。  
  
## <a name="programming-model"></a>编程模型  
 代理库通过允许您通过基于数据流而不是控制流的异步通信模型连接独立的组件来提供对共享状态的替代项。 *数据流* 指的是编程模型进行计算的所有必需的数据时都可用; *控制流* 指的是按预定的顺序进行计算的一个编程模型。  
  
 数据流编程模型相关的概念 *消息传递*, 、 程序的独立组件通过发送消息来与另一个进行通信的位置。  
  
 代理库的三个组件组成︰ *异步代理*, ，*异步消息块*, ，和 *消息传递函数*。 代理维护状态，并使用消息块和消息传递函数与另一个和与外部组件进行通信。 消息传递函数使代理可以发送和接收消息传入和传出的外部组件。 异步消息块存放消息，并使代理能够以同步方式进行通信。  
  
 下图显示了两个代理，使用消息块和消息传递函数进行通信。 在此图中， `agent1` 发送一条消息给 `agent2` 使用 [concurrency:: send](../Topic/send%20Function.md) 函数和一个 [concurrency:: unbounded_buffer](../Topic/unbounded_buffer%20Class.md) 对象。 `agent2` 使用 [concurrency:: receive](../Topic/receive%20Function.md) 函数读取消息。 `agent2` 使用相同的方法来将消息发送到 `agent1`。 虚线的箭头表示代理之间的数据流。 稳定的箭头将代理连接到他们写入或读取的消息块。  
  
 ![代理库的组件](../../parallel/concrt/media/agent_librarycomp.png "Agent_LibraryComp")  
  
 在本主题后面显示了实现此图的代码示例。  
  
 代理编程模型相比具有一些优势其他并发和同步机制，例如，事件。 一个优点是通过使用消息传递对象之间传输状态更改，您可以隔离对共享资源的访问，从而提高可伸缩性。 消息传递的优势是它将同步到数据而不是绑定到外部同步对象进行绑定。 这简化了组件之间的数据传输，并可以消除您的应用程序中的编程错误。  
  
## <a name="when-to-use-the-agents-library"></a>何时使用代理库  
 当您有必须与另一个异步通信的多个操作，请使用代理库。 消息块和消息传递函数使您无需同步机制，例如锁编写并行应用程序。 这样，您将精力集中在应用程序逻辑。  
  
 代理编程模型通常用于创建 *数据管线* 或 *网络*。 数据管道是一系列组件，其中每个执行一个参与更大目标的特定任务。 在从另一个组件收到一条消息时，每个组件在数据流管道中的执行工作。 该工作的结果传递给管道或网络中的其他组件。 组件可以使用更细化的并发功能从其他库，例如， [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)。  
  
## <a name="example"></a>示例  
 下面的示例实现显示在本主题前面的插图。  
  
 [!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/CPP/asynchronous-agents-library_1.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
agent1: sending request...  
agent2: received 'request'.  
agent2: sending response...  
agent1: received '42'.  
```  
  
 以下主题介绍在此示例中使用的功能。  
  
## <a name="related-topics"></a>相关主题  
 [异步代理](../../parallel/concrt/asynchronous-agents.md)  
 介绍异步代理解决较大的计算任务的角色。  
  
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
 描述由代理库提供的各种消息块类型。  
  
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
 介绍了由代理库提供各种消息传递例程。  
  
 [如何︰ 实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
 描述如何在您的应用程序中实现制造者-使用者模式。  
  
 [如何︰ 为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
 说明了几种方法提供工作函数到 [concurrency:: call](../../parallel/concrt/reference/call-class.md) 和 [concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md) 类。  
  
 [如何︰ 在数据管道中的使用 transformer](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
 演示如何使用 [concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md) 数据管道中的类。  
  
 [如何︰ 在已完成的任务之间选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
 演示如何使用 [concurrency:: choice](../../parallel/concrt/reference/choice-class.md) 和 [concurrency:: join](../../parallel/concrt/reference/join-class.md) 类选择用于完成搜索算法的第一个任务。  
  
 [如何︰ 定期发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
 演示如何使用 [concurrency:: timer](../../parallel/concrt/reference/timer-class.md) 类定期发送一条消息。  
  
 [如何︰ 使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
 演示如何使用筛选器以启用异步消息块来接受或拒绝消息。  
  
 [并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 描述如何在您的应用程序中使用各种并行模式，例如并行算法。  
  
 [并发运行时](../../parallel/concrt/concurrency-runtime.md)  
 描述可以简化并发编程并包含相关主题链接的并发运行时。

