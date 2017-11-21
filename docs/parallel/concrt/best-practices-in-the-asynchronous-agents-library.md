---
title: "最佳做法，异步代理库中的 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 15e4b6aca6d9f00806a37a04ffb7c93008125b6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>异步代理库中的最佳做法
本文档介绍如何有效地利用异步代理库。 代理库促进基于参与者的编程模型和进程内消息传递用于粗粒度数据流和管道任务。  
  
 有关代理库的详细信息，请参阅[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
##  <a name="top"></a> 部分  
 本文档包含以下各节：  
  
- [使用隔离状态的代理](#isolation)  
  
- [使用限制的机制来限制在数据管道中的消息数](#throttling)  
  
- [不要在数据管道中执行细化的工作](#fine-grained)  
  
- [不要通过值传递大型消息负载](#large-payloads)  
  
- [在数据网络时所有权是未定义中使用 shared_ptr](#ownership)  
  
##  <a name="isolation"></a>使用隔离状态的代理  
 代理库通过让你通过异步消息传递机制连接隔离的组件提供替代项为共享状态。 异步代理是最有效的当它们隔离自己的内部状态的其他组件。 通过隔离状态，多个组件通常不作用于共享的数据。 状态隔离可以启用你的应用程序进行扩展，因为它减少了共享内存争用。 因为组件不具有对共享数据的访问进行同步，则状态隔离还减少了死锁和争用条件的可能性。  
  
 通常通过在按住中的数据成员隔离在代理中的状态`private`或`protected`部分的代理类，并通过使用消息缓冲区通信状态更改。 下面的示例演示`basic_agent`类，该类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `basic_agent`类使用两个消息缓冲区与外部组件进行通信。 一个消息缓冲区包含传入消息;其他消息缓冲区包含传出消息。  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 有关如何定义和使用代理的完整示例，请参阅[演练： 创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[演练： 创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="throttling"></a>使用限制的机制来限制在数据管道中的消息数  
 许多消息缓冲区类型，如[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)，可以容纳无限的数量的消息。 当消息创建方速度比使用者可以处理这些消息将消息发送到数据管道时，应用程序可以进入低内存或内存不足的状态。 可以使用限制的机制，例如，信号量，来限制在数据管道中同时处于活动状态的消息数。  
  
 下面的基本示例演示如何使用信号量来限制在数据管道中的消息数。 数据管道使用[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数以模拟采用至少 100 毫秒的操作。 此示例定义了发件人产生消息的速度超过使用者可以处理这些消息，因为`semaphore`类，以使应用程序限制的活动消息数。  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 `semaphore`对象限制要同时处理最多两个消息的管线。  
  
 在此示例中制造者向使用者发送相对较少的消息。 因此，此示例不演示的潜在的内存不足或内存不足情况。 但是，此机制很有用，当数据管道包含相对较高的消息数。  
  
 有关如何创建在此示例中使用 semaphore 类的详细信息，请参阅[如何： 使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="fine-grained"></a>不要在数据管道中执行细化的工作  
 代理库在数据管道执行的工作是相当粗粒度时最有用。 例如，一个应用程序组件可能会从文件或网络连接读取数据，有时会将该数据发送到另一个组件。 代理库使用传播消息的协议会导致具有比提供的任务并行构造的系统开销更大的消息传递机制[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 因此，请确保由数据管道执行的工作都足够长，以抵消这种开销。  
  
 尽管粗粒度其任务时，数据管道是最有效，但数据管道的每个阶段可以使用 PPL 构造，如任务组和并行算法进行更细化的工作。 在每个处理阶段中使用细粒度的并行粗粒度的数据网络的示例，请参阅[演练： 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="large-payloads"></a>不要通过值传递大型消息负载  

 在某些情况下，运行时创建的每个消息从一个消息缓冲区传给另一个消息缓冲区的副本。 例如， [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)类提供了一份到其每个目标接收每条消息。 运行时还创建一份消息数据使用消息传递函数如[concurrency:: send](reference/concurrency-namespace-functions.md#send)和[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)若要将消息写入到和从消息中读取消息缓冲区。 虽然此机制可帮助消除并发写入共享数据的风险，但它可能导致较低的内存性能，如果消息负载是相对较大。  
  
 你可以使用指针或引用传递消息时提高内存性能具有较大负载。 下面的示例将指针传递到相同的消息类型的值比较传递大型消息。 此示例定义两个代理类型，`producer`和`consumer`，对其执行操作，`message_data`对象。 该示例比较的时间所需的制造者发送多个`message_data`的对象添加到所需的制造者代理将发送到多个指针的时间的使用者`message_data`向使用者的对象。  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 该示例产生下面的示例输出：  
  
```Output  
Using message_data...  
took 437ms.  
Using message_data*...  
took 47ms.  
```  
  
 因为它会消除运行时创建的完整副本的要求，使用指针的版本更好地执行每个`message_data`制造者从传递到使用者的对象。  
  
 [[返回页首](#top)]  
  
##  <a name="ownership"></a>在数据网络时所有权是未定义中使用 shared_ptr  
 当你通过指针消息传递的管道或网络中发送消息时，你通常为前部网络的每个消息分配内存和释放该内存末尾的网络。 尽管此机制通常都很好，有一些情况下在其中却很难或不可以使用它。 例如，请考虑在其中的数据网络包含多个终端节点。 在这种情况下，没有明确的位置可释放的内存的消息。  
  
 若要解决此问题，可以使用一种机制，例如， [std:: shared_ptr](../../standard-library/shared-ptr-class.md)，这样的一个指针，拥有多个组件。 当最终`shared_ptr`拥有资源的对象被销毁后，资源也将释放。  
  
 下面的示例演示如何使用`shared_ptr`共享在多个消息缓冲区的指针值。 该示例连接[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)到三个对象[concurrency:: call](../../parallel/concrt/reference/call-class.md)对象。 `overwrite_buffer`类将消息提供给其每个目标。 由于有数据网络末尾的数据的多个所有者，此示例使用`shared_ptr`来启用每`call`要共享所有权的消息对象。  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 该示例产生下面的示例输出：  
  
```Output  
Creating resource 42...  
receiver1: received resource 42  
Creating resource 64...  
receiver2: received resource 42  
receiver1: received resource 64  
Destroying resource 42...  
receiver2: received resource 64  
Destroying resource 64...  
```  
  
## <a name="see-also"></a>另请参阅  
 [并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [演练： 创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [演练： 创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [演练： 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

