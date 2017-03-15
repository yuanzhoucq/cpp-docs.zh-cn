---
title: "演练：创建自定义消息块 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "创建自定义消息块 [并发运行时]"
  - "自定义消息块，创建 [并发运行时]"
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# 演练：创建自定义消息块
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍如何创建按优先级排序传入消息的自定义消息块类型。  
  
 尽管内置的消息块类型提供广泛的功能，可以创建您自己的消息块类型和自定义以符合您的应用程序的要求。 异步代理库提供的内置消息块类型的说明，请参阅 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="prerequisites"></a>先决条件  
 在开始本演练之前，请阅读以下文档︰  
  
- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 部分  
 本演练包含以下各节︰  
  
- [设计自定义消息块](#design)  
  
- [定义 priority_buffer 类](#class)  
  
- [完整示例](#complete)  
  
##  <a name="a-namedesigna-designing-a-custom-message-block"></a><a name="design"></a> 设计自定义消息块  
 消息块参与发送和接收消息的操作。 将消息发送的消息块被称为 *源块*。 接收消息的消息块被称为 *目标块*。 同时发送和接收消息的消息块被称为 *传播器块*。 代理库使用抽象类 [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) 来表示源块和抽象类 [concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md) 表示目标块。 消息块类型作用，因为源派生自 `ISource`; 消息块类型作用，因为目标派生自 `ITarget`。  
  
 尽管您可以直接从消息块类型进行派生 `ISource` 和 `ITarget`, 、 的代理库定义了三种基类以执行大部分普遍适用于所有消息块类型的功能，例如，处理错误和连接消息将阻止在一起以并发安全的方式。  [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) 类派生自 `ISource` 并将消息发送给其他块。  [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) 类派生自 `ITarget` 并从其他块接收消息。  [Concurrency:: propagator_block](../../parallel/concrt/reference/propagator-block-class.md) 类派生自 `ISource` 和 `ITarget` 并发送消息给其他块以及从其他块接收消息。 我们建议使用这三种基类以处理基础结构详细信息，从而确保您可以专注于消息块的行为。  
  
  `source_block`, ，`target_block`, ，和 `propagator_block` 类是管理连接，或链接的类型、 源和目标块之间以及管理如何处理消息的类型的参数化的模板。 代理库定义两种执行链接管理类型 [concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) 和 [concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md)。  `single_link_registry` 类允许消息块要链接到一个源或目标。  `multi_link_registry` 类允许消息块链接到多个源或多个目标。 代理库定义一个执行消息管理的类 [concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md)。  `ordered_message_processor` 类允许消息块来处理消息，它将接收它们的顺序。  
  
 若要更好地了解消息块与它们的源和目标，请考虑下面的示例。 此示例演示的声明 [concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md) 类。  
  
 [!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_1.cpp)]  
  
  `transformer` 类派生自 `propagator_block`, ，并因此充当源块和目标块。 它接受类型的消息 `_Input` 并发送类型的消息 `_Output`。  `transformer` 类指定 `single_link_registry` 作为所有目标块的链接管理器和 `multi_link_registry` 作为所有源块的链接管理器。 因此， `transformer` 一个目标，无限个源最多可以有对象。  
  
 派生自的类 `source_block` 必须实现六种方法︰ [propagate_to_any_targets](../Topic/source_block::propagate_to_any_targets%20Method.md), ，[accept_message](../Topic/source_block::accept_message%20Method.md), ，[reserve_message](../Topic/source_block::reserve_message%20Method.md), ，[consume_message](../Topic/source_block::consume_message%20Method.md), ，[release_message](../Topic/source_block::release_message%20Method.md), ，和 [resume_propagation](../Topic/source_block::resume_propagation%20Method.md)。 派生自的类 `target_block` 必须实现 [propagate_message](../Topic/propagator_block::propagate_message%20Method.md) 方法，并且可以根据需要实现 [send_message](../Topic/propagator_block::send_message%20Method.md) 方法。 派生自 `propagator_block` 在功能上等效于同时从 `source_block` 和 `target_block`。  
  
  `propagate_to_any_targets` 方法由运行时以异步还是同步处理传入的消息并传播任何传出消息。  `accept_message` 按目标块以接受的消息调用方法。 许多消息块类型，如 `unbounded_buffer`, ，消息仅发送给将接收它的第一个目标。 因此，它将消息的所有权转移到目标。 其他消息块类型，如 [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), ，向其每个目标块提供消息。 因此， `overwrite_buffer` 为其每个目标创建消息的副本。  
  
  `reserve_message`, ，`consume_message`, ，`release_message`, ，和 `resume_propagation` 方法允许消息块参与消息保留。 目标块调用 `reserve_message` 方法时它们提供了一条消息，并且具有保留以供以后使用该消息。 目标块保留一条消息后，它可以调用 `consume_message` 方法，以使用该消息或 `release_message` 方法来取消预订。 与 `accept_message` 方法时，实现 `consume_message` 可以传输消息的所有权或返回消息的副本。 目标块使用或释放保留的消息后，运行时会调用 `resume_propagation` 方法。 通常情况下，此方法将继续从队列中的下一个消息的消息传播。  
  
 运行时调用 `propagate_message` 方法，以异步方式将消息从另一个块传输到当前。  `send_message` 方法类似于 `propagate_message`, ，只不过它以同步方式，而不是以异步方式将消息发送到目标块。 默认实现 `send_message` 拒绝所有传入的消息。 如果消息未通过目标块相关联的可选筛选器函数，则运行时不调用上述任一方法。 有关消息筛选器的详细信息，请参阅 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
 [[返回页首](#top)]  
  
##  <a name="a-nameclassa-defining-the-prioritybuffer-class"></a><a name="class"></a> 定义 priority_buffer 类  
  `priority_buffer` 类是按优先级别，然后按顺序接收消息的顺序首先排序传入消息的自定义消息块类型。  `priority_buffer` 类类似于 [concurrency:: unbounded_buffer](../Topic/unbounded_buffer%20Class.md) 类，因为它包含一列消息，以及由于它充当源和目标消息块并可以具有多个源和多个目标。 但是， `unbounded_buffer` 消息仅在从其源接收消息的顺序上传播。  
  
  `priority_buffer` 类接收的消息类型的 std::[元组](../../standard-library/tuple-class.md) 包含 `PriorityType` 和 `Type` 元素。 `PriorityType` 引用类型，它保留每条消息; 的优先级 `Type` 指的是消息的数据部分。  `priority_buffer` 类发送类型的消息 `Type`。  `priority_buffer` 类还可以管理两个消息队列︰ [std::priority_queue](../../standard-library/priority-queue-class.md) 为传入消息的对象和 std::[队列](../../standard-library/queue-class.md) 为传出消息的对象。 按优先级顺序消息非常有用 `priority_buffer` 对象同时收到多条消息，或当它收到多条消息之前由使用者读取任何消息。  
  
 除了七种方法，一个类，派生自 `propagator_block` 必须实现 `priority_buffer` 类也将重写 `link_target_notification` 和 `send_message` 方法。  `priority_buffer` 类还定义了两个公共 helper 方法， `enqueue` 和 `dequeue`, ，和一个私有帮助器方法， `propagate_priority_order`。  
  
 下面的过程描述如何实现 `priority_buffer` 类。  
  
#### <a name="to-define-the-prioritybuffer-class"></a>若要定义 priority_buffer 类  
  
1.  创建 c + + 头文件并将其命名 `priority_buffer.h`。 或者，您可以使用现有的头文件，是您项目的一部分。  
  
2.  在 `priority_buffer.h`, ，添加以下代码。  
  
 [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_2.h)]  
  
3.  在 `std` 命名空间中，定义的专用化 [std:: less](../../standard-library/less-struct.md) 和 [std:: greater](../../standard-library/greater-struct.md) ，作用于并发::[消息](../../parallel/concrt/reference/message-class.md) 对象。  
  
 [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_3.h)]  
  
      `priority_buffer` 类存储 `message` 中的对象 `priority_queue` 对象。 这些类型专用化允许优先级队列以对邮件根据它们的优先级别进行排序。 优先级是第一个元素的 `tuple` 对象。  
  
4.  在 `concurrencyex` 命名空间中，声明 `priority_buffer` 类。  
  
 [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_4.h)]  
  
     `priority_buffer` 类派生自 `propagator_block`。 因此，它可以同时发送和接收消息。  `priority_buffer` 类可以具有多个接收类型的消息的目标 `Type`。 它还可以具有多个发送类型的消息的源 `tuple<PriorityType, Type>`。  
  
5.  在 `private` 部分 `priority_buffer` 类中，添加以下成员变量。  
  
 [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_5.h)]  
  
      `priority_queue` 对象保留传入的消息; `queue` 对象保留传出消息。 一个 `priority_buffer` 对象可以同时收到多条消息; `critical_section` 对象同步到输入消息的队列的访问。  
  
