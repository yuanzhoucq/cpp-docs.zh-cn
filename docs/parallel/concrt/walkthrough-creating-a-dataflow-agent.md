---
title: "演练： 创建数据流代理 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- creating dataflow agents [Concurrency Runtime]
- dataflow agents, creating [Concurrency Runtime]
ms.assetid: 9db5ce3f-c51b-4de1-b79b-9ac2a0cbd130
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b94fb68ad28e45141551b238acf99baedf78ef6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-creating-a-dataflow-agent"></a>演练：创建数据流代理
本文档演示如何创建基于代理的应用程序基于数据流，而不是控制流。  
  
 *控制流*指的是在程序中的操作的执行顺序。 控制流是通过使用如条件语句、 循环和等等的控制结构调整的。 或者，*数据流*指在其中进行计算的所有所需的数据时才可用的编程模型。 数据流编程模型都与在其中程序的独立组件相互通信，将消息发送的消息传递的概念。  
  
 异步代理支持的控制流和数据流编程模型。 尽管控制流模型适合在许多情况下，数据流模型适合其他情况下，例如，在代理接收数据，并执行一个基于该数据的负载的操作时。  
  
## <a name="prerequisites"></a>先决条件  
 在开始本演练之前，请阅读以下文档：  
  
- [异步代理](../../parallel/concrt/asynchronous-agents.md)  
  
- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [如何：使用消息块筛选器](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
##  <a name="top"></a> 部分  
 本演练包含以下各节：  
  
- [创建基本的控制流代理](#control-flow)  
  
- [创建基本数据流代理](#dataflow)  
  
- [创建消息日志记录代理](#logging)  
  
##  <a name="control-flow"></a>创建基本的控制流代理  
 考虑下面的示例定义`control_flow_agent`类。 `control_flow_agent`类将对三个消息缓冲区进行操作： 一个输入缓冲区和两个输出缓冲区。 `run`方法在循环中的源消息缓冲区中读取，并使用条件语句来直接控制程序执行流程。 代理递增一个计数器为非零，负数的值，并递增另一个计数器为非零的正值。 代理收到 sentinel 值为零后，它会将计数器的值发送到输出消息缓冲区中。 `negatives`和`positives`方法启用应用程序代理从读取正负值的计数。  
  
 [!code-cpp[concrt-dataflow-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_1.cpp)]  
  
 尽管本示例将代理中的控制流的基本用法，它演示了控件基于流的编程的串行特性。 即使多个消息中可能会提供的输入的消息缓冲区，必须按顺序处理每条消息。 数据流模型使条件语句的评估结果并发的两个分支。 数据流模型还可以创建更复杂的消息传送网络中对数据进行操作变得可用。  
  
 [[返回页首](#top)]  
  
##  <a name="dataflow"></a>创建基本数据流代理  
 本部分演示如何将转换`control_flow_agent`类以使用数据流模型执行相同任务。  
  
 数据流代理的工作方式创建的消息缓冲区，其中每个都有特定用途的网络。 某些消息块使用筛选器函数接受或拒绝基于及其负载的消息。 筛选器函数可确保消息块收到仅将特定值。  
  
#### <a name="to-convert-the-control-flow-agent-to-a-dataflow-agent"></a>若要控制流代理转换数据流代理  
  
1.  将复制的正文`control_flow_agent`到另一个类，例如，类`dataflow_agent`。 或者，你可以重命名`control_flow_agent`类。  
  
2.  删除调用的循环正文`receive`从`run`方法。  
  
 [!code-cpp[concrt-dataflow-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_2.cpp)]  
  
3.  在`run`方法，这些变量的初始化之后`negative_count`和`positive_count`，添加`countdown_event`跟踪的活动操作计数的对象。  
  
 [!code-cpp[concrt-dataflow-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_3.cpp)]  
  
     `countdown_event`类在本主题后面所示。  
  
4.  创建数据流网络的消息将加入的缓冲区对象。  
  
 [!code-cpp[concrt-dataflow-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_4.cpp)]  
  
5.  连接的消息缓冲区，以形成网络。  
  
 [!code-cpp[concrt-dataflow-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_5.cpp)]  
  
6.  等待`event`和`countdown event`要设置的对象。 这些事件发出信号，代理已收到 sentinel 值以及所有操作的完成都时间。  
  
 [!code-cpp[concrt-dataflow-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_6.cpp)]  
  
 下图显示的完整数据流网络`dataflow_agent`类：  
  
 ![数据流网络](../../parallel/concrt/media/concrt_dataflow.png "concrt_dataflow")  
  
 下表描述了网络的成员。  
  
|成员|描述|  
|------------|-----------------|  
|`increment_active`|A [concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)递增 active 事件计数器并将输入的值传递到其他网络的对象。|  
|`negatives`, `positives`|[concurrency:: call](../../parallel/concrt/reference/call-class.md)递增的数字和递减计数活动事件计数器的对象。 每个对象使用筛选器接受负数或正数。|  
|`sentinel`|A [concurrency:: call](../../parallel/concrt/reference/call-class.md)接受 active 事件计数器的仅零和递减的 sentinel 值的对象。|  
|`connector`|A [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)连接到内部网络的源消息缓冲区的对象。|  
  
 因为`run`的单独线程上调用方法时之前的网络完全连接, 其他线程可以将消息发送到网络。 `_source`数据成员是`unbounded_buffer`缓冲从代理到应用程序发送的所有输入的对象。 若要确保网络处理所有输入的消息，代理首先要链接的网络的内部节点，然后将这些链接的该网络时，开始`connector`到`_source`数据成员。 这可保证，如正确网络执行不会处理消息。  
  
 因为此示例中的网络取决于数据流，而不是在控制流，网络必须通信到代理它已完成处理每个输入的值并 sentinel 节点已接收其值。 此示例使用`countdown_event`对象发出信号处理完所有输入的值和[concurrency:: event](../../parallel/concrt/reference/event-class.md)对象，以指示 sentinel 节点已收到其值。 `countdown_event`类使用`event`当计数器值达到零时发送信号的对象。 每次它接收的值时，数据流网络的开头递增的计数器。 网络递减的每个终端节点处理的输入的值后的计数器。 代理形成数据流网络后，等待 sentinel 节点设置`event`对象和`countdown_event`对象以表示其计数器已归零。  
  
 下面的示例演示`control_flow_agent`， `dataflow_agent`，和`countdown_event`类。 `wmain`函数创建`control_flow_agent`和`dataflow_agent`对象，并使用`send_values`函数以向代理发送的一系列随机值。  
  
 [!code-cpp[concrt-dataflow-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_7.cpp)]  
  
 该示例产生下面的示例输出：  
  
```Output  
Control-flow agent:  
There are 500523 negative numbers.  
There are 499477 positive numbers.  
Dataflow agent:  
There are 500523 negative numbers.  
There are 499477 positive numbers.  
```  
  
### <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`dataflow-agent.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 数据流 agent.cpp**  
  
 [[返回页首](#top)]  
  
##  <a name="logging"></a>创建消息日志记录代理  
 下面的示例演示`log_agent`类，类似于`dataflow_agent`类。 `log_agent`类实现异步日志记录代理将日志消息写入到文件然后到控制台。 `log_agent`类使应用程序将分类为信息性消息、 警告或错误。 它还使应用程序指定是否每个日志类别写入到文件和 / 或控制台中。 此示例将所有日志消息写入文件和仅错误消息写入控制台。  
  
 [!code-cpp[concrt-log-filter#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-dataflow-agent_8.cpp)]  
  
 此示例将下面的输出写入控制台。  
  
```Output  
error: This is a sample error message.  
```  
  
 此示例还将生成 log.txt 文件，其中包含以下文本。  
  
```Output  
info: ===Logging started.=== 
warning: This is a sample warning message.  
error: This is a sample error message.  
info: ===Logging finished.=== 
```  
  
### <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`log-filter.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc log-filter.cpp**  
  
 [[返回页首](#top)]  
  
## <a name="see-also"></a>另请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

