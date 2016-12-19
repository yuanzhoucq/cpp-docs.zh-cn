---
title: "异步代理库中的最佳做法 | Microsoft Docs"
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
  - "最佳做法, 异步代理库"
  - "异步代理库, 最佳做法"
  - "异步代理库, 要避免的做法"
  - "要避免的做法, 异步代理库"
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异步代理库中的最佳做法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍如何有效利用异步代理库。  代理库可提升用于粗粒度数据流和流水线操作任务的基于角色的编程模型和进程内消息传递。  
  
 有关代理库的更多信息，请参见[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
##  <a name="top"></a> 各节内容  
 本文档包含以下几节：  
  
-   [使用代理隔离状态](#isolation)  
  
-   [使用限制机制限制数据管道中的消息数量](#throttling)  
  
-   [不要在数据管道中执行细化工作](#fine-grained)  
  
-   [不要通过值传递大型消息负载](#large-payloads)  
  
-   [在未定义所有权的情况下在数据网络中使用 shared\_ptr](#ownership)  
  
##  <a name="isolation"></a> 使用代理隔离状态  
 代理库可提供共享状态的备选方案，方法是让您通过异步消息传递机制连接独立的组件。  如果异步代理将它们的内部状态与其他组件隔离，此时异步代理最有效。  通过隔离状态，多个组件通常不作用于共享的数据。  状态隔离可允许您的应用程序进行扩展，因为它能够减少对共享内存的争用现象。  状态隔离还减少死锁和争用情况发生的可能性，因为组件不必同步对共享数据的访问。  
  
 通过在代理类的 `private` 或 `protected` 部分容纳数据成员和使用消息缓冲区对状态更改进行通信，通常可以在代理中隔离状态。  下面的示例演示从 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 派生的 `basic_agent` 类。  `basic_agent` 类使用两个消息缓冲区与外部组件进行通信。  一个消息缓冲区容纳传入消息；另一个消息缓冲区则容纳传出消息。  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 有关如何定义和使用代理的完整示例，请参见[演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="throttling"></a> 使用限制机制限制数据管道中的消息数量  
 许多消息缓冲区类型（例如 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md)）可以容纳的消息数量没有限制。  当消息制造者将消息发送至数据管道的速度比使用者处理这些消息的速度要快时，应用程序可能进入内存低或内存不足的状态。  您可以使用限制机制（例如信号量）来限制数据管道中并发活动的消息的数量。  
  
 下面的基本示例演示如何使用信号量来限制数据管道中消息的数量。  数据管道使用 [concurrency::wait](../Topic/wait%20Function.md) 函数模拟至少持续 100 毫秒的操作。  由于发送方生成消息的速度要快于使用者处理这些消息的速度，因此该示例定义 `semaphore` 类以允许应用程序限制活动消息的数量。  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 `semaphore` 对象限制管道最多同时处理两条消息。  
  
 此示例中的制造者发送给使用者的消息数相对比较少。  因此，本示例不演示潜在的内存低或内存不足情况。  但是，该机制在数据管道包含的消息数量相对较多时很有用。  
  
 有关如何创建本示例中使用的信号量类的更多信息，请参见[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="fine-grained"></a> 不要在数据管道中执行细化工作  
 代理库在数据管理执行的工作非常粗化时最有用。  例如，一个应用程序组件可能从文件或网络连接读取数据，并偶尔将该数据发送至另一个应用程序。  代理库用于传播消息的协议会导致消息传递机制比[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\) 提供的任务并行构造产生更高的开销。  因此，确保数据管道执行的工作足够长可补偿此开销。  
  
 尽管数据管道在其任务为粗粒化时最有效，但数据管道的各个阶段可以使用 PPL 构造（例如任务组和并行算法）来执行更细化的工作。  有关在各个处理阶段使用细粒化并行的粗粒化数据网络的示例，请参见[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 \[[Top](#top)\]  
  
##  <a name="large-payloads"></a> 不要通过值传递大型消息负载  
 在某些情况下，运行时会创建它从一个消息缓冲区传递给另一个消息缓冲区的每条消息的副本。  例如，[concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 类可将其接收的每条消息的副本提供给其各个目标。  当您使用消息传递函数（例如 [concurrency::send](../Topic/send%20Function.md) 和 [concurrency::receive](../Topic/receive%20Function.md)）在消息缓冲区中写入和读取消息时，运行时也会创建消息数据的副本。  尽管此机制可帮助消除并发写入共享数据的风险，但当消息负载相对较大时，它可能会导致较低的内存性能。  
  
 当您传递具有较大负载的消息时，可以使用指针或引用来提升内存性能。  下面的示例将通过值传递大型消息与传递相同消息类型的指针进行比较。  此示例定义两种代理类型，`producer` 和 `consumer`，它们作用于 `message_data` 对象。  此示例将制造者将多个 `message_data` 对象发送至使用者所需的时间与制造者代理将多个 `message_data` 对象的指针发送至使用者所需的时间进行比较。  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 此示例产生下面的示例输出：  
  
  **使用 message\_data…**  
**花费 437ms。**  
**使用 message\_data\*...**  
**花费 47ms。** 使用指针的版本执行效果更佳，因为它不需要运行时创建其从制造者传递至使用者的每个 `message_data` 对象的完整副本。  
  
 \[[Top](#top)\]  
  
##  <a name="ownership"></a> 在未定义所有权的情况下在数据网络中使用 shared\_ptr  
 当您在消息传递管道或网络中通过指针发送消息时，通常可在网络的前端为每个消息分配内存，并在网络的末端释放该内存。  尽管该机制通常都很好用，但在有些情况下却很难或无法使用。  例如，在数据网络包含多个终端节点的情况下。  这种情况下，没有明确的位置可释放消息的内存。  
  
 若要解决此问题，可以使用 [std::shared\_ptr](../../standard-library/shared-ptr-class.md) 等机制，它可以使指针由多个组件所拥有。  当占有资源的最后一个 `shared_ptr` 对象被销毁时，也会释放该资源。  
  
 下面的示例演示如何使用 `shared_ptr` 在多个消息缓冲区之间共享指针值。  此示例将 [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 对象连接至三个 [concurrency::call](../../parallel/concrt/reference/call-class.md) 对象。  `overwrite_buffer` 类将消息提供给其各个目标。  由于在数据网络的末端有多个数据的所有者，因此该示例使用 `shared_ptr` 允许各个 `call` 对象共享消息的所有权。  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 此示例产生下面的示例输出：  
  
  **创建资源42...**  
**receiver1:接收资源42**  
**创建资源64...**  
**receiver2:接收资源42**  
**receiver1:接收资源64**  
**损坏的资源 42…**  
**receiver2:接收资源64**  
**损坏的资源 64…**   
## 请参阅  
 [并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)