---
title: 演练： 使用 join 避免死锁 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5deb501cc05c2a771b6e14d5091b1baa95f2f622
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693331"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>演练：使用 join 避免死锁
本主题使用通过哲学家就餐问题说明如何使用[concurrency:: join](../../parallel/concrt/reference/join-class.md)类以防止你的应用程序中发生死锁。 在软件应用中，如果两个或多个进程分别留有资源，且相互等待另一进程释放其他资源，就会发生死锁。  
  
 通过哲学家就餐问题是常规的一组在多个并发进程之间共享一组资源时可能发生的问题的特定示例。  
  
## <a name="prerequisites"></a>系统必备  
 在开始本演练之前，请阅读以下主题：  
  
- [异步代理](../../parallel/concrt/asynchronous-agents.md)  
  
- [演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
  
- [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
  
- [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> 部分  
 本演练包含以下各节：  
  
- [通过哲学家就餐问题](#problem)  
  
- [Naïve 实现](#deadlock)  
  
- [使用 join 避免死锁](#solution)  
  
##  <a name="problem"></a> 通过哲学家就餐问题  
 通过哲学家就餐问题说明了如何在应用程序中发生死锁。 此问题，请在五个哲学家坐在轮表。 每个哲学家思想和饮食之间交替。 每个哲学家必须与左侧，另一个邻居共享筷子筷子与右侧邻居。 下图显示此布局。  
  
 ![用餐哲学家就餐问题](../../parallel/concrt/media/dining_philosophersproblem.png "dining_philosophersproblem")  
  
 为了就餐，哲学家必须包含两个筷子。 如果每个哲学家保持一个筷子，并等待另一个，然后没有一个哲学家可以吞噬你和所有枯竭。  
  
 [[返回页首](#top)]  
  
##  <a name="deadlock"></a> Naïve 实现  
 下面的示例演示通过哲学家就餐问题的简单实现。 `philosopher`类，该类派生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)，使每个哲学家可以单独操作。 该示例使用的共享的数组[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)对象，让每个`philosopher`对象对一对筷子的独占访问权。  
  
 要关联到图中，实现`philosopher`类表示一个哲学家。 `int`变量表示每个筷子。 `critical_section`对象作为放置在其停留筷子的持有者。 `run`方法模拟哲学家的生命周期。 `think`方法模拟思考操作和`eat`方法模拟就餐操作。  
  
 A`philosopher`对象锁定全部两个`critical_section`对象以模拟从之前它是持有人筷子删除调用`eat`方法。 在调用后`eat`、`philosopher`对象返回到是持有人通过设置的筷子`critical_section`对象回解除锁定状态。  
  
 `pickup_chopsticks`方法演示了可能出现死锁。 如果每个`philosopher`对象可以访问一个锁，则没有`philosopher`对象可以继续，因为其他锁由另一个控制`philosopher`对象。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
  
### <a name="code"></a>代码  
 [!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`philosophers-deadlock.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc philosophers-deadlock.cpp**  
  
 [[返回页首](#top)]  
  
##  <a name="solution"></a> 使用 join 避免死锁  
 本部分演示如何使用消息缓冲区和消息传递函数来消除出现死锁的机会。  
  
 要关联到更早版本的一个，此示例`philosopher`类替换每个`critical_section`对象使用[concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md)对象和一个`join`对象。 `join`对象用作到哲学家提供筷子的仲裁。  
  
 此示例使用`unbounded_buffer`类，因为在目标收到来自消息`unbounded_buffer`对象，从消息队列中删除消息。 这使`unbounded_buffer`包含一条消息，则指示筷子的对象都不可用。 `unbounded_buffer`不包含消息的对象表示筷子正在使用。  
  
 此示例使用非贪婪`join`对象，因为非贪婪联接用于为每`philosopher`对象对这两个筷子的访问仅当同时`unbounded_buffer`对象包含一条消息。 因为贪婪联接接受的消息变得可用时，就会立即，贪婪联接将不会阻止死锁。 如果所有贪婪，则会发生死锁`join`对象收到一条消息，但永远等待另一个变得可用。  
  
 有关贪婪和非贪婪联接，以及各种消息缓冲区类型之间的差异的详细信息，请参阅[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
#### <a name="to-prevent-deadlock-in-this-example"></a>若要防止在此示例中的死锁  
  
1.  删除以下代码示例中。  
  
 [!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]  
  
2.  更改的类型`_left`和`_right`的数据成员`philosopher`类到`unbounded_buffer`。  
  
 [!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]  
  
3.  修改`philosopher`构造函数以使用`unbounded_buffer`作为其参数的对象。  
  
 [!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]  
  
4.  修改`pickup_chopsticks`要使用非贪婪方法`join`对象从这两个筷子的消息缓冲区接收消息。  
  
 [!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]  
  
5.  修改`putdown_chopsticks`方法来通过将一条消息发送到这两个筷子的消息缓冲区释放对筷子的访问。  
  
 [!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]  
  
6.  修改`run`方法保存的结果`pickup_chopsticks`方法并传递到这些结果`putdown_chopsticks`方法。  
  
 [!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]  
  
7.  修改的声明`chopsticks`变量中`wmain`函数为非数组的`unbounded_buffer`每个保存一条消息的对象。  
  
 [!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面显示的已完成的示例中使用非贪婪`join`对象，若要消除的死锁风险。  
  
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
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`philosophers-join.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc philosophers-join.cpp**  
  
 [[返回页首](#top)]  
  
## <a name="see-also"></a>请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)
