---
title: 异步消息块
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: b78b4db4dda33e0a94da3624ea1ffd8748a601f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586116"
---
# <a name="asynchronous-message-blocks"></a>异步消息块

代理库提供了多个消息块类型，您可以将应用程序组件间的消息传播以线程安全的方式。 消息块会使用这些类型通常与各种消息传递例程，如[concurrency:: send](reference/concurrency-namespace-functions.md#send)， [concurrency:: asend](reference/concurrency-namespace-functions.md#asend)， [concurrency:: receive](reference/concurrency-namespace-functions.md#receive)，并[concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive)。 有关消息传递由代理库定义的例程的详细信息，请参阅[消息传递函数](../../parallel/concrt/message-passing-functions.md)。

##  <a name="top"></a> 部分

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

##  <a name="sources_and_targets"></a> 源和目标

源和目标是在消息传递两个重要的参与方。 一个*源*是指将消息发送的通信的终结点。 一个*目标*指的是所接收消息的通信的终结点。 您可以将读取从一个终结点作为源和目标为写入到的终结点。 应用程序连接源和目标组合在一起，向窗体*消息传递网络*。

代理库使用两个抽象类来表示源和目标： [concurrency::ISource](../../parallel/concrt/reference/isource-class.md)并[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)。 消息块类型作用，因为源派生自`ISource`; 消息块类型作用，因为目标派生`ITarget`。 消息块类型的定义为源和目标派生自`ISource`和`ITarget`。

[[返回页首](#top)]

##  <a name="propagation"></a> 消息传播

*消息传播*是到另一个组件中发送一条消息的操作。 消息块提供的一条消息，它可以接受、 拒绝，或推迟的消息。 每个消息块类型存储，并以不同方式传输消息。 例如，`unbounded_buffer`类存储无限的数量的消息，`overwrite_buffer`类一次存储一条消息和 transformer 类存储每个消息的一个改写的版本。 在本文档后面的更详细地介绍了这些消息块类型。

当消息块接受一条消息时，它可以根据需要执行工作，并且如果消息块是一个源，将生成的消息传递到网络的另一个成员。 消息块可以使用筛选器函数以拒绝不想接收的消息。 稍后在本主题中，在部分中的更详细地描述了筛选器是[消息筛选](#filtering)。 推迟消息的消息块可保留该消息并使用它更高版本。 稍后在本主题中，在部分中的更详细地描述消息保留[消息保留](#reservation)。

代理库以异步方式允许消息块或以同步方式将消息传递。 当您将邮件传递到消息块以同步方式，例如，通过使用`send`函数，直到目标块接受或拒绝该消息运行时阻止当前上下文。 当您将邮件传递到消息块以异步方式，例如，通过使用`asend`函数，运行时提供消息到目标，并且如果目标接受消息，运行时计划传播消息的异步任务向接收方。 运行时使用轻量级任务以协作方式传播消息。 轻量级任务有关的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

应用程序将连接源和目标在一起构成消息传递网络。 通常情况下，链接的网络和调用`send`或`asend`将数据传递到网络。 若要将源消息块连接到的目标，请调用[concurrency::ISource::link_target](reference/isource-class.md#link_target)方法。 若要断开源块与目标的连接，调用[concurrency::ISource::unlink_target](reference/isource-class.md#unlink_target)方法。 若要将源块断开所有其目标，请调用[concurrency::ISource::unlink_targets](reference/isource-class.md#unlink_targets)方法。 在预定义的消息块类型之一离开范围或被销毁后，它自动断开连接本身从任何目标块。 某些消息块类型限制可以写入的目标的最大数目。 以下部分介绍适用于预定义的消息块类型的限制。

[[返回页首](#top)]

##  <a name="overview"></a> 消息块类型的概述

下表简要介绍重要的消息块类型的角色。

[unbounded_buffer](#unbounded_buffer)<br/>
存储队列的消息。

[overwrite_buffer](#overwrite_buffer)<br/>
存储可以写入到和从多次读取的消息。

[single_assignment](#single_assignment)<br/>
存储可以写入一次并从多个时间中读取的消息。

[调用](#call)<br/>
当它收到一条消息时执行工作。

[transformer](#transformer)<br/>
执行工作时它接收数据并将该工作的结果发送到另一个目标块。 `transformer`类可以处理不同的输入和输出类型。

[choice](#choice)<br/>
从一组源中选择的第一个可用消息。

[联接和多类型的联接](#join)<br/>
等待所有消息收到来自一组源，然后将消息组合到一个消息中的另一个消息块。

[timer](#timer)<br/>
向目标块按固定间隔发送一条消息。

这些消息块类型具有不同的特征，使它们适用于不同的情况。 以下是一些特征：

- *传播类型*： 消息块是否充当源的数据和 / 或数据，接收方。

- *消息排序*： 消息块是否保持原始顺序发送或接收消息。 每个预定义的消息块类型维持其发送或接收消息的原始顺序。

- *源计数*： 消息块可以读取的源的最大数目。

- *目标计数*： 消息块可以将写入到的目标的最大数目。

下表显示了这些特征如何与各种消息块类型相关联。

|消息块类型|传播类型 （源、 目标，或两者）|消息顺序 （有序或无序列表）|源计数|目标计数|
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

以下部分介绍更多详细信息中的消息块类型。

[[返回页首](#top)]

##  <a name="unbounded_buffer"></a> unbounded_buffer 类

[Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)类表示常规用途的异步消息结构。 此类存储先进先出 (FIFO) 消息队列，此消息队列可由多个源写入或从多个目标读取。 在目标收到来自消息`unbounded_buffer`对象，从消息队列中删除该消息。 因此，尽管`unbounded_buffer`对象可以具有多个目标，只有一个目标将接收每条消息。 需将多条消息传递给另一个组件，且该组件必须接收每条消息时，`unbounded_buffer` 类十分有用。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`unbounded_buffer`类。 此示例发送到三个值`unbounded_buffer`对象，然后这些值从读回相同的对象。

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

该示例产生下面的输出：

```Output
334455
```

有关完整示例，演示如何使用`unbounded_buffer`类，请参阅[如何： 实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[返回页首](#top)]

##  <a name="overwrite_buffer"></a> overwrite_buffer 类

[Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)类相似`unbounded_buffer`类，不同之处在于`overwrite_buffer`对象将存储只是一条消息。 此外，在目标收到来自消息`overwrite_buffer`对象，该消息不会从缓冲区删除。 因此，多个目标将接收到该消息的副本。

`overwrite_buffer`类很有用，当你想要将多个消息传递到另一个组件，而该组件需要最新的值。 需向多个组件广播消息时，此类也很有用。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`overwrite_buffer`类。 此示例发送到三个值`overwrite _buffer`对象，然后读取当前值相同的对象从三次。 此示例中是类似的示例`unbounded_buffer`类。 但是，`overwrite_buffer`类存储只是一条消息。 此外，运行时不会删除从消息`overwrite_buffer`对象后读取它。

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

该示例产生下面的输出：

```Output
555555
```

有关完整示例，演示如何使用`overwrite_buffer`类，请参阅[如何： 实现各种制造者-使用者模式](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)。

[[返回页首](#top)]

##  <a name="single_assignment"></a> single_assignment 类

[3&gt;concurrency::single_assignment&lt;3}](../../parallel/concrt/reference/single-assignment-class.md)类相似`overwrite_buffer`类，不同之处在于`single_assignment`对象可以写入仅一次。 与 `overwrite_buffer` 类相似，在目标收到来自 `single_assignment` 对象的消息时，不会从该目标删除此消息。 因此，多个目标将接收到该消息的副本。 `single_assignment`类很有用，当您需要广播到多个组件的一条消息。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`single_assignment`类。 此示例发送到三个值`single_assignment`对象，然后读取当前值相同的对象从三次。 此示例中是类似的示例`overwrite_buffer`类。 尽管同时`overwrite_buffer`并`single_assignment`类存储一条消息，`single_assignment`类可以写入仅一次。

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

该示例产生下面的输出：

```Output
333333
```

有关完整示例，演示如何使用`single_assignment`类，请参阅[演练： 实现 Future](../../parallel/concrt/walkthrough-implementing-futures.md)。

[[返回页首](#top)]

##  <a name="call"></a> call 类

[Concurrency:: call](../../parallel/concrt/reference/call-class.md)类充当一个消息接收器，接收数据时执行工作函数。 此工作函数可以是 lambda 表达式、 函数对象或函数指针。 一个`call`因为它以将消息发送到其他组件的并行操作对象的行为方式不同于普通的函数调用。 如果`call`对象执行工作时收到的消息，则它将该消息添加到队列。 每个`call`对象进程队列中的邮件中接收它们的顺序。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`call`类。 此示例将创建`call`打印到控制台收到的每个值的对象。 该示例然后将发送到三个值`call`对象。 因为`call`对象处理单独线程上的消息，本示例还使用计数器变量和一个[事件](../../parallel/concrt/reference/event-class.md)对象，以确保该`call`对象之前处理所有消息`wmain`函数将返回。

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

该示例产生下面的输出：

```Output
334455
```

有关完整示例，演示如何使用`call`类，请参阅[如何： 为 call 和 transformer 类提供工作函数](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)。

[[返回页首](#top)]

##  <a name="transformer"></a> transformer 类

[Concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)类将为这两个消息接收方和消息发件人进行操作。 `transformer`类相似`call`类，因为接收数据时，它执行用户定义工作函数。 但是，`transformer`类还将工作函数的结果发送到接收方对象。 像`call`对象，`transformer`对象以并行方式对向其发送消息的其他组件进行操作。 如果`transformer`对象执行工作时收到的消息，则它将该消息添加到队列。 每个`transformer`对象处理其接收它们的顺序中的排队的消息。

`transformer`类将其消息发送到一个目标。 如果您设置`_PTarget`将构造函数中的参数`NULL`，可以稍后通过调用指定目标[concurrency::link_target](reference/source-block-class.md#link_target)方法。

与提供的代理库中，所有其他异步消息块类型不同`transformer`类可以处理不同的输入和输出类型。 数据从一种类型转换为另一个使这种能力`transformer`类在多个并发的网络中的关键组件。 此外，可以在的工作函数中添加更多细粒度的并行功能`transformer`对象。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`transformer`类。 此示例将创建`transformer`对象，每个输入`int`值以便生成 0.33`double`值作为输出。 该示例然后接收转换后的值从同一个`transformer`对象，并将其打印到控制台。

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

该示例产生下面的输出：

```Output
10.8914.5218.15
```

有关完整示例，演示如何使用`transformer`类，请参阅[如何： 在数据管道中的使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

[[返回页首](#top)]

##  <a name="choice"></a> choice 类

[Concurrency:: choice](../../parallel/concrt/reference/choice-class.md)类从一组源中选择的第一个可用消息。 `choice`类表示而不是一种数据流机制的控制流机制 (主题[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)描述数据流和控制流之间的差异)。

从所选对象读取类似于调用 Windows API 函数`WaitForMultipleObjects`时，它具有`bWaitAll`参数设置为`FALSE`。 但是，`choice`类将数据绑定到事件本身而不是外部的同步对象。

通常情况下，使用`choice`类一起[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)函数来驱动应用程序中的控制流。 使用`choice`类时必须具有不同类型的消息缓冲区之间进行选择。 使用`single_assignment`类时必须具有相同的类型的消息缓冲区之间进行选择。

将链接到源的顺序`choice`对象很重要，因为它可以确定选择哪一条消息。 例如，假设您可以将链接多个已包含一条消息的消息缓冲区`choice`对象。 `choice`对象从其链接到的第一个源中选择消息。 链接的所有源之后,`choice`对象保留在其中每个源接收消息的顺序。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`choice`类。 此示例使用[concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice)函数来创建`choice`对象在三个消息块之间选择。 该示例然后计算各种斐波那契数字，并将每个结果存储在不同的消息块中。 该示例然后会将基于首先完成该操作的消息打印到控制台。

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

此示例产生下面的示例输出：

```Output
fib35 received its value first. Result = 9227465
```

因为任务，用于计算 35<sup>th</sup>斐波那契数字不保证首先完成，此示例的输出而异。

此示例使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法来计算中并行的斐波那契数字。 有关详细信息`parallel_invoke`，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

有关完整示例，演示如何使用`choice`类，请参阅[如何： 选择在完成任务](../../parallel/concrt/how-to-select-among-completed-tasks.md)。

[[返回页首](#top)]

##  <a name="join"></a> 联接和 multitype_join 类

[Concurrency:: join](../../parallel/concrt/reference/join-class.md)并[concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md)类使你可以等待一组源的每个成员，才能收到一条消息。 `join`类将具有通用的消息类型的源对象进行操作。 `multitype_join`类将可以具有不同的消息类型的源对象进行操作。

从读取`join`或`multitype_join`对象类似于调用 Windows API 函数`WaitForMultipleObjects`当具有`bWaitAll`参数设置为`TRUE`。 但是，就像`choice`对象，`join`和`multitype_join`对象使用的一种事件机制，将数据绑定到事件本身而不是外部的同步对象。

从读取`join`对象生成 std::[向量](../../standard-library/vector-class.md)对象。 从读取`multitype_join`对象生成 std::[元组](../../standard-library/tuple-class.md)对象。 元素出现在相同的顺序中的这些对象，如链接到其相应的源缓冲区`join`或`multitype_join`对象。 因为缓冲区链接到源的链接的顺序`join`或`multitype_join`对象并在随后出现的元素的顺序与关联`vector`或`tuple`对象，我们建议不取消链接从现有源缓冲区联接。 执行此操作可能会导致未指定的行为。

### <a name="greedy-versus-non-greedy-joins"></a>贪婪与非贪婪联接

`join`和`multitype_join`类支持的贪婪和非贪婪联接概念。 一个*贪婪联接*接受来自其每个源的消息，消息可用，直到所有消息都都可用。 一个*非贪婪联接*接收消息的两个阶段。 首先，非贪婪联接等待，直到它从其每个源提供一条消息。 其次，源的所有消息都都可用后，非贪婪联接会尝试保留所有这些消息。 如果它可以保留每条消息，它使用的所有消息，并将其传播到其目标。 否则为它释放，或取消，消息保留项并再次等待每个源接收的消息。

贪婪联接比非贪婪联接更好地执行，因为它们立即接受消息。 但是，在极少数情况下，贪婪联接可以导致死锁。 如果你有包含一个或多个共享的源对象的多个联接，请使用非贪婪联接。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`join`类。 此示例使用[concurrency::make_join](reference/concurrency-namespace-functions.md#make_join)函数来创建`join`对象，它接收从三个`single_assignment`对象。 此示例计算各种斐波那契数字，将每个结果存储在不同`single_assignment`对象，然后再将打印到控制台中每个结果`join`对象持有。 此示例中是类似的示例`choice`类，不同之处在于`join`类会等待所有源消息块接收的消息。

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

该示例产生下面的输出：

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

此示例使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)算法来计算中并行的斐波那契数字。 有关详细信息`parallel_invoke`，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

有关完整示例，演示如何使用`join`类，请参阅[如何： 选择在完成任务](../../parallel/concrt/how-to-select-among-completed-tasks.md)并[演练： 使用 join 避免死锁](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

[[返回页首](#top)]

##  <a name="timer"></a> timer 类

并发::[timer 类](../../parallel/concrt/reference/timer-class.md)充当消息源。 一个`timer`对象将经过一段指定的时间后向目标发送一条消息。 `timer`必须延迟发送一条消息，或你想要在固定时间间隔发送一条消息时，类非常有用。

`timer`类将其消息发送到一个目标。 如果您设置`_PTarget`将构造函数中的参数`NULL`，可以稍后通过调用指定目标[concurrency::ISource::link_target](reference/source-block-class.md#link_target)方法。

一个`timer`可以重复或非重复对象。 若要创建重复的计时器，请将传递 **，则返回 true**为`_Repeating`时调用的构造函数的参数。 否则，将传递**false**为`_Repeating`参数来创建一个非重复的计时器。 如果重复的计时器，它发送同一条消息到其目标在每个时间间隔之后。

代理库创建`timer`处于非启动状态的对象。 若要启动计时器对象，调用[concurrency::timer::start](reference/timer-class.md#start)方法。 若要停止`timer`对象，请销毁的对象或调用[concurrency::timer::stop](reference/timer-class.md#stop)方法。 若要暂停重复计时器，调用[concurrency::timer::pause](reference/timer-class.md#pause)方法。

### <a name="example"></a>示例

下面的示例演示如何使用的基本结构`timer`类。 该示例使用`timer`和`call`对象来报告进度的较长的操作。

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

此示例产生下面的示例输出：

```Output
Computing fib(42)..................................................result is 267914296
```

有关完整示例，演示如何使用`timer`类，请参阅[如何： 定期发送一条消息](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)。

[[返回页首](#top)]

##  <a name="filtering"></a> 消息筛选

在创建消息块对象时，你可以提供*筛选器函数*，它确定消息块是接受还是拒绝消息。 筛选器函数是有用的方式，以保证的消息块只接收特定值。

下面的示例演示如何创建`unbounded_buffer`使用筛选器函数以接受只有偶数的对象。 `unbounded_buffer`对象拒绝奇数，并因此不会传播到目标块的奇数。

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

该示例产生下面的输出：

```Output
0 2 4 6 8
```

筛选器函数可以是 lambda 函数、 函数指针或函数对象。 每个筛选器函数采用以下形式之一。

```Output
bool (T)
bool (T const &)
```

若要消除不必要的数据复制，使用第二个窗体时您具有按值传播的聚合类型。

消息筛选支持*数据流*编程模型，在接收数据时组件执行计算。 有关使用筛选器函数来控制流的消息传递网络中的数据的示例，请参阅[如何： 使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)，[演练： 创建数据流代理](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)，和[演练： 创建图像处理网络](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[返回页首](#top)]

##  <a name="reservation"></a> 消息保留

*消息保留*允许消息块来保留一条消息以供将来使用。 通常情况下，消息保留不直接使用。 但是，了解消息保留可以帮助您更好地了解一些预定义的消息块类型的行为。

请考虑非贪婪和贪婪联接。 这两种使用消息保留保留消息以供将来使用。 描述更早版本，非贪婪联接接收消息的两个阶段。 在第一阶段，非贪婪`join`对象会等待其每个源接收的消息。 非贪婪联接会尝试保留所有这些消息。 如果它可以保留每条消息，它使用的所有消息，并将其传播到其目标。 否则为它释放，或取消，消息保留项并再次等待每个源接收的消息。

贪婪联接，它还从多个源读取输入的消息，使用消息保留它在等待从每个源接收的消息读取其他消息。 例如，请考虑从消息块接收消息的贪婪联接`A`和`B`。 如果贪婪联接从 B 接收两条消息，但尚未收到来自的消息`A`，贪婪联接将保存来自的第二个消息的唯一的消息标识符`B`。 贪婪联接收到来自后`A`，并将传播这些消息，它使用已保存的消息标识符以查看是否第二个消息从`B`仍然可用。

实现您自己的自定义消息块类型时，可以使用消息保留。 有关如何创建自定义消息块类型的示例，请参阅[演练： 创建自定义消息块](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)。

[[返回页首](#top)]

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)