6.  在 `private` 部分，定义的复制构造函数和赋值运算符。 这样可以防止 `priority_queue` 对象赋值。  
  
 [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_6.h)]  
  
7.  在 `public` 部分，定义的构造函数所共有的许多消息块类型。 此外定义析构函数。  
  
 [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_7.h)]  
  
8.  在 `public` 部分中，定义的方法 `enqueue` 和 `dequeue`。 这些帮助器方法提供了一种备选方法将消息发送到和接收邮件的 `priority_buffer` 对象。  
  
 [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_8.h)]  
  
9. 在 `protected` 部分，定义 `propagate_to_any_targets` 方法。  
  
 [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_9.h)]  
  
      `propagate_to_any_targets` 方法会将传输位于输入输出队列到队列的前面，并传播输出队列中的所有消息的消息。  
  
10. 在 `protected` 部分，定义 `accept_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_10.h)]  
  
     当目标块通过调用 `accept_message` 方法， `priority_buffer` 类将消息的所有权转移给接受它的第一个目标块。 (这类似于的行为 `unbounded_buffer`。)  
  
11. 在 `protected` 部分，定义 `reserve_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_11.h)]  
  
      `priority_buffer` 类允许目标块提供的消息标识符匹配的消息位于队列开头的标识符时保留消息。 换而言之，则目标可以保留该消息，如果 `priority_buffer` 对象尚未收到更多的消息，并且当前尚未不传播。  
  
