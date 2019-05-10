---
title: 演练：创建自定义消息块
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: e7dfc5d78d2281d77b9ce882b302c4d7db776d3b
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856984"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>演练：创建自定义消息块

本文档介绍如何创建按优先级排序传入消息的自定义消息块类型。

尽管内置的消息块类型提供广泛的功能，可以创建您自己的消息块类型和自定义以满足你的应用程序的要求。 异步代理库提供的内置消息块类型的说明，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

## <a name="prerequisites"></a>系统必备

在开始本演练之前，请阅读以下文档：

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

##  <a name="top"></a> 部分

本演练包含以下各节：

- [设计自定义消息块](#design)

- [定义 priority_buffer 类](#class)

- [完整示例](#complete)

##  <a name="design"></a> 设计自定义消息块

消息块参与发送和接收消息的操作。 将消息发送的消息块被称为*源块*。 接收消息的消息块被称为*目标块*。 同时发送和接收消息的消息块被称为*传播器块*。 代理库使用抽象类[concurrency::ISource](../../parallel/concrt/reference/isource-class.md)表示源块和抽象类[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)表示目标块。 消息块类型作用，因为源派生自`ISource`; 消息块类型作用，因为目标派生`ITarget`。

尽管您可以直接从您的消息块类型进行派生`ISource`和`ITarget`，代理库定义了三种基类，这些类执行的许多功能共有的所有消息块类型，例如，处理错误和将消息块连接以并发安全的方式在一起。 [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md)类派生自`ISource`，并将消息发送给其他块。 [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md)类派生自`ITarget`和从其他块接收消息。 [Concurrency:: propagator_block](../../parallel/concrt/reference/propagator-block-class.md)类派生自`ISource`和`ITarget`和发送消息给其他块以及从其他块接收消息。 我们建议使用这三个基本类来处理基础结构详细信息，以便您可以集中精力消息块的行为。

`source_block`， `target_block`，和`propagator_block`类是在管理包的连接，或链接的类型、 源和目标块之间和管理如何处理消息的类型参数化的模板。 代理库定义执行链接管理的两种类型[concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md)并[concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)。 `single_link_registry`类允许消息块链接到一个源或目标。 `multi_link_registry`类允许消息块链接到多个源或多个目标。 代理库定义一个类，该类执行消息管理[concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。 `ordered_message_processor`类使消息块按顺序接收它们的顺序处理消息。

若要更好地了解消息块如何关联到其源和目标，请考虑下面的示例。 此示例显示如何声明[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)类。

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

`transformer`类派生自`propagator_block`，并因此充当源块和目标块。 它接受类型的消息`_Input`，并将发送类型的消息`_Output`。 `transformer`类指定`single_link_registry`作为任何目标块的链接管理器和`multi_link_registry`作为任何源块的链接管理器。 因此，`transformer`对象最多可包含一个目标，但无限的数量的源。

从派生的类`source_block`必须实现六种方法： [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets)， [accept_message](reference/source-block-class.md#accept_message)， [reserve_message](reference/source-block-class.md#reserve_message)， [consume_message](reference/source-block-class.md#consume_message)， [release_message](reference/source-block-class.md#release_message)，和[resume_propagation](reference/source-block-class.md#resume_propagation)。 从派生的类`target_block`必须实现[propagate_message](reference/propagator-block-class.md#propagate_message)方法，并且可以根据需要实现[send_message](reference/propagator-block-class.md#send_message)方法。 派生自`propagator_block`在功能上等效于同时从`source_block`和`target_block`。

`propagate_to_any_targets`方法由运行时以异步还是同步方式处理任何传入的消息并传播任何传出的消息。 `accept_message`由目标块接受的消息调用方法。 许多消息块类型，如`unbounded_buffer`，仅向会接收它的第一个目标发送消息。 因此，它将消息的所有权转移到目标。 其他消息块类型，如[concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md)，向每个目标块提供消息。 因此，`overwrite_buffer`为其每个目标创建消息的副本。

`reserve_message`， `consume_message`， `release_message`，和`resume_propagation`方法启用消息块参与消息保留。 目标将阻止调用`reserve_message`方法时它们提供一条消息，并且必须保留以供将来使用的消息。 目标块保留一条消息后，它可以调用`consume_message`方法以使用该消息或`release_message`方法来取消预订。 如同`accept_message`方法，实现`consume_message`可以传输消息的所有权或返回消息的副本。 目标块使用或释放保留的消息后，运行时调用`resume_propagation`方法。 通常情况下，此方法将继续从队列中的下一条消息传播。

运行时调用`propagate_message`方法来以异步方式将消息从另一个块传输到当前的一个。 `send_message`方法类似于`propagate_message`，只不过它以同步方式，而不是以异步方式将消息发送到目标块。 默认实现`send_message`拒绝传入的所有消息。 如果消息不会传递与目标块相关联的可选筛选器函数，运行时不会调用这些方法之一。 有关消息筛选器的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

[[返回页首](#top)]

##  <a name="class"></a> 定义 priority_buffer 类

`priority_buffer`类是传入消息进行排序首先按优先级别，然后按顺序接收消息的自定义消息块类型。 `priority_buffer`类相似[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)类，因为它包含队列的消息，以及由于它充当源和目标消息块，并且可以具有多个源和多个目标。 但是，`unbounded_buffer`消息仅在从其源接收消息的顺序上传播。

`priority_buffer`类接收的消息类型的 std::[元组](../../standard-library/tuple-class.md)包含`PriorityType`和`Type`元素。 `PriorityType` 是指保存的每条消息; 优先级的类型`Type`指的是消息的数据部分。 `priority_buffer`类发送类型的消息`Type`。 `priority_buffer`类还可管理两个消息队列： [std::priority_queue](../../standard-library/priority-queue-class.md)传入消息的对象和 std::[队列](../../standard-library/queue-class.md)为传出消息的对象。 按优先级排序的消息时，操作有用`priority_buffer`对象同时收到多条消息，或当它收到多条消息之前由使用者读取的任何消息。

除了七种方法，类的派生`propagator_block`必须实现`priority_buffer`类还重写`link_target_notification`和`send_message`方法。 `priority_buffer`类还定义了两个公共 helper 方法，`enqueue`并`dequeue`，和一个专用帮助器方法， `propagate_priority_order`。

以下过程介绍如何实现`priority_buffer`类。

#### <a name="to-define-the-prioritybuffer-class"></a>若要定义 priority_buffer 类

1. 创建C++标头文件并将其命名`priority_buffer.h`。 或者，可以使用现有的头文件的项目的一部分。

1. 在`priority_buffer.h`，添加以下代码。

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. 在`std`命名空间中，定义的专用化[std:: less](../../standard-library/less-struct.md)并[std:: greater](../../standard-library/greater-struct.md)的作用于并发::[消息](../../parallel/concrt/reference/message-class.md)对象。

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   `priority_buffer`类存储`message`中的对象`priority_queue`对象。 这些类型专用化启用优先级队列进行排序根据它们的优先级别的消息。 优先级是第一个元素的`tuple`对象。

1. 在中`concurrencyex`命名空间中，声明`priority_buffer`类。

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   `priority_buffer` 类派生自 `propagator_block`。 因此，它可以同时发送和接收消息。 `priority_buffer`类可以具有多个目标接收消息的类型的`Type`。 它还可以发送消息的类型的多个源`tuple<PriorityType, Type>`。

1. 在中`private`一部分`priority_buffer`类中，添加以下成员变量。

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   `priority_queue`对象包含传入消息;`queue`对象保留传出消息。 一个`priority_buffer`对象可以同时接收多个消息;`critical_section`对象同步到输入消息的队列的访问。

1. 在`private`部分中，定义的复制构造函数和赋值运算符。 这可以防止`priority_queue`对象赋值。

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. 在`public`部分中，定义多个消息块类型通用的构造函数。 此外定义析构函数。

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. 在中`public`部分中，定义的方法`enqueue`和`dequeue`。 这些帮助器方法提供了一种将消息发送到和接收消息从`priority_buffer`对象。

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. 在中`protected`部分中，定义`propagate_to_any_targets`方法。

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   `propagate_to_any_targets`方法传输位于输入输出队列到队列的开头和传播输出队列中的所有消息的消息。

10. 在中`protected`部分中，定义`accept_message`方法。

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   当目标块调用`accept_message`方法，`priority_buffer`类将该消息的所有权转移到第一个目标块接受它。 (这类似于的行为`unbounded_buffer`。)

11. 在中`protected`部分中，定义`reserve_message`方法。

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   `priority_buffer`类允许目标块提供的消息标识符匹配的消息位于队列开头的标识符时保留消息。 换而言之，目标可以保留该消息，如果`priority_buffer`对象尚未收到的其他消息，并且当前尚不传播。

12. 在中`protected`部分中，定义`consume_message`方法。

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   目标块调用`consume_message`要传输的消息，将其保留的所有权。

13. 在中`protected`部分中，定义`release_message`方法。

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   目标块调用`release_message`取消消息到其保留。

14. 在中`protected`部分中，定义`resume_propagation`方法。

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   运行时调用`resume_propagation`目标块使用或释放保留的消息之后。 此方法传播输出队列中的任何消息。

15. 在中`protected`部分中，定义`link_target_notification`方法。

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   `_M_pReservedFor`成员变量定义的基类， `source_block`。 此成员变量指向目标块后，如果有持有预订与前面的输出队列的消息。 运行时调用`link_target_notification`时，新目标已链接到`priority_buffer`对象。 此方法传播是输出队列中，如果没有目标存放保留任何消息。

16. 在中`private`部分中，定义`propagate_priority_order`方法。

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   此方法传播输出队列中的所有消息。 在队列中的每条消息提供到每个目标块，直到其中一个目标块接受消息。 `priority_buffer`类保留传出消息的顺序。 因此，输出队列中的第一个消息必须接受由目标块之前此方法还提供了向目标块的任何其他消息。

17. 在中`protected`部分中，定义`propagate_message`方法。

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   `propagate_message`方法使`priority_buffer`类作为消息接收方或目标。 此方法接收的消息，提供由提供的源块并将该消息插入到优先级队列。 `propagate_message`方法然后以异步方式发送所有消息输出到目标块。

   运行时调用此方法调用时[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函数或消息块连接至其他消息块。

18. 在中`protected`部分中，定义`send_message`方法。

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   `send_message`方法类似于`propagate_message`。 但是，它将发送以同步方式而不是以异步方式将输出消息。

   运行时调用此方法同步发送操作，例如当你调用期间[concurrency:: send](reference/concurrency-namespace-functions.md#send)函数。

`priority_buffer`类包含很平常的许多消息块类型的构造函数重载。 某些构造函数重载可获取[concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md)或[concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md)使消息块由特定任务计划程序管理的对象。 其他构造函数重载采用一个筛选器函数。 筛选器函数，允许接受或拒绝其有效负载基于消息的消息块。 有关消息筛选器的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。 有关任务计划程序的详细信息，请参阅[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。

因为`priority_buffer`类按优先级排序消息，然后接收消息的顺序，此类是最有用时异步接收消息，例如，在调用时[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函数或消息块连接至其他消息块。

[[返回页首](#top)]

##  <a name="complete"></a> 完整示例

下面的示例演示的完整定义`priority_buffer`类。

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

下面的示例将同时执行的若干`asend`并[concurrency:: receive](reference/concurrency-namespace-functions.md#receive)上的操作`priority_buffer`对象。

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

此示例生成下面的示例输出。

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

`priority_buffer`类订单的消息首先按优先级别，然后在其中它将接收消息的顺序。 在此示例中，向队列开头插入具有更大的数值优先级的消息。

[[返回页首](#top)]

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到的定义`priority_buffer`名为的文件中类`priority_buffer.h`和名为的文件中的测试程序`priority_buffer.cpp`然后在 Visual Studio 中运行以下命令命令提示符窗口。

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)
