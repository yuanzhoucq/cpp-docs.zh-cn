---
title: 如何：转换使用异常处理的 OpenMP 循环以使用并发运行时
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 380a96eedb8a70965197c4a5ce0c5199bc268db5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141818"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>如何：转换使用异常处理的 OpenMP 循环以使用并发运行时

此示例演示如何转换执行异常处理的 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../../parallel/openmp/reference/for-openmp.md)循环以使用并发运行时异常处理机制。

在 OpenMP 中，并行区域中引发的异常必须由同一线程在同一区域中捕获和处理。 用于转义并行区域的异常由未经处理的异常处理程序捕获，此异常处理程序默认情况下会终止进程。

在并发运行时中，当你在传递给任务组（如[concurrency：： task_group](reference/task-group-class.md)或[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象）的工作函数体中引发异常时，或者在并行算法（如[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)）中引发异常时，运行时将存储该异常，并将其封送到等待任务组或算法完成的上下文中。 对于任务组，等待上下文是调用[concurrency：： task_group：： wait](reference/task-group-class.md#wait)、 [concurrency：： structured_task_group：： wait](reference/structured-task-group-class.md#wait)、 [concurrency：： task_group：： run_and_wait](reference/task-group-class.md#run_and_wait)或 concurrency：： [structured_task_group：： run_and_wait](reference/structured-task-group-class.md#run_and_wait)的上下文。 对于并行算法，等待上下文是调用该算法的上下文。 运行时还会停止任务组中的所有活动任务（包括子任务组中的任务），并放弃尚未启动的任何任务。

## <a name="example"></a>示例

此示例演示如何处理 OpenMP `parallel` 区域中的异常和对 `parallel_for`的调用中的异常。 `do_work` 函数执行的内存分配请求不会成功，因此引发了[std：： bad_alloc](../../standard-library/bad-alloc-class.md)类型的异常。 在使用 OpenMP 的版本中，引发异常的线程还必须捕获该异常。 换句话说，OpenMP 并行循环的每次迭代都必须处理异常。 在使用并发运行时的版本中，主线程捕获由另一个线程引发的异常。

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

本示例生成以下输出。

```Output
Using OpenMP...
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
Using the Concurrency Runtime...
An error of type 'class std::bad_alloc' occurred.
```

在此示例中，使用 OpenMP 的版本发生异常，并由每个循环迭代进行处理。 在使用并发运行时的版本中，运行时存储异常，停止所有活动任务，丢弃尚未启动的所有任务，并将异常封送到调用 `parallel_for`的上下文。

如果您要求在发生异常后使用 OpenMP 的版本终止，则可以使用布尔标志来向其他循环迭代发出错误发生的信号。 如主题[如何：转换使用取消的 OpenMP 循环来使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)的示例中所示，如果设置了标志，则后续循环迭代将不执行任何操作。 相反，如果您要求在发生异常后继续使用并发运行时的循环，请处理并行循环正文本身中的异常。

并发运行时的其他组件（如异步代理和轻量级任务）不传输异常。 相反，未经处理的异常处理程序会捕获未处理的异常，默认情况下会终止进程。 有关异常处理的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

有关 `parallel_for` 和其他并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `concrt-omp-exceptions.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc/openmp concrt-omp-exceptions**

## <a name="see-also"></a>另请参阅

[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)
