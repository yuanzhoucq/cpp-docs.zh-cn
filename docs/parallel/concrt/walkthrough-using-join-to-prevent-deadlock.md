---
title: "演练：使用 join 避免死锁 | Microsoft Docs"
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
  - "使用联接阻止死锁 [并发运行时]"
  - "死锁，阻止 [并发运行时]"
  - "非贪婪联接，示例"
  - "join 类，示例"
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 演练：使用 join 避免死锁
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题通过哲学家就餐问题说明如何使用 [concurrency::join](../../parallel/concrt/reference/join-class.md) 类来避免应用程序中发生死锁。  在软件应用程序中，在两个或更多进程中的每个进程都占用一个资源，并相互等待另一个进程释放一些其他资源时，会发生死锁。  
  
 哲学家就餐问题是在多个并发进程之间共享资源集时可能出现的一组常规问题的具体示例。  
  
## 系统必备  
 在开始本演练之前，请阅读下列主题：  
  
-   [异步代理](../../parallel/concrt/asynchronous-agents.md)  
  
-   [演练：创建基于代理的应用程序](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
  
-   [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [消息传递函数](../../parallel/concrt/message-passing-functions.md)  
  
-   [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> 各节内容  
 本演练包含以下各节：  
  
-   [哲学家就餐问题](#problem)  
  
-   [低级实现](#deadlock)  
  
-   [使用联接避免死锁](#solution)  
  
##  <a name="problem"></a> 哲学家就餐问题  
 哲学家就餐问题说明了在应用程序中如何发生死锁。  在这个问题中，五个哲学家坐在圆桌旁。  每个哲学家一边思考一边就餐。  每个哲学家必须与左侧邻居共享一根筷子，与右侧邻居共享另一根筷子。  下图显示了这一布局。  
  
 ![哲学家就餐问题](../../parallel/concrt/media/dining_philosophersproblem.png "Dining\_PhilosophersProblem")  
  
 为了就餐，哲学家必须拿起两根筷子。  如果每个哲学家都只拿起一根筷子而等待另一根筷子，则没有一个哲学家可以吃到食物，所有人都饿着。  
  
 \[[Top](#top)\]  
  
##  <a name="deadlock"></a> 低级实现  
 下面的示例演示哲学家就餐问题的低级实现。  从 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 派生的 `philosopher` 类使每个哲学家可以单独操作。  该示例使用 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 对象的共享数组为每个 `philosopher` 对象授予对一对筷子的独占访问权。  
  
 为了将该实现与图示相关联，`philosopher` 类表示一个哲学家。  `int` 变量表示每根筷子。  `critical_section` 对象作为放置筷子的托架。  `run` 方法模拟哲学家的生命周期。  `think` 方法模拟思考操作，`eat` 方法模拟就餐操作。  
  
 `philosopher` 对象在调用 `eat` 方法之前，锁定全部两个 `critical_section` 对象，以模拟从托架上取走筷子的操作。  调用 `eat` 后，`philosopher` 对象通过将 `critical_section` 对象设置回未锁定状态，将筷子放回到托架。  
  
 `pickup_chopsticks` 方法说明了可能发生死锁的位置。  如果每个 `philosopher` 对象获得了一个锁的访问权，则没有 `philosopher` 对象可以继续，因为另一个锁由另一个 `philosopher` 对象控制。  
  
## 示例  
  
### 说明  
  
### 代码  
 [!CODE [concrt-philosophers-deadlock#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-deadlock#1)]  
  
## 编译代码  
 复制代码示例，再将此代码粘贴到 Visual Studio 项目中或一个名为 `philosophers-deadlock.cpp` 的文件中，然后在 Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc philosophers\-deadlock.cpp**  
  
 \[[Top](#top)\]  
  
##  <a name="solution"></a> 使用联接避免死锁  
 本节说明如何使用消息缓冲区和消息传递函数来消除出现死锁的机会。  
  
 为了将该示例与上一示例相关联，`philosopher` 类通过使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 对象和 `join` 对象来替换每个 `critical_section` 对象。  `join` 对象作为向哲学家提供筷子的仲裁者。  
  
 该示例使用 `unbounded_buffer` 类，这是因为在目标收到来自 `unbounded_buffer` 对象的消息后，将从消息队列中移除此消息。  这样，包含消息的 `unbounded_buffer` 对象表示筷子可用。  不包含消息的 `unbounded_buffer` 对象则表示筷子正在使用中。  
  
 该示例使用非贪婪 `join` 对象，这是因为只有当两个 `unbounded_buffer` 对象都包含消息时，非贪婪联接才为每个 `philosopher` 对象授予全部两根筷子的访问权。  因为只要消息可用，贪婪联接就会接受消息，所以贪婪联接无法避免死锁。  如果所有贪婪 `join` 对象收到其中一条消息，但是永远等待另一条变为可用，则会发生死锁。  
  
 有关贪婪和非贪婪联接的更多信息，以及各种消息缓冲区类型之间的差异，请参见[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
#### 在此示例中避免死锁  
  
1.  从示例中移除以下代码。  
  
     [!CODE [concrt-philosophers-deadlock#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-deadlock#2)]  
  
2.  将 `philosopher` 类的 `_left` 和 `_right` 数据成员的类型更改为 `unbounded_buffer`。  
  
     [!CODE [concrt-philosophers-join#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-join#2)]  
  
3.  修改 `philosopher` 构造函数，以采用 `unbounded_buffer` 对象作为其参数。  
  
     [!CODE [concrt-philosophers-join#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-join#3)]  
  
4.  修改 `pickup_chopsticks` 方法，以使用非贪婪 `join` 对象从全部两根筷子的消息缓冲区接收消息。  
  
     [!CODE [concrt-philosophers-join#4](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-join#4)]  
  
5.  修改 `putdown_chopsticks` 方法，以通过将消息发送到全部两根筷子的消息缓冲区来释放对筷子的访问权。  
  
     [!CODE [concrt-philosophers-join#5](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-join#5)]  
  
6.  修改 `run` 方法，以保存 `pickup_chopsticks` 方法的结果，并将这些结果传递给 `putdown_chopsticks` 方法。  
  
     [!CODE [concrt-philosophers-join#6](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-join#6)]  
  
7.  将 `wmain` 函数中 `chopsticks` 变量的声明修改为 `unbounded_buffer` 对象的数组，其中每个对象保存一条消息。  
  
     [!CODE [concrt-philosophers-join#7](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-join#7)]  
  
## 示例  
  
### 说明  
 下面显示了使用非贪婪 `join` 对象消除死锁风险的已完成示例。  
  
### 代码  
 [!CODE [concrt-philosophers-join#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-philosophers-join#1)]  
  
### 注释  
 该示例产生下面的输出。  
  
  **亚里斯多德吃了 50 次。**  
**笛卡儿吃了 50 次。**  
**hobbes 吃了 50 次。**  
**socrates 吃了 50 次。**  
**柏拉图吃了 50 次。**   
## 编译代码  
 复制代码示例，再将此代码粘贴到 Visual Studio项目中或一个名为`philosophers-join.cpp` 的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc philosophers\-join.cpp**  
  
 \[[Top](#top)\]  
  
## 请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [消息传递函数](../../parallel/concrt/message-passing-functions.md)   
 [同步数据结构](../../parallel/concrt/synchronization-data-structures.md)