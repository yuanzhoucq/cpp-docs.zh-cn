---
title: 异步代理库中的最佳做法
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 1cd6b54a014d35d17c732ed52f8529b05274585b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142095"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>异步代理库中的最佳做法

本文档介绍如何有效使用异步代理库。 代理库为粗粒度的数据流和管道任务升级基于参与者的编程模型和进程内消息传递。

有关代理库的详细信息，请参阅[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。

## <a name="top"></a> 部分

本文档包含以下各节：

- [使用代理隔离状态](#isolation)

- [使用限制机制限制数据管道中的消息数](#throttling)

- [请勿在数据管道中执行细化工作](#fine-grained)

- [不要通过值传递大消息负载](#large-payloads)

- [在未定义所有权时，在数据网络中使用 shared_ptr](#ownership)

## <a name="isolation"></a>使用代理隔离状态

代理库通过允许通过异步消息传递机制连接隔离的组件，提供共享状态的替代项。 异步代理在将其内部状态与其他组件隔离时最有效。 通过隔离状态，多个组件通常不会对共享数据执行操作。 状态隔离可以使应用程序进行缩放，因为它可以减少对共享内存的争用。 状态隔离还降低了死锁和争用条件的可能性，因为组件不必同步对共享数据的访问。

通常通过将数据成员保存在代理类的 `private` 或 `protected` 部分中，并通过使用消息缓冲区传达状态更改来隔离代理中的状态。 下面的示例演示了从[concurrency：： agent](../../parallel/concrt/reference/agent-class.md)派生的 `basic_agent` 类。 `basic_agent` 类使用两个消息缓冲区与外部组件通信。 一个消息缓冲区包含传入消息;其他消息缓冲区包含传出消息。

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

有关如何定义和使用代理的完整示例，请参阅[演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)和[演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)。

[[返回页首](#top)]

## <a name="throttling"></a>使用限制机制限制数据管道中的消息数

许多消息缓冲区类型（如[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)）可以包含无限数量的消息。 当消息制造者向数据管道发送消息的速度比使用者可以处理这些消息的速度快时，应用程序可以输入内存不足或内存不足的状态。 可以使用限制机制（例如，信号量）来限制数据管道中同时处于活动状态的消息数。

下面的基本示例演示如何使用信号量来限制数据管道中的消息数。 数据管道使用[concurrency：： wait](reference/concurrency-namespace-functions.md#wait)函数来模拟至少需要100毫秒的操作。 因为发送方产生的消息速度快于使用者可以处理这些消息的速度，所以，此示例定义了 `semaphore` 类，以使应用程序能够限制活动消息的数量。

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

`semaphore` 对象限制管道在同一时间最多处理两条消息。

此示例中的制造者向使用者发送相对较少的消息。 因此，此示例不会演示可能的内存不足或内存不足的情况。 但是，当数据管道包含的消息数量相对较多时，此机制很有用。

有关如何创建此示例中使用的信号灯类的详细信息，请参阅[如何：使用上下文类实现协作信号量](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)。

[[返回页首](#top)]

## <a name="fine-grained"></a>请勿在数据管道中执行细化工作

当数据管道执行的工作相当粗粒度时，代理库最为有用。 例如，一个应用程序组件可能从文件或网络连接中读取数据，但有时会将该数据发送到另一个组件。 代理库用于传播消息的协议会导致消息传递机制比[并行模式库](../../parallel/concrt/parallel-patterns-library-ppl.md)（PPL）提供的任务并行构造的开销更多。 因此，请确保数据管道执行的工作足够长，以抵消此开销。

尽管数据管道在其任务较为细化时最有效，但数据管道的每个阶段都可以使用 PPL 构造（如任务组和并行算法）执行更细化的工作。 有关在每个处理阶段使用细化并行的粗粒度数据网络的示例，请参阅[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[返回页首](#top)]

## <a name="large-payloads"></a>不要通过值传递大消息负载

在某些情况下，运行时将创建从一个消息缓冲区传递到另一个消息缓冲区的每个消息的副本。 例如， [concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)类提供它接收到每个目标的每个消息的副本。 当你使用消息传递函数（如[concurrency：： send](reference/concurrency-namespace-functions.md#send)和[concurrency：： receive](reference/concurrency-namespace-functions.md#receive) ）向消息缓冲区写入消息和从中读取消息时，运行时还会创建消息数据的副本。 尽管此机制有助于消除并发写入共享数据的风险，但当消息有效负载较大时，可能会导致内存性能不佳。

当传递具有大型有效负载的消息时，可以使用指针或引用来提高内存性能。 下面的示例将按值传递大消息进行比较，以将指针传递到相同的消息类型。 此示例定义了两个在 `message_data` 对象上操作的代理类型，`producer` 和 `consumer`。 该示例将生成者向使用者发送多个 `message_data` 对象所需的时间进行比较，使生成者代理向使用者发送 `message_data` 对象所需的时间。

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

此示例将生成以下示例输出：

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

使用指针的版本更好，因为它不再要求运行时创建它从制造者传递到使用者的每个 `message_data` 对象的完整副本。

[[返回页首](#top)]

## <a name="ownership"></a>在未定义所有权时，在数据网络中使用 shared_ptr

当你通过消息传递管道或网络发送消息时，通常会为网络前面的每个消息分配内存，并在网络结束时释放该内存。 虽然这种机制通常很好地运行，但在某些情况下很难或无法使用它。 例如，假设数据网络包含多个终结点节点。 在这种情况下，没有任何明确的位置可用来释放消息内存。

若要解决此问题，可以使用一种机制（例如[std：： shared_ptr](../../standard-library/shared-ptr-class.md)），该机制允许多个组件拥有一个指针。 当拥有资源的最终 `shared_ptr` 对象被销毁时，资源也会被释放。

下面的示例演示如何使用 `shared_ptr` 在多个消息缓冲区之间共享指针值。 该示例将[concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)对象连接到三个[concurrency：： call](../../parallel/concrt/reference/call-class.md)对象。 `overwrite_buffer` 类向其每个目标提供消息。 由于数据网络的末尾有多个数据所有者，因此，此示例使用 `shared_ptr` 来使每个 `call` 对象都可以共享消息的所有权。

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

此示例将生成以下示例输出：

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

[并发运行时最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[演练：创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[演练：创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[并行模式库中的最佳做法](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[并发运行时中的常规最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
