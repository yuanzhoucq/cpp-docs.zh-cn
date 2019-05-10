---
title: 异步代理库中的最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: c61393957a63895a9ecbdaaae8d83a5fbd710de3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236541"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>异步代理库中的最佳做法

本文档介绍如何有效地利用异步代理库。 代理库可提升应用基于角色的编程模型和进程内消息传递，以粗粒度数据流和流水线操作任务。

有关代理库的详细信息，请参阅[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。

##  <a name="top"></a> 部分

本文档包含以下各节：

- [使用代理为隔离状态](#isolation)

- [使用限制机制来限制数据管道中的消息数](#throttling)

- [不要在数据管道中执行细化的工作](#fine-grained)

- [不要通过值传递大型消息有效负载](#large-payloads)

- [在数据网络时所有权是未定义中使用 shared_ptr](#ownership)

##  <a name="isolation"></a> 使用代理为隔离状态

代理库提供共享状态的替代方法，通过让你通过异步消息传递机制连接独立的组件。 当他们隔离其内部状态从其他组件时，异步代理是最有效。 通过隔离状态，多个组件通常不作用于共享的数据。 状态隔离可以使应用程序能够缩放，因为它减少了对共享内存的争用。 状态隔离还可减少死锁和争用条件的可能性，因为组件无需同步对共享数据的访问。

通常通过保留中的数据成员隔离中代理的状态`private`或`protected`部分的代理类并通过使用消息缓冲区将状态更改通知。 下面的示例演示`basic_agent`类，该类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)。 `basic_agent`类使用两个消息缓冲区与外部组件进行通信。 一个消息缓冲区保留传入的消息;其他消息缓冲区包含传出消息。

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

有关如何定义和使用代理的完整示例，请参阅[演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)。

[[返回页首](#top)]

##  <a name="throttling"></a> 使用限制机制来限制数据管道中的消息数

许多消息缓冲区类型，如[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)，可以包含无限的数量的消息。 当消息创建方快于使用者可以处理这些消息将消息发送到数据管道时，应用程序可以进入低内存或内存不足状态。 阻止机制，例如，一个信号量，可用于限制在数据管道中同时处于活动状态的消息数。

下面的基本示例演示如何使用一个信号量来限制数据管道中的消息数。 数据管道用途[concurrency:: wait](reference/concurrency-namespace-functions.md#wait)函数以模拟需至少 100 毫秒的操作。 此示例定义了发送方不是使用者可以处理这些消息更快地生成消息，因为`semaphore`类，以使应用程序，以限制活动消息的数目。

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore`对象限制要同时处理最多两个消息的管道。

在此示例中生成者将相对较少的消息发送给使用者。 因此，此示例没有演示潜在的低内存或内存不足条件。 但是，此机制时，数据管道包含相对大量的消息。

有关如何创建信号量类，用于在此示例中的详细信息，请参阅[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

[[返回页首](#top)]

##  <a name="fine-grained"></a> 不要在数据管道中执行细化的工作

非常粗粒度的数据管道执行的工作时，代理库是最有用。 例如，某个应用程序组件可能会从文件或网络连接读取数据并偶尔会将该数据发送到另一个组件。 代理库使用传播消息的协议将导致有更多的开销比提供的任务并行构造的消息传递机制[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md)(PPL)。 因此，请确保通过数据管道执行的工作是足够长，以抵消这种开销。

尽管粗粒度其任务时，数据管道是最有效，但数据管道的每个阶段可以使用 PPL 构造，如任务组和并行算法进行更细化的工作。 在每个处理阶段使用细粒度并行操作的粗粒度的数据网络的示例，请参阅[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[返回页首](#top)]

##  <a name="large-payloads"></a> 不要通过值传递大型消息有效负载

在某些情况下，运行时创建从一个消息缓冲区传递到另一个消息缓冲区每条消息的副本。 例如， [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)类提供了一份到其每个目标接收每条消息。 运行时还创建一份消息数据，如使用消息传递函数时[concurrency:: send](reference/concurrency-namespace-functions.md#send)并[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)若要将消息写入和从消息中读取消息缓冲区。 虽然此机制可帮助消除同时写入共享数据的风险，但它可能相对较大的消息有效负载时导致较低的内存性能。

可以使用指针或引用来传递消息时提高内存性能具有较大负载。 下面的示例将传递大型消息通过将指针传递到相同的消息类型的值进行比较。 该示例定义了两个代理类型，`producer`并`consumer`，，作用于`message_data`对象。 该示例比较了所需的生成者发送多个时间`message_data`时间所需的制造者代理，将发送到多个指针的使用者的对象`message_data`向使用者的对象。

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

此示例产生下面的示例输出：

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

使用指针的版本更好地执行，因为它不运行时创建的完整副本需要每个`message_data`会传递给使用者从生成者的对象。

[[返回页首](#top)]

##  <a name="ownership"></a> 在数据网络时所有权是未定义中使用 shared_ptr

时将消息发送的消息传递管道或网络中的指针时，你通常为前面在网络的每个消息分配内存和释放该内存末尾的网络。 尽管这种机制通常都很好，存在一些情况下在其中很难或不可以使用它。 例如，假设数据网络中包含多个终端节点。 在这种情况下，没有明确的位置可释放的内存的消息。

若要解决此问题，可以使用一种机制，例如， [std:: shared_ptr](../../standard-library/shared-ptr-class.md)，这样使它们属于多个组件的指针。 当最终`shared_ptr`拥有资源的对象被销毁后，资源也将释放。

下面的示例演示如何使用`shared_ptr`共享在多个消息缓冲区的指针值。 该示例连接[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)为三个对象[concurrency:: call](../../parallel/concrt/reference/call-class.md)对象。 `overwrite_buffer`类提供了为其每个目标的消息。 由于没有数据网络末尾处的数据的多个所有者，因此此示例使用`shared_ptr`来启用每`call`要共享所有权的消息的对象。

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

此示例产生下面的示例输出：

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

## <a name="see-also"></a>请参阅

[并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
