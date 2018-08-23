---
title: 演练： 在启用 COM 的应用程序中使用并发运行时 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd9f665f77ca5ae5311b034ee7afef6241ac489
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692543"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>演练：在启用 COM 的应用程序中使用并发运行时
本文档演示如何在使用组件对象模型 (COM) 的应用程序中使用并发运行时。  
  
## <a name="prerequisites"></a>系统必备  
 在开始本演练之前，请阅读以下文档：  
  
- [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
- [并行算法](../../parallel/concrt/parallel-algorithms.md)  
  
- [异步代理](../../parallel/concrt/asynchronous-agents.md)  
  
- [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)  
  
 有关 COM 的详细信息，请参阅[组件对象模型 (COM)](http://msdn.microsoft.com/library/windows/desktop/ms680573)。  
  
## <a name="managing-the-lifetime-of-the-com-library"></a>COM 库的生存期管理  
 尽管使用了 COM，与并发运行时遵循相同的原则作为任何其他并发机制，但以下准则可以帮助你有效地一起使用这些库。  
  
-   一个线程必须调用[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)它使用 COM 库之前。  
  
-   线程可以调用`CoInitializeEx`多次，只要它提供的每个调用的相同自变量。  
  
-   每次调用`CoInitializeEx`，还必须调用线程[CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715)。 换而言之，调用`CoInitializeEx`和`CoUninitialize`必须平衡。  
  
-   若要从一个线程单元切换到另一个，线程必须完全释放 COM 库之前它将调用`CoInitializeEx`与新的线程处理规范。  
  
 当与并发运行时使用 COM 时，其他 COM 原则适用。 例如，在单线程单元 (STA) 中创建对象并将该对象与另一单元封送的应用程序还必须提供一个消息循环来处理传入消息。 另请记住，封送处理单元之间的对象可能会降低性能。  
  
### <a name="using-com-with-the-parallel-patterns-library"></a>使用 COM 和并行模式库  
 当你使用 COM 组件在并行模式库 (PPL)，例如，任务组或并行算法时调用`CoInitializeEx`在每个任务或迭代，并调用过程中使用 COM 库之前`CoUninitialize`每个任务或迭代完成之前. 下面的示例演示如何管理与 COM 库的生存期[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象。  
  
 [!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]  
  
 你必须确保取消任务或并行算法时或在任务体引发异常时正确释放 COM 库。 若要保证任务将调用`CoUninitialize`退出之前，请使用`try-finally`块或*获取资源即初始化*(RAII) 模式。 下面的示例使用`try-finally`块来释放 COM 库，当任务完成或被取消，或当引发异常。  
  
 [!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]  
  
 下面的示例使用 RAII 模式，以定义`CCoInitializer`类，该类管理给定作用域中的 COM 库的生存期。  
  
 [!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]  
  
 你可以使用`CCoInitializer`类，如下所示在任务退出时自动释放 COM 库。  
  
 [!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]  
  
 有关并发运行时中的取消操作的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)。  
  
### <a name="using-com-with-asynchronous-agents"></a>使用 COM 和异步代理  

 当你使用 COM 时异步代理时，调用`CoInitializeEx`在使用中的 COM 库之前[concurrency::agent::run](reference/agent-class.md#run)你的代理的方法。 然后调用`CoUninitialize`之前`run`方法返回。 不会将 COM 管理例程中的构造函数或析构函数的你的代理，并且不会重写[concurrency::agent::start](reference/agent-class.md#start)或[concurrency:: agent:: 完成](reference/agent-class.md#done)方法因为这些方法从与不同的线程调用`run`方法。  

  
 下面的示例演示一个名为的基本的代理类`CCoAgent`，后者管理中的 COM 库`run`方法。  
  
 [!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]  
  
 稍后在本演练提供了一个完整的示例。  
  
### <a name="using-com-with-lightweight-tasks"></a>使用 COM 和轻量级任务  
 文档[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)介绍并发运行时中的轻量任务的角色。 你可以使用轻量级任务使用 COM，就像与传递给任何线程例程`CreateThread`Windows API 中的函数。 这在下面的示例中显示。  
  
 [!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]  
  
## <a name="an-example-of-a-com-enabled-application"></a>启用 COM 的应用程序示例  
 本部分说明的完整支持 COM 的应用程序使用`IScriptControl`接口用于执行脚本计算 n 斐波那<sup>th</sup>斐波那契数。 此示例先从主线程中，调用脚本，然后使用 PPL 和代理同时调用此脚本。  
  
 请考虑以下帮助器函数， `RunScriptProcedure`，其调用中的过程`IScriptControl`对象。  
  
 [!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]  
  
 `wmain`函数创建`IScriptControl`对象，请将脚本代码添加到计算 n 斐波那<sup>th</sup>斐波那契数，然后调用`RunScriptProcedure`要运行该脚本函数。  
  
 [!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]  
  
### <a name="calling-the-script-from-the-ppl"></a>从 PPL 调用脚本  

 为以下函数， `ParallelFibonacci`，使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法并行调用此脚本。 此函数使用`CCoInitializer`类来管理任务的每次迭代过程中的 COM 库的生存期。  

  
 [!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]  
  
 若要使用`ParallelFibonacci`函数的示例中，添加下面的代码之前`wmain`函数返回。  
  
 [!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]  
  
### <a name="calling-the-script-from-an-agent"></a>从代理调用脚本  
 下面的示例演示`FibonacciScriptAgent`类，该类将调用的脚本过程来计算 n<sup>th</sup>斐波那契数。 `FibonacciScriptAgent`类使用消息传递来从主程序，接收输入到脚本函数的值。 `run`方法管理在整个任务的 COM 库的生存期。  
  
 [!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]  
  
 为以下函数， `AgentFibonacci`，创建几个`FibonacciScriptAgent`对象，并使用消息传递来发送多个输入对这些对象的值。  
  
 [!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]  
  
 若要使用`AgentFibonacci`函数的示例中，添加下面的代码之前`wmain`函数返回。  
  
 [!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]  
  
### <a name="the-complete-example"></a>完整示例  
 下面的代码显示完整示例，其中使用并行算法和异步代理来调用计算 Fibonacci 数字的脚本过程。  
  
 [!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]  
  
 该示例产生下面的示例输出。  
  
```Output  
Main Thread:  
fib(15) = 610  
 
Parallel Fibonacci:  
fib(15) = 610  
fib(10) = 55  
fib(16) = 987  
fib(18) = 2584  
fib(11) = 89  
fib(17) = 1597  
fib(19) = 4181  
fib(12) = 144  
fib(13) = 233  
fib(14) = 377  
 
Agent Fibonacci:  
fib(30) = 832040  
fib(22) = 17711  
fib(10) = 55  
fib(12) = 144  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-scripts.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 并行 scripts.cpp /link ole32.lib**  
  
## <a name="see-also"></a>请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)

