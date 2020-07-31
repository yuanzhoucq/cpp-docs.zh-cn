---
title: 演练：创建自定义消息块
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: f95eaf7e1da41bd473ab15d12330d0177b98ccdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219490"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>演练：创建自定义消息块

本文档介绍如何创建按优先级对传入消息进行排序的自定义消息块类型。

尽管内置消息块类型提供范围广泛的功能，但你可以创建自己的消息块类型并对其进行自定义，以满足应用程序的要求。 有关异步代理库提供的内置消息块类型的说明，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="prerequisites"></a>先决条件

在开始本演练之前，请阅读以下文档：

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>个

本演练包含以下各节：

- [设计自定义消息块](#design)

- [定义 priority_buffer 类](#class)

- [完整示例](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>设计自定义消息块

消息块参与发送和接收消息的操作。 发送消息的消息块称为*源块*。 接收消息的消息块称为*目标块*。 发送和接收消息的消息块称为*传播程序块*。 代理库使用抽象类[concurrency：： ISource](../../parallel/concrt/reference/isource-class.md)来表示源块，并使用抽象类[Concurrency：： ITarget](../../parallel/concrt/reference/itarget-class.md)来表示目标块。 用作源的消息块类型是从派生的 `ISource` ; 作为目标的消息块类型派生自 `ITarget` 。

尽管可以直接从和派生消息块类型 `ISource` ，但 `ITarget` 代理库定义了三个基类，这些基类可执行所有消息块类型共有的很多功能，例如，以并发安全的方式处理错误并将消息块连接在一起。 [Concurrency：： source_block](../../parallel/concrt/reference/source-block-class.md)类派生自 `ISource` ，并向其他块发送消息。 [Concurrency：： target_block](../../parallel/concrt/reference/target-block-class.md)类从 `ITarget` 其他块派生并接收消息。 [Concurrency：:p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md)类派生自 `ISource` 和 `ITarget` ，并向其他块发送消息，并从其他块接收消息。 建议你使用这三个基类来处理基础结构详细信息，以便你可以专注于消息块的行为。

`source_block`、 `target_block` 和 `propagator_block` 类是在管理源和目标块之间以及管理消息处理方式的类型上的类型参数化的模板。 代理库定义了两个类型，这些类型执行链接管理[： concurrency：： single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md)和[concurrency：： multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)。 `single_link_registry`类可使消息块链接到一个源或一个目标。 `multi_link_registry`类可使消息块链接到多个源或多个目标。 代理库定义一个类，该类执行消息管理： [concurrency：： ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。 `ordered_message_processor`类使消息块能够按接收消息的顺序处理消息。

为了更好地了解消息块与其源和目标之间的关系，请考虑以下示例。 此示例演示[concurrency：：变压器](../../parallel/concrt/reference/transformer-class.md)类的声明。

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer`类派生自 `propagator_block` ，因此它既充当源块又充当目标块。 它接受类型为的消息 `_Input` ，并发送类型为的消息 `_Output` 。 `transformer`类将指定 `single_link_registry` 为任何目标块的链接管理器，并指定为 `multi_link_registry` 任何源块的链接管理器。 因此，一个 `transformer` 对象最多可以有一个目标和不限数量的源。

派生自的类 `source_block` 必须实现六种方法： [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets)、 [accept_message](reference/source-block-class.md#accept_message)、 [reserve_message](reference/source-block-class.md#reserve_message)、 [consume_message](reference/source-block-class.md#consume_message)、 [release_message](reference/source-block-class.md#release_message)和[resume_propagation](reference/source-block-class.md#resume_propagation)。 派生自的类 `target_block` 必须实现[propagate_message](reference/propagator-block-class.md#propagate_message)方法，并可以选择实现[send_message](reference/propagator-block-class.md#send_message)方法。 从派生的 `propagator_block` 在功能上等效于从 `source_block` 和派生 `target_block` 。

此 `propagate_to_any_targets` 方法由运行时调用，用于异步或同步处理任何传入的消息并传播任何传出消息。 此 `accept_message` 方法由目标块调用以接受消息。 许多消息块类型（如 `unbounded_buffer` ）仅将消息发送到接收它的第一个目标。 因此，它将消息的所有权转移到目标。 其他消息块类型（如[concurrency：： overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)）向其每个目标块提供消息。 因此，会 `overwrite_buffer` 为其每个目标创建一份消息副本。

`reserve_message`、 `consume_message` 、 `release_message` 和 `resume_propagation` 方法使消息块可以参与消息保留。 目标块 `reserve_message` 在提供消息时调用方法，并且必须保留消息以供以后使用。 目标块保留一条消息后，它可以调用 `consume_message` 方法以使用该消息或 `release_message` 方法来取消保留。 与方法一样 `accept_message` ，的实现 `consume_message` 可以传输消息的所有权或返回消息的副本。 在目标块使用或释放保留消息后，运行时将调用 `resume_propagation` 方法。 通常，此方法将从队列中的下一条消息开始继续消息传播。

运行时调用 `propagate_message` 方法，以将消息从另一个块异步传输到当前块。 此 `send_message` 方法类似于 `propagate_message` ，不同之处在于同步而不是以异步方式将消息发送到目标块。 的默认实现 `send_message` 拒绝所有传入的消息。 如果消息未通过与目标块关联的可选筛选器函数，则运行时不会调用这两个方法中的任何一个。 有关消息筛选器的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

[[顶部](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>定义 priority_buffer 类

`priority_buffer`类是自定义消息块类型，它先按优先级对传入消息进行排序，然后按接收消息的顺序对传入消息进行排序。 此 `priority_buffer` 类类似于[concurrency：： unbounded_buffer](reference/unbounded-buffer-class.md)类，因为它包含消息队列，并且它同时充当源和目标消息块，并且可以同时具有多个源和多个目标。 但是， `unbounded_buffer` 只会按照消息源接收消息的顺序来传播消息。

`priority_buffer`类接收包含和元素的 std：：[元组](../../standard-library/tuple-class.md)类型的消息 `PriorityType` `Type` 。 `PriorityType`指保存每个消息优先级的类型;`Type`引用消息的数据部分。 `priority_buffer`类发送类型为的消息 `Type` 。 `priority_buffer`该类还会管理两个消息队列：用于传入消息的[std：:p riority_queue](../../standard-library/priority-queue-class.md)对象和传出消息的 std：：[queue](../../standard-library/queue-class.md)对象。 当 `priority_buffer` 对象同时接收多个消息或在使用者读取消息之前接收多个消息时，按优先级对消息进行排序非常有用。

除了派生自的类必须实现的七种方法外 `propagator_block` ， `priority_buffer` 该类还会重写 `link_target_notification` 和 `send_message` 方法。 `priority_buffer`该类还定义了两个公共 helper 方法， `enqueue` 和 `dequeue` 一个私有帮助器方法 `propagate_priority_order` 。

下面的过程描述如何实现 `priority_buffer` 类。

#### <a name="to-define-the-priority_buffer-class"></a>定义 priority_buffer 类

1. 创建 c + + 头文件并将其命名为 `priority_buffer.h` 。 或者，你可以使用项目中包含的现有头文件。

1. 在中 `priority_buffer.h` ，添加以下代码。

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. 在 `std` 命名空间中，定义[std：： less](../../standard-library/less-struct.md)和[std：：更高](../../standard-library/greater-struct.md)的专用化，对 concurrency：：[message](../../parallel/concrt/reference/message-class.md)对象执行操作。

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   `priority_buffer`类 `message` 在对象中存储对象 `priority_queue` 。 这些类型特殊化使优先级队列能够根据消息的优先级对消息进行排序。 优先级是对象的第一个元素 `tuple` 。

1. 在 `concurrencyex` 命名空间中声明 `priority_buffer` 类。

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` 类从 `propagator_block` 派生。 因此，它可以发送和接收消息。 `priority_buffer`类可以有多个目标来接收类型为的消息 `Type` 。 它还可以有多个源来发送类型为的消息 `tuple<PriorityType, Type>` 。

1. 在 **`private`** 类的节中 `priority_buffer` ，添加以下成员变量。

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   `priority_queue`对象保存传入消息; `queue` 对象保存传出消息。 一个 `priority_buffer` 对象可以同时接收多个消息; `critical_section` 对象同步对输入消息的队列的访问。

1. 在 **`private`** 部分中，定义复制构造函数和赋值运算符。 这会阻止 `priority_queue` 对象被赋值。

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. 在 **`public`** 部分中，定义多个消息块类型常见的构造函数。 同时定义析构函数。

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. 在 **`public`** 部分中，定义方法 `enqueue` 和 `dequeue` 。 这些帮助器方法提供了一种将消息发送到对象并从对象接收消息的替代方法 `priority_buffer` 。

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. 在 **`protected`** 部分中，定义 `propagate_to_any_targets` 方法。

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   方法将位于 `propagate_to_any_targets` 输入队列前面的消息传输到输出队列，并在输出队列中传播所有消息。

1. 在 **`protected`** 部分中，定义 `accept_message` 方法。

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   当目标块调用方法时 `accept_message` ， `priority_buffer` 类会将消息的所有权转移到接受它的第一个目标块。 （这与的行为类似 `unbounded_buffer` 。）

1. 在 **`protected`** 部分中，定义 `reserve_message` 方法。

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   `priority_buffer`当提供的消息标识符与位于队列前面的消息的标识符相匹配时，类允许目标块保留一条消息。 换句话说，如果 `priority_buffer` 对象尚未收到附加消息，并且尚未传播到当前消息，则目标可以保留该消息。

1. 在 **`protected`** 部分中，定义 `consume_message` 方法。

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   目标块会调用 `consume_message` 以传输其保留的消息的所有权。

1. 在 **`protected`** 部分中，定义 `release_message` 方法。

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   目标块调用 `release_message` 以取消其对消息的保留。

1. 在 **`protected`** 部分中，定义 `resume_propagation` 方法。

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   在 `resume_propagation` 目标块使用或释放保留的消息之后，运行时调用。 此方法传播输出队列中的所有消息。

1. 在 **`protected`** 部分中，定义 `link_target_notification` 方法。

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   `_M_pReservedFor`成员变量由基类定义 `source_block` 。 此成员变量指向包含对输出队列前面的消息的保留的目标块（如果有）。 `link_target_notification`当新目标链接到对象时，运行时调用 `priority_buffer` 。 如果没有目标持有保留，此方法将传播输出队列中的所有消息。

1. 在 **`private`** 部分中，定义 `propagate_priority_order` 方法。

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   此方法传播输出队列中的所有消息。 队列中的每条消息都向每个目标块提供，直到其中一个目标块接受消息。 `priority_buffer`类保留传出消息的顺序。 因此，在此方法向目标块提供任何其他消息之前，目标块必须接受输出队列中的第一条消息。

1. 在 **`protected`** 部分中，定义 `propagate_message` 方法。

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   `propagate_message`方法启用 `priority_buffer` 类作为消息接收方或目标。 此方法接收提供的源块提供的消息，并将该消息插入到优先级队列中。 `propagate_message`然后，方法将所有输出消息异步发送到目标块。

   当调用[concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函数或消息块连接到其他消息块时，运行时调用此方法。

1. 在 **`protected`** 部分中，定义 `send_message` 方法。

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   此 `send_message` 方法类似于 `propagate_message` 。 但是，它会以同步方式而不是以异步方式发送输出消息。

   在同步发送操作期间，运行时调用此方法，如调用[concurrency：： send](reference/concurrency-namespace-functions.md#send)函数时。

`priority_buffer`类包含许多消息块类型中的典型构造函数重载。 一些构造函数重载采用[concurrency：：计划程序](../../parallel/concrt/reference/scheduler-class.md)或[Concurrency：： ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md)对象，使消息块可以由特定的任务计划程序管理。 其他构造函数重载采用筛选器函数。 筛选器函数使消息块能够根据其负载来接受或拒绝消息。 有关消息筛选器的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。 有关任务计划程序的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

由于 `priority_buffer` 类按优先级对消息进行排序，然后按接收消息的顺序对消息进行排序，因此，当调用[concurrency：： asend](reference/concurrency-namespace-functions.md#asend)函数或消息块连接到其他消息块时，此类最有用。

[[顶部](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>完整的示例

下面的示例演示类的完整定义 `priority_buffer` 。

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

下面的示例同时对对象执行多 `asend` 个[并发的：： receive](reference/concurrency-namespace-functions.md#receive)操作 `priority_buffer` 。

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

此示例将生成以下示例输出。

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer`类首先按优先级排序消息，然后按接收消息的顺序对消息进行排序。 在此示例中，在队列的前面插入了具有较高数字优先级的消息。

[[顶部](#top)]

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或将类的定义粘贴到名为的文件中，并将测试程序粘贴到名为的文件中， `priority_buffer` `priority_buffer.h` `priority_buffer.cpp` 然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe/EHsc priority_buffer .cpp**

## <a name="see-also"></a>另请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)
