---
title: 演练：使用 join 避免死锁
ms.date: 11/04/2016
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: b98c2deb158b9b9fc71caa7133aeaeb2acfd369c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498808"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>演练：使用 join 避免死锁

本主题使用哲学家就餐问题说明如何使用[concurrency:: join](../../parallel/concrt/reference/join-class.md)类，以避免在应用程序中的死锁。 在软件应用中，如果两个或多个进程分别留有资源，且相互等待另一进程释放其他资源，就会发生死锁。

哲学家就餐问题是在多个并发进程之间共享一组资源时可能发生的问题的常规集的具体示例。

## <a name="prerequisites"></a>系统必备

在开始本演练之前，请阅读以下主题：

- [异步代理](../../parallel/concrt/asynchronous-agents.md)

- [演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)

- [消息传递函数](../../parallel/concrt/message-passing-functions.md)

- [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> 部分

本演练包含以下各节：

- [哲学家就餐问题](#problem)

- [简单实现](#deadlock)

- [使用 join 避免死锁](#solution)

##  <a name="problem"></a> 哲学家就餐问题

哲学家就餐问题说明了如何在应用程序中发生死锁。 此问题，请在五个哲学家坐在圆桌。 每个哲学家思考并吃之间交替。 每个哲学家必须与邻居节点的左窗格和另一个共享筷子筷子与右侧相邻节点。 下图显示了此布局。

![哲学家就餐问题](../../parallel/concrt/media/dining_philosophersproblem.png "dining_philosophersproblem")

若要吃，哲学家必须保留两个筷子。 如果每个哲学家保存一个筷子并且正在等待另一个，然后无哲学家可能会消耗，所有影响。

[[返回页首](#top)]

##  <a name="deadlock"></a> 简单实现

下面的示例演示哲学家就餐问题的简单实现。 `philosopher`类，该类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)，使每个哲学家可以单独操作。 该示例使用的共享的数组[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)对象，让每个对象`philosopher`对象对一对筷子的独占访问权限。

若要与相关图所示，实现`philosopher`类表示一个哲学家。 `int`变量表示每个筷子。 `critical_section`对象用作持有者筷子的 rest。 `run`方法模拟的哲学家生命周期。 `think`方法模拟思考操作和`eat`方法模拟吃的操作。

一个`philosopher`对象锁定全部两个`critical_section`对象来模拟从之前它是持有人筷子删除调用`eat`方法。 在调用`eat`，则`philosopher`对象返回筷子持有者设置`critical_section`对象返回未锁定状态。

`pickup_chopsticks`方法说明了可能发生死锁。 如果每个`philosopher`对象获得其中一个锁，则不访问权`philosopher`对象可以继续，因为由另一个控制其他锁定`philosopher`对象。

## <a name="example"></a>示例

### <a name="description"></a>描述

### <a name="code"></a>代码

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`philosophers-deadlock.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc philosophers-deadlock.cpp**

[[返回页首](#top)]

##  <a name="solution"></a> 使用 join 避免死锁

本部分演示如何使用消息缓冲区和消息传递函数来消除死锁的可能性。

若要与此示例与上一，`philosopher`类替换每个`critical_section`通过使用对象[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象和一个`join`对象。 `join`对象用作到哲学家提供筷子的仲裁器。

此示例使用`unbounded_buffer`类，因为在目标收到来自消息`unbounded_buffer`对象，从消息队列删除消息。 这使`unbounded_buffer`包含一条消息，指示筷子的对象都不可用。 `unbounded_buffer`不包含消息的对象，表示正使用筷子。

此示例使用非贪婪`join`对象，因为非贪婪联接用于为每`philosopher`对象对这两个筷子的访问仅当同时`unbounded_buffer`对象包含一条消息。 贪婪联接变得可用时，就立即接受消息，因此，贪婪联接将不会阻止死锁。 如果所有贪婪，则会发生死锁`join`对象接收某条消息，但永远等待另一个变得可用。

有关贪婪和非贪婪联接和各种消息缓冲区类型之间的差异的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。

#### <a name="to-prevent-deadlock-in-this-example"></a>若要避免在此示例中的死锁

1. 删除以下代码示例中。

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. 更改的类型`_left`并`_right`的数据成员`philosopher`类来`unbounded_buffer`。

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. 修改`philosopher`构造函数以使用`unbounded_buffer`对象作为其参数。

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. 修改`pickup_chopsticks`方法以使用非贪婪`join`对象从这两个筷子的消息缓冲区接收消息。

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. 修改`putdown_chopsticks`方法，以通过将一条消息发送到这两个筷子的消息缓冲区释放对筷子的访问权限。

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. 修改`run`方法来保留的结果`pickup_chopsticks`方法，并将传递到这些结果`putdown_chopsticks`方法。

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. 修改的声明`chopsticks`变量中`wmain`函数的数组`unbounded_buffer`对象每个保存一条消息。

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

## <a name="example"></a>示例

### <a name="description"></a>描述

下面显示了已完成的示例使用非贪婪`join`对象以消除死锁风险。

### <a name="code"></a>代码

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

### <a name="comments"></a>注释

本示例生成以下输出。

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`philosophers-join.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc philosophers-join.cpp**

[[返回页首](#top)]

## <a name="see-also"></a>请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[消息传递函数](../../parallel/concrt/message-passing-functions.md)<br/>
[同步数据结构](../../parallel/concrt/synchronization-data-structures.md)
