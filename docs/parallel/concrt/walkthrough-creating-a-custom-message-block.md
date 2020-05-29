---
title: 演练：创建自定义消息块
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: 3386994dce68812cf3ed0852a24d8910cb903acf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368562"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>演练：创建自定义消息块

本文档介绍如何创建按优先级对传入邮件进行排序的自定义消息块类型。

尽管内置的消息块类型提供了广泛的功能，但您可以创建自己的消息块类型并对其进行自定义以满足应用程序的要求。 有关异步代理库提供的内置消息块类型的说明，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="prerequisites"></a>先决条件

在开始本演练之前，请阅读以下文档：

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>部分

本演练包含以下各节：

- [设计自定义消息块](#design)

- [定义priority_buffer类](#class)

- [完整示例](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>设计自定义消息块

消息块参与发送和接收消息的行为。 发送消息的消息块称为*源块*。 接收消息的消息块称为*目标块*。 发送和接收消息的消息块称为*传播器块*。 代理库使用抽象类[并发：：iSource](../../parallel/concrt/reference/isource-class.md)表示源块和抽象类[并发：：iTarget](../../parallel/concrt/reference/itarget-class.md)表示目标块。 充当源的消息块类型派生自`ISource`。充当目标的消息块类型派生自`ITarget`。

尽管可以直接从`ISource`和`ITarget`派生消息块类型，但代理库定义了三个基类，它们执行所有消息块类型共有的大部分功能，例如，以并发安全的方式处理错误和将消息块连接在一起。 [并发：：source_block](../../parallel/concrt/reference/source-block-class.md)类派生并`ISource`发送消息到其他块。 [并发：：target_block](../../parallel/concrt/reference/target-block-class.md)类派生自`ITarget`其他块并接收消息。 [并发：:p罗帕器_block](../../parallel/concrt/reference/propagator-block-class.md)类派生自`ISource`并将`ITarget`消息发送到其他块，它接收来自其他块的消息。 我们建议您使用这三个基类来处理基础结构详细信息，以便您可以专注于消息块的行为。

`target_block``propagator_block`和`source_block`类是在管理源和目标块之间的连接或链接的类型以及管理消息处理方式的类型上参数化的模板。 代理库定义了两种执行链接管理的类型，[并发：：single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md)[并发：multi_link_registry。](../../parallel/concrt/reference/multi-link-registry-class.md) 该`single_link_registry`类使消息块能够链接到一个源或一个目标。 该`multi_link_registry`类使消息块能够链接到多个源或多个目标。 代理库定义一个执行消息管理的类，[并发：：ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。 类`ordered_message_processor`使消息块能够按接收消息的顺序处理消息。

为了更好地了解消息块与其源和目标的关系，请考虑以下示例。 此示例显示[并发：：转换器](../../parallel/concrt/reference/transformer-class.md)类的声明。

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

类`transformer`派生自`propagator_block`，因此同时充当源块和目标块。 它接受类型`_Input`的消息并发送类型的消息`_Output`。 类`transformer`指定`single_link_registry`为任何目标块的链接管理器，并`multi_link_registry`指定为任何源块的链接管理器。 因此，一`transformer`个对象最多只能有一个目标和无限数量的源。

派生自`source_block`的类必须实现六种方法：propagate_to_any_targets、accept_message、reserve_message、consume_message、release_message和[release_message](reference/source-block-class.md#release_message)[reserve_message](reference/source-block-class.md#reserve_message)[resume_propagation。](reference/source-block-class.md#resume_propagation) [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets) [accept_message](reference/source-block-class.md#accept_message) [consume_message](reference/source-block-class.md#consume_message) 派生自`target_block`的类必须实现[propagate_message](reference/propagator-block-class.md#propagate_message)方法，并且可以选择实现[send_message](reference/propagator-block-class.md#send_message)方法。 派生自`propagator_block`在功能上等效于派生从 和`source_block``target_block`。

运行时`propagate_to_any_targets`调用该方法以异步或同步处理任何传入消息并传播出任何传出消息。 目标`accept_message`块调用该方法以接受消息。 许多消息块类型（如`unbounded_buffer`）仅向接收消息的第一个目标发送消息。 因此，它将消息的所有权转移到目标。 其他消息块类型（如[并发：：overwrite_buffer）](../../parallel/concrt/reference/overwrite-buffer-class.md)向其每个目标块提供消息。 因此，`overwrite_buffer`为其每个目标创建消息的副本。

、 和`resume_propagation`方法使消息块能够参与消息保留。 `reserve_message` `consume_message` `release_message` 当 Target`reserve_message`块收到消息时调用该方法，并且必须保留消息供以后使用。 目标块保留消息后，它可以调用`consume_message`方法以使用该消息或取消保留`release_message`的方法。 与 方法`accept_message`一样，实现`consume_message`可以转移消息的所有权或返回消息的副本。 在目标块使用或释放保留消息后，运行时将调用`resume_propagation`方法。 通常，此方法继续消息传播，从队列中的下一条消息开始。

运行时调用`propagate_message`该方法以异步方式将消息从另一个块传输到当前块。 该方法`send_message`类似于`propagate_message`，只不过它是同步的，而不是异步的，将消息发送到目标块。 的`send_message`默认实现拒绝所有传入消息。 如果消息未传递与目标块关联的可选筛选器函数，则运行时不会调用这些方法中的任何一个。 有关消息筛选器的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

[[顶部](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>定义priority_buffer类

类`priority_buffer`是一种自定义消息块类型，它首先按优先级对传入邮件进行排序，然后按接收消息的顺序排序。 类`priority_buffer`类似于[并发：：unbounded_buffer](reference/unbounded-buffer-class.md)类，因为它包含消息队列，也因为它同时充当源和目标消息块，可以同时具有多个源和多个目标。 但是，`unbounded_buffer`消息传播仅基于消息从其源接收消息的顺序。

类`priority_buffer`接收类型为 std 的消息：包含`PriorityType`和`Type`元素的[元组](../../standard-library/tuple-class.md)。 `PriorityType`指保存每条消息优先级的类型;`Type`引用消息的数据部分。 类`priority_buffer`发送类型 的消息`Type`。 该`priority_buffer`类还管理两个消息队列：传入消息的[std：:priity_queue](../../standard-library/priority-queue-class.md)对象和用于传出消息的 std：[队列对象](../../standard-library/queue-class.md)。 当`priority_buffer`对象同时接收多条消息或在使用者读取任何消息之前接收多条消息时，按优先级排序消息非常有用。

除了`propagator_block`派生自类必须实现的七种方法外`priority_buffer`，类还重写 和`link_target_notification`方法。 `send_message` 该`priority_buffer`类还定义了两个公共帮助器方法，`enqueue`和`dequeue`和 和 .`propagate_priority_order`和 一个私有帮助器方法 。

以下过程介绍如何实现类`priority_buffer`。

#### <a name="to-define-the-priority_buffer-class"></a>定义priority_buffer类

1. 创建一个C++头文件并命名`priority_buffer.h`它。 或者，您可以使用作为项目一部分的现有标头文件。

1. 在`priority_buffer.h`中，添加以下代码。

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. 在命名`std`空间中，定义[std：：：less](../../standard-library/less-struct.md)和[std：：：大于](../../standard-library/greater-struct.md)对并发作用的专门化：[消息](../../parallel/concrt/reference/message-class.md)对象。

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   类`priority_buffer`将对象`message`存储在对象中`priority_queue`。 这些类型专门化使优先级队列能够根据邮件的优先级对消息进行排序。 优先级是对象的第一个`tuple`元素。

1. 在命名`concurrencyex`空间中，声明类`priority_buffer`。

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` 类派生自 `propagator_block`。 因此，它可以发送和接收消息。 类`priority_buffer`可以有多个目标来接收类型`Type`的消息。 它还可以有多个源，发送类型`tuple<PriorityType, Type>`的消息。

1. 在`private`类的部分中`priority_buffer`，添加以下成员变量。

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   对象`priority_queue`保存传入消息;对象`queue`保存传出消息。 对象`priority_buffer`可以同时接收多条消息;对象`critical_section`同步对输入消息队列的访问。

1. 在部分`private`中，定义复制构造函数和赋值运算符。 这可以防止`priority_queue`对象被分配。

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. 在本节`public`中，定义许多消息块类型共有的构造函数。 还定义析构函数。

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. 在`public`部分中，定义方法和`enqueue``dequeue`。 这些帮助程序方法提供了向`priority_buffer`对象发送消息和接收来自对象的消息的替代方法。

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. 在部分`protected`中，定义`propagate_to_any_targets`方法。

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   该方法`propagate_to_any_targets`将输入队列前面的消息传输到输出队列，并传播输出队列中的所有消息。

1. 在部分`protected`中，定义`accept_message`方法。

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   当目标块调用`accept_message`该方法时，`priority_buffer`类将消息的所有权转移到接受它的第一个目标块。 （这类似于`unbounded_buffer`.） 的行为。

1. 在部分`protected`中，定义`reserve_message`方法。

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   当`priority_buffer`提供的消息标识符与队列前面的消息标识符匹配时，类允许目标块保留消息。 换句话说，如果对象尚未收到其他消息但尚未传播出当前`priority_buffer`消息，则目标可以保留该消息。

1. 在部分`protected`中，定义`consume_message`方法。

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   目标块调用`consume_message`以转移它保留的消息的所有权。

1. 在部分`protected`中，定义`release_message`方法。

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   目标块调用`release_message`以取消其对消息的保留。

1. 在部分`protected`中，定义`resume_propagation`方法。

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   目标块使用或`resume_propagation`释放保留消息之后的运行时调用。 此方法传播输出队列中的任何消息。

1. 在部分`protected`中，定义`link_target_notification`方法。

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   成员`_M_pReservedFor`变量由基类 定义`source_block`。 此成员变量指向目标块（如果有），该块对输出队列前面的消息保留。 当新目标链接到`link_target_notification`对象时，`priority_buffer`运行时调用。 如果没有目标保留，此方法会传播输出队列中的任何消息。

1. 在部分`private`中，定义`propagate_priority_order`方法。

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   此方法从输出队列中传播所有消息。 队列中的每个消息都提供给每个目标块，直到其中一个目标块接受该消息。 类`priority_buffer`保留传出消息的顺序。 因此，在此方法向目标块提供任何其他消息之前，目标块必须接受输出队列中的第一条消息。

1. 在部分`protected`中，定义`propagate_message`方法。

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   该方法`propagate_message`使`priority_buffer`类能够充当消息接收者或目标。 此方法接收提供的源块提供的消息，并将该消息插入到优先级队列中。 然后`propagate_message`，该方法异步地将所有输出消息发送到目标块。

   当您调用[并发：：asend](reference/concurrency-namespace-functions.md#asend)函数或消息块连接到其他消息块时，运行时调用此方法。

1. 在部分`protected`中，定义`send_message`方法。

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   该方法`send_message`类似于`propagate_message`。 但是，它同步而不是异步发送输出消息。

   运行时在同步发送操作期间调用此方法，例如调用[并发：：：发送](reference/concurrency-namespace-functions.md#send)函数时。

类`priority_buffer`包含构造函数重载，这些重载是许多消息块类型中常见的。 某些构造函数重载采用[并发：：计划程序](../../parallel/concrt/reference/scheduler-class.md)或[并发：：计划组](../../parallel/concrt/reference/schedulegroup-class.md)对象，使消息块能够由特定的任务调度程序管理。 其他构造函数重载采用筛选器函数。 筛选器功能使消息块能够根据其负载接受或拒绝消息。 有关消息筛选器的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。 有关任务计划程序的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

由于`priority_buffer`类按优先级排序，然后按接收消息的顺序排序，因此在异步接收消息时（例如，当您调用[并发：：asend](reference/concurrency-namespace-functions.md#asend)函数或消息块连接到其他消息块时）时，该类最有用。

[[顶部](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>完整示例

下面的示例显示了`priority_buffer`类的完整定义。

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

以下示例同时执行多个`asend`[并发：：接收](reference/concurrency-namespace-functions.md#receive)`priority_buffer`对象上的操作。

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

此示例生成以下示例输出。

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

类`priority_buffer`首先按优先级排序消息，然后按接收消息的顺序排序。 在此示例中，具有更大数字优先级的消息插入到队列的前面。

[[顶部](#top)]

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将`priority_buffer`类的定义粘贴到已命名的`priority_buffer.h`文件中，并将测试程序粘贴到名为`priority_buffer.cpp`的文件中，然后在 Visual Studio 命令提示窗口中运行以下命令。

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>另请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)
