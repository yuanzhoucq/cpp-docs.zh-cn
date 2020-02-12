---
title: 演练：在启用 COM 的应用程序中使用并发运行时
ms.date: 04/25/2019
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: faa072ab2b5973ace0f0ca138dcedffa56044213
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140623"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>演练：在启用 COM 的应用程序中使用并发运行时

本文档演示如何在使用组件对象模型（COM）的应用程序中使用并发运行时。

## <a name="prerequisites"></a>先决条件

在开始本演练之前，请阅读以下文档：

- [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [并行算法](../../parallel/concrt/parallel-algorithms.md)

- [异步代理](../../parallel/concrt/asynchronous-agents.md)

- [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

有关 COM 的详细信息，请参阅[组件对象模型（COM）](/windows/win32/com/component-object-model--com--portal)。

## <a name="managing-the-lifetime-of-the-com-library"></a>管理 COM 库的生存期

尽管对并发运行时使用 COM 与任何其他并发机制遵循相同的原则，但以下准则可帮助你有效地结合使用这些库。

- 线程必须先调用[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) ，然后才能使用 COM 库。

- 只要每次调用都提供相同的参数，线程就可以多次调用 `CoInitializeEx`。

- 对于 `CoInitializeEx`的每个调用，线程还必须调用[CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize)。 换句话说，必须平衡对 `CoInitializeEx` 和 `CoUninitialize` 的调用。

- 若要从一个线程单元切换到另一个线程单元，线程必须先完全释放 COM 库，然后再使用新的线程规范调用 `CoInitializeEx`。

其他 COM 原则适用于使用 COM 与并发运行时。 例如，在单线程单元（STA）中创建对象并将该对象封送到其他单元的应用程序还必须提供消息循环来处理传入消息。 另请记住，在单元间封送对象会降低性能。

### <a name="using-com-with-the-parallel-patterns-library"></a>结合使用 COM 与并行模式库

将 COM 与并行模式库（PPL）中的组件（例如，任务组或并行算法）结合使用时，在每个任务或迭代期间使用 COM 库之前调用 `CoInitializeEx`，并在每个任务或迭代完成之前调用 `CoUninitialize`。 下面的示例演示如何使用[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象管理 COM 库的生存期。

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

您必须确保在任务或并行算法被取消或任务正文引发异常时正确释放 COM 库。 为了保证任务在退出之前调用 `CoUninitialize`，请使用 `try-finally` 块或*资源采集为初始化*（RAII）模式。 下面的示例使用 `try-finally` 块在任务完成或取消或引发异常时释放 COM 库。

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

下面的示例使用 RAII 模式来定义 `CCoInitializer` 类，该类管理给定范围内 COM 库的生存期。

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

在任务退出时，可以使用 `CCoInitializer` 类自动释放 COM 库，如下所示。

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

有关并发运行时中的取消的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

### <a name="using-com-with-asynchronous-agents"></a>结合使用 COM 和异步代理

将 COM 与异步代理一起使用时，请在为代理使用[concurrency：： agent：： run](reference/agent-class.md#run)方法中的 com 库之前调用 `CoInitializeEx`。 然后在 `run` 方法返回之前调用 `CoUninitialize`。 不要在您的代理的构造函数或析构函数中使用 COM 管理例程，并且不要覆盖[concurrency：： agent：： start](reference/agent-class.md#start)或[concurrency：： agent：:d 一种](reference/agent-class.md#done)方法，因为这些方法是从 `run` 方法之外的其他线程中调用的。

下面的示例演示一个名为 `CCoAgent`的基本代理类，该类管理 `run` 方法中的 COM 库。

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

本演练稍后会提供完整的示例。

### <a name="using-com-with-lightweight-tasks"></a>通过轻量级任务使用 COM

文档[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)描述了并发运行时中轻量级任务的角色。 与在 Windows API 中传递到 `CreateThread` 函数的任何线程例程一样，可以将 COM 与轻型任务配合使用。 这在下面的示例中显示。

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>启用 COM 的应用程序的示例

本部分介绍一个完整的启用 COM 的应用程序，该应用程序使用 `IScriptControl` 接口来执行计算<sup>第</sup>n 个斐波那契数字的脚本。 此示例首先从主线程调用脚本，然后使用 PPL 和代理来并发调用脚本。

请考虑以下 helper 函数，`RunScriptProcedure`，它调用 `IScriptControl` 对象中的过程。

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

`wmain` 函数将创建一个 `IScriptControl` 对象，向其添加用于计算<sup>第</sup>n 个斐波那契数的脚本代码，然后调用该 `RunScriptProcedure` 函数以运行该脚本。

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>从 PPL 调用脚本

以下函数 `ParallelFibonacci`使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法以并行方式调用脚本。 此函数使用 `CCoInitializer` 类在任务的每次迭代期间管理 COM 库的生存期。

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

若要将 `ParallelFibonacci` 函数与示例一起使用，请在 `wmain` 函数返回之前添加以下代码。

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>从代理调用脚本

下面的示例演示了 `FibonacciScriptAgent` 类，该类调用脚本过程来计算<sup>第</sup>n 个斐波那契数。 `FibonacciScriptAgent` 类使用消息传递从主程序接收到脚本函数的输入值。 `run` 方法管理整个任务中 COM 库的生存期。

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

以下函数 `AgentFibonacci`创建多个 `FibonacciScriptAgent` 对象，并使用消息传递向这些对象发送多个输入值。

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

若要将 `AgentFibonacci` 函数与示例一起使用，请在 `wmain` 函数返回之前添加以下代码。

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>完整示例

下面的代码演示了一个完整的示例，该示例使用并行算法和异步代理来调用用于计算斐波那契数的脚本过程。

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

该示例生成以下示例输出。

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

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `parallel-scripts.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc parallel-scripts/link ole32.lib**

## <a name="see-also"></a>另请参阅

[并发运行时演练](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[异步代理](../../parallel/concrt/asynchronous-agents.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
