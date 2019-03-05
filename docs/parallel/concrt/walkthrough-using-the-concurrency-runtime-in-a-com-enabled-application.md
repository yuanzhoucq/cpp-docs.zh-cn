---
title: 演练：在启用 COM 的应用程序中使用并发运行时
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: 9d306377be4a000c54fb5556b15263a15b2d4618
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278192"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>演练：在启用 COM 的应用程序中使用并发运行时

本文档演示如何在使用组件对象模型 (COM) 的应用程序中使用并发运行时。

## <a name="prerequisites"></a>系统必备

在开始本演练之前，请阅读以下文档：

- [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [并行算法](../../parallel/concrt/parallel-algorithms.md)

- [异步代理](../../parallel/concrt/asynchronous-agents.md)

- [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

有关 COM 的详细信息，请参阅[组件对象模型 (COM)](/windows/desktop/com/component-object-model--com--portal)。

## <a name="managing-the-lifetime-of-the-com-library"></a>管理 COM 库的生存期

虽然使用了 COM 与并发运行时遵循的相同原则作为任何其他并发机制，以下准则可以帮助您有效地结合使用这些库。

- 必须在调用线程[CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex)它使用 COM 库之前。

- 一个线程可以调用`CoInitializeEx`多次，只要它提供的每个调用的相同参数。

- 每次调用`CoInitializeEx`，还必须调用线程[CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize)。 换而言之，调用`CoInitializeEx`和`CoUninitialize`必须平衡。

- 若要从一个线程单元切换到另一个，线程必须完全释放 COM 库调用之前`CoInitializeEx`与新的线程处理规范。

并发运行时中使用 COM 时，将应用其他 COM 原则。 例如，在单线程单元 (STA) 中创建一个对象，并将该对象到另一个单元封送的应用程序还必须提供一个消息循环来处理传入的消息。 此外请记住，单元之间封送对象可能会降低性能。

### <a name="using-com-with-the-parallel-patterns-library"></a>使用 COM 和并行模式库

当您使用 COM 组件在并行模式库 (PPL)，例如，任务组或并行算法时调用`CoInitializeEx`在每个任务或迭代，并调用中使用 COM 库之前`CoUninitialize`每个任务或迭代完成之前. 下面的示例演示如何管理使用 COM 库的生存期[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象。

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

必须确保取消任务或并行算法时或任务正文引发异常时正确释放 COM 库。 若要保证任务调用`CoUninitialize`退出之前，请使用`try-finally`块或*获取资源即初始化*(RAII) 模式。 下面的示例使用`try-finally`块时该任务完成或已取消或引发异常时释放 COM 库。

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

以下示例使用 RAII 模式定义`CCoInitializer`类，该类管理给定作用域中的 COM 库的生存期。

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

可以使用`CCoInitializer`类，如下所示任务退出时自动释放 COM 库。

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

有关并发运行时中的取消操作的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)。

### <a name="using-com-with-asynchronous-agents"></a>使用 COM 和异步代理

使用异步代理使用 COM 时，调用`CoInitializeEx`在使用中的 COM 库之前[2&gt;concurrency::agent::run&lt;2}](reference/agent-class.md#run)你的代理的方法。 然后调用`CoUninitialize`之前`run`方法返回。 不使用 COM 管理例程中的构造函数或析构函数的代理，并且不会重写[concurrency::agent::start](reference/agent-class.md#start)或[concurrency:: agent:: 完成](reference/agent-class.md#done)方法因为这些方法从与不同的线程调用`run`方法。

下面的示例演示一个基本的代理类，名为`CCoAgent`，用于管理中的 COM 库`run`方法。

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

稍后在本演练提供了一个完整示例。

### <a name="using-com-with-lightweight-tasks"></a>使用 COM 和轻量级任务

文档[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)介绍并发运行时中的轻量级任务的角色。 您可以使用轻量级任务使用 COM，就像可以像使用传递给任何线程例程`CreateThread`Windows API 中的函数。 这在下面的示例中显示。

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>支持 COM 的应用程序示例

本部分说明的完整支持 COM 的应用程序使用`IScriptControl`接口来执行脚本，用于计算 n<sup>th</sup>斐波纳契数。 此示例先从主线程调用脚本，然后使用 PPL 和代理同时调用此脚本。

请考虑以下帮助器函数， `RunScriptProcedure`，它调用过程中`IScriptControl`对象。

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

`wmain`函数创建`IScriptControl`对象，将脚本代码添加到其计算 n<sup>th</sup>斐波纳契数，然后调用`RunScriptProcedure`函数来运行该脚本。

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>从 PPL 调用脚本

以下函数， `ParallelFibonacci`，使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法以并行调用脚本。 此函数使用`CCoInitializer`类来管理 COM 库的生存期在任务的每次迭代过程。

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

若要使用`ParallelFibonacci`函数的示例中，添加以下代码之前`wmain`函数返回。

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>从代理调用脚本

下面的示例演示`FibonacciScriptAgent`类，该类将调用的脚本过程来计算 n<sup>th</sup>斐波纳契数。 `FibonacciScriptAgent`类使用消息传递来接收从主程序中，输入到脚本函数的值。 `run`方法管理 COM 库在整个任务的生存期。

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

以下函数， `AgentFibonacci`，创建的多个`FibonacciScriptAgent`对象，并使用消息传递来发送多个输入值与这些对象。

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

若要使用`AgentFibonacci`函数的示例中，添加以下代码之前`wmain`函数返回。

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>完整示例

下面的代码演示使用并行算法和异步代理来调用脚本过程，用于计算斐波那契数字的完整示例。

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

该示例生成下面的示例输出。

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

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-scripts.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 并行 scripts.cpp /link ole32.lib**

## <a name="see-also"></a>请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
