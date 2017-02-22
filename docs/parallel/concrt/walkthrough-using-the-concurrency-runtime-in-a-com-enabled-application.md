---
title: "演练：在启用 COM 的应用程序中使用并发运行时 | Microsoft Docs"
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
  - "并发运行时, 与 COM 一起使用"
  - "COM, 与并发运行时一起使用"
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 演练：在启用 COM 的应用程序中使用并发运行时
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档演示如何在使用组件对象模型 \(COM\) 的应用程序中使用并发运行时。  
  
## 系统必备  
 在开始本演练之前，请阅读下列文档：  
  
-   [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [并行算法](../../parallel/concrt/parallel-algorithms.md)  
  
-   [异步代理](../../parallel/concrt/asynchronous-agents.md)  
  
-   [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)  
  
 有关 COM 的更多信息，请参见[组件对象模型 \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms680573)。  
  
## 管理 COM 库的生存期  
 尽管结合使用 COM 和并行运行时遵循与其他任何并发机制相同的准则，但以下准则可帮助您有效地一起使用这些库。  
  
-   线程必须先调用 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) 然后才能使用 COM 库。  
  
-   线程可以多次调用 `CoInitializeEx`，只要它每次调用都提供相同的参数。  
  
-   每当调用 `CoInitializeEx` 时，线程还必须调用 [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715)。  也就是说，`CoInitializeEx` 和 `CoUninitialize` 的调用必须平衡。  
  
-   若要从一个线程单元切换到另一个线程单元，线程必须先完全释放 COM 库，然后再通过新的线程处理规范调用 `CoInitializeEx`。  
  
 在将 COM 与并发运行时结合使用时，适用其他 COM 原则。  例如，在单线程单元 \(STA\) 中创建对象并将此对象封送到另一个单元的应用程序还必须提供用于处理传入消息的消息循环。  还请记住，在单元之间封送对象会降低性能。  
  
### 结合使用 COM 和并行模式库  
 将 COM 与并行模式库 \(PPL\) 中的某个组件（如任务组或并行算法）一起使用时，请先调用 `CoInitializeEx`，再在每个任务或迭代的执行期间使用 COM 库，接着调用 `CoUninitialize`，然后完成每个任务或迭代。  以下示例演示如何使用 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 对象管理 COM 库的生存期。  
  
 [!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]  
  
 必须确保在取消任务或并行算法时或任务正文引发异常时正确释放 COM 库。  为了保证任务在退出之前调用 `CoUninitialize`，请使用 `try-finally` 块或“获取资源即初始化”\(RAII\) 模式。  以下示例使用 `try-finally` 块在任务完成或取消时或引发异常时释放 COM 库。  
  
 [!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]  
  
 以下示例使用 RAII 模式定义 `CCoInitializer` 类，该类管理 COM 库在给定范围内的生存期。  
  
 [!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]  
  
 使用 `CCoInitializer` 类可在任务退出时自动释放 COM 库，如下所示。  
  
 [!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]  
  
 有关并发运行时中的取消操作的更多信息，请参见 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
### 结合使用 COM 和异步代理  
 将 COM 与异步代理结合使用时，请先调用 `CoInitializeEx`，然后在代理的 [concurrency::agent::run](../Topic/agent::run%20Method.md) 方法中使用 COM 库。  然后，在 `run` 方法返回之前调用 `CoUninitialize`。  不要在代理的构造函数或析构函数中使用 COM 管理例程，也不要重写 [concurrency::agent::start](../Topic/agent::start%20Method.md) 或 [concurrency::agent::done](../Topic/agent::done%20Method.md) 方法，因为这些方法是从与 `run` 方法不同的线程调用的。  
  
 以下示例演示了一个名为 `CCoAgent` 的基本代理类，该类使用 `run` 方法管理 COM 库。  
  
 [!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]  
  
 本演练稍后将提供一个完整示例。  
  
### 结合使用 COM 和轻量级任务  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)文档介绍并发运行时中的轻量级任务的角色。  就像对传递到 Windows API 中的 `CreateThread` 函数的线程例程所做的那样，可以将 COM 与轻量级任务一起使用。  这将在下面的示例中显示。  
  
 [!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]  
  
## 启用 COM 的应用程序的示例  
 本节将演示一个完整的启用 COM 的应用程序，该应用程序使用 `IScriptControl` 接口执行计算第 N 个斐波纳契数的脚本。  此示例首先从主线程调用此脚本，再使用 PPL 和代理同时调用此脚本。  
  
 请考虑 helper 函数 `RunScriptProcedure`，该函数可调用 `IScriptControl` 对象中的过程。  
  
 [!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]  
  
 `wmain` 函数将创建一个 `IScriptControl` 对象，再向该对象添加计算第 N 个斐波纳契数的脚本代码，然后调用 `RunScriptProcedure` 函数来运行此脚本。  
  
 [!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]  
  
### 从 PPL 中调用脚本  
 下面的`ParallelFibonacci` 函数使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法以并行方式调用此脚本。  在任务的每次迭代期间，此函数使用 `CCoInitializer` 类来管理 COM 库的生存期。  
  
 [!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]  
  
 若要在此示例中使用 `ParallelFibonacci` 函数，请在 `wmain` 函数返回之前添加以下代码。  
  
 [!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]  
  
### 从代理调用脚本  
 以下示例演示调用脚本过程来计算第 N 个斐波纳契数的 `FibonacciScriptAgent` 类。  `FibonacciScriptAgent` 类使用消息传递功能，从主程序接收此脚本函数的输入值。  `run` 方法管理 COM 库在整个任务中的生存期。  
  
 [!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]  
  
 函数 `AgentFibonacci` 创建若干个 `FibonacciScriptAgent` 对象，并使用消息传递功能向这些对象发送若干个输入值。  
  
 [!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]  
  
 若要在此示例中使用 `AgentFibonacci` 函数，请在 `wmain` 函数返回之前添加以下代码。  
  
 [!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]  
  
### 完整示例  
 下面的代码演示完整示例，该示例使用并行算法和异步代理调用计算斐波那契数列的脚本过程。  
  
 [!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]  
  
 此示例产生下面的示例输出。  
  
  **主线程**  
**fib\(15\) \= 610**  
**并行斐波纳契数：**  
**fib\(15\) \= 610**  
**fib\(10\) \= 55**  
**fib\(16\) \= 987**  
**fib\(18\) \= 2584**  
**fib\(11\) \= 89**  
**fib\(17\) \= 1597**  
**fib\(19\) \= 4181**  
**fib\(12\) \= 144**  
**fib\(13\) \= 233**  
**fib\(14\) \= 377**  
**代理斐波纳契数：**  
**fib\(30\) \= 832040**  
**fib\(22\) \= 17711**  
**fib\(10\) \= 55**  
**fib\(12\) \= 144**   
## 编译代码  
 复制代码示例，将其粘贴到Visual Studio 项目中或名为 `parallel-scripts.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc parallel\-scripts.cpp \/link ole32.lib**  
  
## 请参阅  
 [并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [异步代理](../../parallel/concrt/asynchronous-agents.md)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)