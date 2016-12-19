---
title: "异步消息块 | Microsoft Docs"
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
  - "非贪婪联接 [并发运行时]"
  - "异步消息块"
  - "贪婪联接 [并发运行时]"
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 异步消息块
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代理库提供使您能够将应用程序组件间的消息传播以线程安全的方式的多个消息块类型。 这些消息块类型通常用于与各种消息传递例程，如 [concurrency:: send](../Topic/send%20Function.md), ，[concurrency:: asend](../Topic/asend%20Function.md), ，[concurrency:: receive](../Topic/receive%20Function.md), ，和 [concurrency:: try_receive](../Topic/try_receive%20Function.md)。 有关消息传递由代理库定义的例程的详细信息，请参阅 [消息传递函数](../../parallel/concrt/message-passing-functions.md)。  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 部分  
 本主题包含以下各节：  
  
- [源和目标](#sources_and_targets)  
  
- [消息传播](#propagation)  
  
- [消息块类型的概述](#overview)  
  
- [unbounded_buffer 类](#unbounded_buffer)  
  
- [overwrite_buffer 类](#overwrite_buffer)  
  
- [single_assignment 类](#single_assignment)  
  
- [call 类](#call)  
  
- [transformer 类](#transformer)  
  
- [choice 类](#choice)  
  
- [联接和 multitype_join 类](#join)  
  
- [timer 类](#timer)  
  
- [消息筛选](#filtering)  
  
- [消息保留](#reservation)  
  
##  <a name="a-namesourcesandtargetsa-sources-and-targets"></a><a name="sources_and_targets"></a> 源和目标  
 源和目标都是消息传递中的两个重要参与者。 一个 *源* 是指将消息发送的通信的终结点。 一个 *目标* 是指接收消息的通信的终结点。 您可以将作为从读取的终结点的源和目标作为写入到的终结点。 应用程序连接源和目标结合来形成 *消息传递网络*。  
  
 代理库使用两个抽象类来表示源和目标︰ [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) 和 [concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)。 消息块类型作用，因为源派生自 `ISource`; 消息块类型作用，因为目标派生自 `ITarget`。 消息块类型 act 作为源和目标派生自两 `ISource` 和 `ITarget`。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namepropagationa-message-propagation"></a><a name="propagation"></a> 消息传播  
 *消息传播* 是一种将一条消息从一个组件发送到另一个行为。 消息块提供的一条消息，它可以接受、 拒绝或推迟该消息。 每个消息块类型存储，并以不同的方式传输消息。 例如， `unbounded_buffer` 类存储无限的数量的消息， `overwrite_buffer` 类一次存储一条消息，并 transformer 类将存储每个消息的一个改写的版本。 在本文档后面的更详细地描述了这些消息块类型。  
  
 当消息块接受一条消息时，它可以根据需要执行工作并，如果消息块是一个源，将所生成的消息传递到网络的另一个成员。 消息块可以使用 filter 函数来拒绝不想接收的消息。 在本主题的部分中后面的更详细地描述了筛选 [消息筛选](#filtering)。 推迟消息的消息块可以保留该消息，并使用它更高版本。 中的部分中的本主题中后面的更详细地描述消息保留 [消息保留](#reservation)。  
  
 代理库以异步方式允许消息块或以同步方式将消息传递。 当您将邮件传递到消息块以同步方式，例如，通过使用 `send` 函数，则运行时可阻止当前上下文直到目标块接受或拒绝该消息。 当您将邮件传递到消息块以异步方式，例如，通过使用 `asend` 函数，则运行时将消息提供给目标，并且如果目标接受消息时，运行时计划传播到接收方的消息的异步任务。 运行时使用轻量级任务以协作方式传播消息。 轻量级任务的详细信息，请参阅 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 应用程序将连接源和目标在一起构成消息传递网络。 通常情况下，链接的网络并调用 `send` 或 `asend` 将数据传递到网络。 若要将源消息块连接到目标，调用 [concurrency::ISource::link_target](../Topic/ISource::link_target%20Method.md) 方法。 若要断开源块连接目标，调用 [concurrency::ISource::unlink_target](../Topic/ISource::unlink_target%20Method.md) 方法。 若要断开与所有其目标连接源块，调用 [concurrency::ISource::unlink_targets](../Topic/ISource::unlink_targets%20Method.md) 方法。 当预定义的消息块类型之一离开范围或被销毁时，它自动断开连接本身与所有目标块。 某些消息块类型限制可以写入的目标的最大数量。 以下部分介绍适用于预定义的消息块类型的限制。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameoverviewa-overview-of-message-block-types"></a><a name="overview"></a> 消息块类型的概述  
 下表简要介绍重要的消息块类型的角色。  
  
 [unbounded_buffer](#unbounded_buffer)  
 将存储消息的队列。  
  
 [overwrite_buffer](#overwrite_buffer)  
 存储可以写入和读取多个时间中的消息。  
  
 [single_assignment](#single_assignment)  
 存储可以写入一次并多次读取的消息。  
  
 [调用](#call)  
 在收到一条消息时执行工作。  
  
 [转换器](#transformer)  
 它接收数据并将该工作的结果发送到另一个目标块时执行工作。  `transformer` 类，可以作用于不同的输入和输出类型。  
  
 [选择](#choice)  
 从一组源中选择第一个可用消息。  
  
 [联接和多类型的联接](#join)  
 等待所有消息从一组源收到并随后将消息组合到另一个消息块的一条消息。  
  
 [计时器](#timer)  
 将一条消息按固定间隔发送到目标块。  
  
 这些消息块类型具有不同的特征，这使得它们适用于不同的情形。 以下是一些特征︰  
  
- *传播类型*︰ 消息块是否充当源的数据和 / 或数据，接收方。  
  
- *消息排序*︰ 消息块是否保持原始顺序不发送或接收消息。 每个预定义的消息块类型维持其发送或接收消息的原始顺序。  
  
- *源计数*︰ 的消息块可以读取的源的最大数目。  
  
- *目标计数*︰ 消息块可写入到的目标的最大数量。  
  
 下表显示如何这些特征的各种消息块类型相关联。  
  
|消息块类型|传播类型 （源、 目标，或两者）|消息顺序 （Ordered 或未排序）|源计数|目标计数|  
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|  
|`unbounded_buffer`|消息和传送|Ordered|不受限制|不受限制|  
|`overwrite_buffer`|消息和传送|Ordered|不受限制|不受限制|  
|`single_assignment`|消息和传送|Ordered|不受限制|不受限制|  
|`call`|目标|Ordered|不受限制|不适用|  
|`transformer`|消息和传送|Ordered|不受限制|1|  
|`choice`|消息和传送|Ordered|10|1|  
|`join`|消息和传送|Ordered|不受限制|1|  
|`multitype_join`|消息和传送|Ordered|10|1|  
|`timer`|源|不适用|不适用|1|  
  
 以下各节描述了更多详细信息中的消息块类型。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameunboundedbuffera-unboundedbuffer-class"></a><a name="unbounded_buffer"></a> unbounded_buffer 类  
  [Concurrency:: unbounded_buffer](../Topic/unbounded_buffer%20Class.md) 类表示一般用途的异步消息结构。 此类存储先进先出 (FIFO) 消息队列，此消息队列可由多个源写入或从多个目标读取。 在目标收到来自消息 `unbounded_buffer` 对象，从消息队列中移除该消息。 因此，尽管 `unbounded_buffer` 对象可以具有多个目标，只有一个目标将接收每条消息。 需将多条消息传递给另一个组件，且该组件必须接收每条消息时，`unbounded_buffer` 类十分有用。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `unbounded_buffer` 类。 本示例将发送到三个值 `unbounded_buffer` 对象，然后返回从同一对象中读取这些值。  
  
 [!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_1.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
334455  
```  
  
 有关完整的示例演示如何使用 `unbounded_buffer` 类，请参阅 [如何︰ 实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameoverwritebuffera-overwritebuffer-class"></a><a name="overwrite_buffer"></a> overwrite_buffer 类  
  [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) 类类似于 `unbounded_buffer` 类，不同之处在于 `overwrite_buffer` 对象用于存储只是一条消息。 此外，在目标收到来自消息 `overwrite_buffer` 对象，该消息不会从缓冲区删除。 因此，多个目标将接收到该消息的副本。  
  
  `overwrite_buffer` 类很有用，如果想要将多个消息传递到另一个组件，但该组件只需要最新的值。 需向多个组件广播消息时，此类也很有用。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `overwrite_buffer` 类。 本示例将发送到三个值 `overwrite _buffer` 对象，然后读取当前值从同一对象三次。 此示例是相似的示例 `unbounded_buffer` 类。 但是， `overwrite_buffer` 类存储只是一条消息。 此外，运行时不会删除该消息从 `overwrite_buffer` 对象后读取它。  
  
 [!CODE [concrt-overwrite_buffer-structure#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-overwrite_buffer-structure#1)]  
  
 该示例产生下面的输出：  
  
```Output  
555555  
```  
  
 有关完整的示例演示如何使用 `overwrite_buffer` 类，请参阅 [如何︰ 实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namesingleassignmenta-singleassignment-class"></a><a name="single_assignment"></a> single_assignment 类  
  [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 类类似于 `overwrite_buffer` 类，不同之处在于 `single_assignment` 对象可写入一次。 与 `overwrite_buffer` 类相似，在目标收到来自 `single_assignment` 对象的消息时，不会从该目标删除此消息。 因此，多个目标将接收到该消息的副本。  `single_assignment` 类很有用，当你想要一条消息广播给多个组件。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `single_assignment` 类。 本示例将发送到三个值 `single_assignment` 对象，然后读取当前值从同一对象三次。 此示例是相似的示例 `overwrite_buffer` 类。 尽管同时 `overwrite_buffer` 和 `single_assignment` 类存储一条消息， `single_assignment` 类可写入一次。  
  
 [!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_2.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
333333  
```  
  
 有关完整的示例演示如何使用 `single_assignment` 类，请参阅 [演练︰ 实现 Future](../../parallel/concrt/walkthrough-implementing-futures.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namecalla-call-class"></a><a name="call"></a> call 类  
  [Concurrency:: call](../../parallel/concrt/reference/call-class.md) 类充当接收数据时执行工作函数消息接收方。 此工作函数可以是 lambda 表达式、 函数对象或函数指针。 一个 `call` 因为它以并行方式对向其发送消息的其他组件操作对象的行为方式不同于普通的函数调用。 如果 `call` 对象执行工作时却突然收到消息，则它将此消息添加到队列。 每个 `call` 对象进程队列中的邮件中接收它们的顺序。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `call` 类。 此示例将创建 `call` 将打印到控制台收到每个值的对象。 该示例然后将发送到三个值 `call` 对象。 因为 `call` 对象处理单独的线程上的消息，此示例还使用一个计数器变量和一个 [事件](../../parallel/concrt/reference/event-class.md) 对象以确保 `call` 对象之前处理所有消息 `wmain` 函数返回。  
  
 [!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_3.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
334455  
```  
  
 有关完整的示例演示如何使用 `call` 类，请参阅 [如何︰ 为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nametransformera-transformer-class"></a><a name="transformer"></a> transformer 类  
  [Concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md) 类将为这两个消息接收方和消息发件人进行操作。  `transformer` 类类似于 `call` 类，因为它执行用户定义的工作函数在接收数据。 但是， `transformer` 类还将工作函数的结果发送到接收方对象。 如 `call` 对象， `transformer` 对象以并行方式对向其发送消息的其他组件进行操作。 如果 `transformer` 对象执行工作时却突然收到消息，则它将此消息添加到队列。 每个 `transformer` 对象处理其排队的邮件中接收它们的顺序。  
  
  `transformer` 类将其消息发送到一个目标。 如果您设置 `_PTarget` 到构造函数中的参数 `NULL`, ，稍后可以将目标指定通过调用 [concurrency::link_target](../Topic/source_block::link_target%20Method.md) 方法。  
  
 与提供的代理库中，所有其他异步消息块类型不同 `transformer` 类，可以作用于不同的输入和输出类型。 这种转换为另一个可从一种类型的数据的能力 `transformer` 类许多并发网络中的关键组件。 此外，可以添加更多细粒度的并行功能的工作函数中 `transformer` 对象。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `transformer` 类。 此示例将创建 `transformer` 对象，每个输入 `int` 值以便生成 0.33 `double` 值作为输出。 该示例然后接收转换后的值与同一个 `transformer` 对象，并输出到控制台。  
  
 [!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_4.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
10.8914.5218.15  
```  
  
 有关完整的示例演示如何使用 `transformer` 类，请参阅 [如何︰ 在数据管道中的使用 transformer](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namechoicea-choice-class"></a><a name="choice"></a> choice 类  
  [Concurrency:: choice](../../parallel/concrt/reference/choice-class.md) 类从一组源中选择第一个可用消息。  `choice` 类表示控制流机制，而不是一种数据流机制 (主题 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md) 描述数据流和控制流之间的差异)。  
  
 读取从选择的对象类似于调用 Windows API 函数 `WaitForMultipleObjects` ，它也 `bWaitAll` 参数设置为 `FALSE`。 但是， `choice` 类将数据绑定到事件本身而不是外部同步对象。  
  
 通常，您可以使用 `choice` 类一起 [concurrency:: receive](../Topic/receive%20Function.md) 函数来驱动应用程序中的控制流。 使用 `choice` 类时必须具有不同类型的消息缓冲区之间进行选择。 使用 `single_assignment` 类时必须具有相同类型的消息缓冲区之间进行选择。  
  
 将链接到源的顺序 `choice` 对象很重要，因为它可以确定选择哪一条消息。 例如，考虑这种情况，你可以将链接多个已包含到一条消息的消息缓冲区 `choice` 对象。  `choice` 对象从其链接到的第一个源中选择的消息。 链接的所有源之后, `choice` 对象保留在其中每个源收到一条消息的顺序。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `choice` 类。 此示例使用 [concurrency::make_choice](../Topic/make_choice%20Function.md) 函数来创建 `choice` 在三个消息块之间选择的对象。 该示例然后计算各种斐波那契数字，并将每个结果存储在不同的消息块中。 该示例然后向控制台显示一条消息，根据首先完成该操作。  
  
 [!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_5.cpp)]  
  
 该示例产生下面的示例输出︰  
  
```Output  
fib35 received its value first. Result = 9227465  
```  
  
 因为任务，计算 35<sup>th</sup> 斐波那契数字不保证完成第一次，此示例的输出可能会不同。  
  
 此示例使用 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 算法来计算并行斐波那契数字。 有关详细信息 `parallel_invoke`, ，请参阅 [并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 有关完整的示例演示如何使用 `choice` 类，请参阅 [如何︰ 选择之间完成的任务](../../parallel/concrt/how-to-select-among-completed-tasks.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namejoina-join-and-multitypejoin-classes"></a><a name="join"></a> 联接和 multitype_join 类  
  [Concurrency:: join](../../parallel/concrt/reference/join-class.md) 和 [concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md) 类使您可以等待的一组源的每个成员，用于接收消息。  `join` 类将具有通用的消息类型的源对象进行操作。  `multitype_join` 类将对可具有不同的消息类型的源对象进行操作。  
  
 从读取 `join` 或 `multitype_join` 对象类似于调用 Windows API 函数 `WaitForMultipleObjects` ，它也 `bWaitAll` 参数设置为 `TRUE`。 但是，就像 `choice` 对象， `join` 和 `multitype_join` 对象使用的一种事件机制，将数据绑定到事件本身而不是外部同步对象。  
  
 从读取 `join` 对象生成 std::[向量](../../standard-library/vector-class.md) 对象。 从读取 `multitype_join` 对象生成 std::[元组](../../standard-library/tuple-class.md) 对象。 元素出现在这些对象以相同的顺序，如其对应的源缓冲区链接到 `join` 或 `multitype_join` 对象。 因为源的链接的顺序缓冲区链接到 `join` 或 `multitype_join` 对象并在随后出现的元素的顺序与关联 `vector` 或 `tuple` 对象时，我们建议不取消链接从一个联接现有源缓冲区。 这样做可能导致未指定的行为。  
  
### <a name="greedy-versus-non-greedy-joins"></a>贪婪与非贪婪联接  
  `join` 和 `multitype_join` 类支持贪婪和非贪婪联接的概念。 一个 *贪婪联接* 接受来自其每个源的消息，如消息变为可用，直到所有消息都都可用。 一个 *非贪婪联接* 接收消息的两个阶段。 首先，非贪婪联接等待，直到它从其每个源提供一条消息。 第二，所有源消息都都可用后，非贪婪联接来尝试保留所有这些消息。 如果它可以保留每条消息，它使用所有消息，并将其传播到其目标。 否则为它释放时，或取消，消息保留并重新等待每个源收到一条消息。  
  
 贪婪联接比非贪婪联接的更好地执行，因为它们会立即接受消息。 但是，在极少数情况下，贪婪联接可能导致死锁。 当有多个联接，其中包含一个或多个共享的源对象时，请使用非贪婪联接。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `join` 类。 此示例使用 [concurrency::make_join](../Topic/make_join%20Function.md) 函数来创建 `join` 对象，它接收由三个 `single_assignment` 对象。 此示例计算各种斐波那契数字，则将在不同存储每个结果 `single_assignment` 对象，并向每个控制台然后将打印结果 `join` 对象容纳。 此示例是相似的示例 `choice` 类，不同之处在于 `join` 类会等待所有源消息块，用于接收消息。  
  
 [!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_6.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008  
```  
  
 此示例使用 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 算法来计算并行斐波那契数字。 有关详细信息 `parallel_invoke`, ，请参阅 [并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
 有关完整的示例演示如何使用 `join` 类，请参阅 [如何︰ 选择之间完成的任务](../../parallel/concrt/how-to-select-among-completed-tasks.md) 和 [演练︰ 使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nametimera-timer-class"></a><a name="timer"></a> timer 类  
 并发::[timer 类](../../parallel/concrt/reference/timer-class.md) 充当消息源。 一个 `timer` 对象将指定的时间段过后向目标发送一条消息。  `timer` 类很有用，当必须推迟发送一条消息，或者你想要将消息发送定期时间间隔。  
  
  `timer` 类将其消息发送到一个目标。 如果您设置 `_PTarget` 到构造函数中的参数 `NULL`, ，稍后可以将目标指定通过调用 [concurrency::ISource::link_target](../Topic/source_block::link_target%20Method.md) 方法。  
  
 一个 `timer` 对象可以重复或非重复。 若要创建重复的计时器，请将传递 `true` 为 `_Repeating` 时调用的构造函数参数。 否则，将传递 `false` 为 `_Repeating` 参数来创建了一个非重复的计时器。 如果重复的计时器，它将发送同一消息向其目标在每个时间间隔之后。  
  
 代理库创建 `timer` 处于非启动状态的对象。 若要启动计时器对象，调用 [concurrency::timer::start](../Topic/timer::start%20Method.md) 方法。 若要停止 `timer` 对象，请销毁的对象或调用 [concurrency::timer::stop](../Topic/timer::stop%20Method.md) 方法。 若要暂停重复的计时器，请调用 [concurrency::timer::pause](../Topic/timer::pause%20Method.md) 方法。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用的基本结构 `timer` 类。 该示例使用 `timer` 和 `call` 要报告的时间较长操作进度的对象。  
  
 [!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_7.cpp)]  
  
 该示例产生下面的示例输出︰  
  
```Output  
Computing fib(42)..................................................result is 267914296  
```  
  
 有关完整的示例演示如何使用 `timer` 类，请参阅 [如何︰ 定期发送一条消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namefilteringa-message-filtering"></a><a name="filtering"></a> 消息筛选  
 在创建消息块对象时，您可以提供 *filter 函数* ，它确定消息块是接受还是拒绝一条消息。 筛选器函数是保证的消息块只接收特定值的有用方式。  
  
 下面的示例演示如何创建 `unbounded_buffer` 使用筛选器函数仅接受偶数的对象。  `unbounded_buffer` 对象拒绝奇数，并因此不会传播到目标块的奇数。  
  
 [!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/CPP/asynchronous-message-blocks_8.cpp)]  
  
 该示例产生下面的输出：  
  
```Output  
0 2 4 6 8  
```  
  
 Filter 函数可以是 lambda 函数、 函数指针或函数对象。 每个筛选器函数采用以下形式之一。  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 若要消除不必要的情况下复制数据，使用第二种形式，当您具有按值传播的聚合类型。  
  
 消息筛选支持 *数据流* 编程模型，在接收数据时组件执行计算。 有关使用筛选器函数来控制消息传递网络中的数据流的示例，请参阅 [如何︰ 使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md), ，[演练︰ 创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md), ，和 [演练︰ 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namereservationa-message-reservation"></a><a name="reservation"></a> 消息保留  
 *消息保留* 允许消息块保留消息以供将来使用。 通常情况下，消息保留不直接使用。 但是，了解消息保留可以帮助您更好地了解一些预定义的消息块类型的行为。  
  
 请考虑非贪婪和贪婪联接。 这两种使用消息保留保留消息以供将来使用。 所述更早版本，非贪婪联接接收消息的两个阶段。 在第一阶段，非贪婪 `join` 对象会等待其每个源接收的消息。 非贪婪联接会尝试保留所有这些消息。 如果它可以保留每条消息，它使用所有消息，并将其传播到其目标。 否则为它释放时，或取消，消息保留并重新等待每个源收到一条消息。  
  
 贪婪联接，它还从多个源中读取输入的消息，使用消息保留它等待来自每个源收到一条消息时读取其他消息。 例如，请考虑从消息块接收消息的贪婪联接 `A` 和 `B`。 如果贪婪联接从 B 接收两条消息，但尚未收到来自消息 `A`, ，贪婪联接将保存从第二个消息的唯一的消息标识符 `B`。 贪婪联接接收来自消息后 `A` 并传播出这些消息，它会使用已保存的消息标识符以查看是否第二个消息从 `B` 仍然可用。  
  
 当您实现您自己的自定义消息块类型时，您可以使用消息保留。 有关如何创建自定义消息块类型的示例，请参阅 [演练︰ 创建自定义消息块](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)。  
  
 [[返回页首](#top)]  
  
## <a name="see-also"></a>另请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)