12. 在 `protected` 部分，定义 `consume_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_12.h)]  
  
     目标块调用 `consume_message` 来传输它保留消息的所有权。  
  
13. 在 `protected` 部分，定义 `release_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_13.h)]  
  
     目标块调用 `release_message` 若要取消其预留到一条消息。  
  
14. 在 `protected` 部分，定义 `resume_propagation` 方法。  
  
 [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_14.h)]  
  
     运行时调用 `resume_propagation` 目标块使用或释放保留的消息之后。 此方法会将传播出去输出队列中的任何消息。  
  
15. 在 `protected` 部分，定义 `link_target_notification` 方法。  
  
 [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_15.h)]  
  
      `_M_pReservedFor` 成员变量定义由基类， `source_block`。 此成员变量指向目标块后，如果有存放到在前面的输出队列的消息保留。 运行时调用 `link_target_notification` 当新的目标已链接到 `priority_buffer` 对象。 此方法会将传播出去处于输出队列中，如果没有目标存放保留任何消息。  
  
16. 在 `private` 部分，定义 `propagate_priority_order` 方法。  
  
 [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_16.h)]  
  
     此方法会将传播出去输出队列中的所有消息。 直到其中一个目标块接受消息，队列中的每个消息提供给每个目标块。  `priority_buffer` 类保留传出消息的顺序。 因此，输出队列中的第一个消息必须接受由目标块之前此方法提供向目标块的任何其他消息。  
  
17. 在 `protected` 部分，定义 `propagate_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_17.h)]  
  
      `propagate_message` 方法可以使 `priority_buffer` 类充当消息接收方，或确定目标。 此方法接收的消息，提供由提供的源块并将该消息插入到优先级队列。  `propagate_message` 方法然后以异步方式发送所有消息输出到目标块。  
  
     运行时调用此方法，当您调用 [concurrency:: asend](../Topic/asend%20Function.md) 函数或消息块连接至其他消息块。  
  
18. 在 `protected` 部分，定义 `send_message` 方法。  
  
 [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_18.h)]  
  
      `send_message` 方法类似于 `propagate_message`。 但是，它将发送同步而不是以异步方式将输出消息。  
  
     运行时调用此方法在同步发送操作中，例如当您调用 [concurrency:: send](../Topic/send%20Function.md) 函数。  
  
  `priority_buffer` 类包含很平常的许多消息块类型的构造函数重载。 某些构造函数重载可获取 [concurrency:: scheduler](../../parallel/concrt/reference/scheduler-class.md) 或 [concurrency:: schedulegroup](../../parallel/concrt/reference/schedulegroup-class.md) 允许消息块由特定任务计划程序管理的对象。 其他构造函数重载采用一个筛选器函数。 筛选器函数使消息块来接受或拒绝其负载根据一条消息。 有关消息筛选器的详细信息，请参阅 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。 有关任务计划程序的详细信息，请参阅 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)。  
  
 因为 `priority_buffer` 类按优先级排序消息，然后按照接收消息的顺序，此类最时很有用异步接收消息，例如，当您调用 [concurrency:: asend](../Topic/asend%20Function.md) 函数或消息块连接至其他消息块。  
  
 [[返回页首](#top)]  
  
##  <a name="a-namecompletea-the-complete-example"></a><a name="complete"></a> 完整示例  
 下面的示例演示的完整定义 `priority_buffer` 类。  
  
 [!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_19.h)]  
  
 下面的示例将同时执行若干个 `asend` 和 [concurrency:: receive](../Topic/receive%20Function.md) 操作 `priority_buffer` 对象。  
  
 [!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-a-custom-message-block_20.cpp)]  
  
 该示例产生下面的示例输出。  
  
```Output  
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36  
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24  
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12  
```  
  
  `priority_buffer` 类订单消息先按优先级别，然后按顺序接收消息的顺序。 在此示例中，具有更大的数值优先级的消息插入队列前面的朝向。  
  
 [[返回页首](#top)]  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴的定义 `priority_buffer` 类中的文件，名为 `priority_buffer.h` 和名为的文件中的测试程序 `priority_buffer.cpp` ，然后在 Visual Studio 命令提示窗口中运行以下命令。  
  
 **cl.exe /EHsc priority_buffer.cpp**  
  
## <a name="see-also"></a>另请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)
