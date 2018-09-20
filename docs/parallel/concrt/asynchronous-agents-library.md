---
title: 异步代理库 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Agents Library
- Asynchronous Agents Library
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9b8cfbf81edb478b1c7dd157d0faae7eb66be18
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433865"
---
# <a name="asynchronous-agents-library"></a>异步代理库

异步代理库 (或只需*代理库*) 提供了编程模型，可用于提高启用并发的应用程序开发的可靠性。 代理库是一个 c + + 模板库可提高基于角色的编程模型和进程内消息传递，以粗粒度数据流和流水线操作任务。 代理库生成并发运行时的计划和资源管理组件。

## <a name="programming-model"></a>编程模型

代理库提供共享状态的替代方法，通过让你通过基于数据流而不是控制流的异步通信模型连接独立的组件。 *数据流*指的是编程模型进行计算的所有必需的数据都可用;*控制流*指按预设的顺序进行计算的编程模型。

数据流编程模型与*消息传递*这一概念相关，其中程序的独立组件通过发送消息相互通信。

代理库由三个组件组成：*异步代理*，*异步消息块*，并*消息传递函数*。 代理维护状态，并使用消息块和消息传递函数与另一个以及与外部组件进行通信。 消息传递函数使代理能够发送和接收消息与外部组件。 异步消息块存放消息，并使代理能够以同步方式进行通信。

下图显示了两个代理使用消息块和消息传递函数进行通信。 在此图中，`agent1`发送到消息`agent2`通过使用[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数和一个[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象。 `agent2` 使用[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数来读取该消息。 `agent2` 使用相同的方法将消息发送到`agent1`。 虚线的箭头表示代理之间的数据流。 实线箭头将代理连接到它们写入或读取的消息块。

![代理库的组件](../../parallel/concrt/media/agent_librarycomp.png "agent_librarycomp")

实现此图中的代码示例是在本主题后面所示。

代理编程模型具有几大优势，其他并发和同步机制，例如，事件。 一个优点是，通过使用消息传递对象之间传输状态更改，你可以隔离对共享资源的访问并因此改进可伸缩性。 消息传递的优势是它绑定到数据而不是将它绑定至外部同步对象的同步。 这简化了组件之间的数据传输，并可以消除应用程序中的编程错误。

## <a name="when-to-use-the-agents-library"></a>何时使用代理库

如果你有必须相互进行异步通信的多个操作，请使用代理库。 消息块和消息传递函数可以编写并行应用程序而无需同步机制，例如锁。 这样，您将精力集中在应用程序逻辑。

代理编程模型通常用于创建*数据管道*或*网络*。 数据管道是一系列组件，其中每个执行特定任务的影响更大目标。 在数据流管道中的每个组件执行工作时从另一个组件收到的消息。 该工作的结果传递给管道或网络中的其他组件。 组件可以使用更多的细粒度并发功能从其他库，例如，则[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)。

## <a name="example"></a>示例

下面的示例实现显示在本主题前面的插图。

[!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/cpp/asynchronous-agents-library_1.cpp)]

该示例产生下面的输出：

```Output
agent1: sending request...
agent2: received 'request'.
agent2: sending response...
agent1: received '42'.
```

以下主题介绍在此示例中使用的功能。

## <a name="related-topics"></a>相关主题

[异步代理](../../parallel/concrt/asynchronous-agents.md)<br/>
介绍异步代理解决较大的计算任务的角色。

[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
介绍由代理库提供的各种消息块类型。

[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
介绍了由代理库提供各种消息传递例程。

[如何：实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br/>
介绍如何在你的应用程序中实现制造者-使用者模式。

[如何：为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br/>
说明了通过多种方法提供工作函数[concurrency:: call](../../parallel/concrt/reference/call-class.md)并[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)类。

[如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
演示如何使用[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)数据管道中的类。

[如何：在已完成的任务之间选择](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br/>
演示如何使用[concurrency:: choice](../../parallel/concrt/reference/choice-class.md)并[concurrency:: join](../../parallel/concrt/reference/join-class.md)类选择第一个任务完成搜索算法。

[如何：定期发送消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br/>
演示如何使用[concurrency:: timer](../../parallel/concrt/reference/timer-class.md)类定期发送一条消息。

[如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)<br/>
演示如何使用筛选器使异步消息块能够接受或拒绝消息。

[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
介绍如何在您的应用程序中使用各种并行模式，如并行算法。

[并发运行时](../../parallel/concrt/concurrency-runtime.md)<br/>
描述可以简化并发编程并包含相关主题链接的并发运行时。

