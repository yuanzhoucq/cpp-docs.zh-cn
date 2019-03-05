---
title: 如何：转换使用异常处理以使用并发运行时的 OpenMP 循环
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 118cf3e485fa78ae3eaa5efe34708924b89d6588
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285147"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>如何：转换使用异常处理以使用并发运行时的 OpenMP 循环

此示例演示如何将转换 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)执行异常处理，以使用并发运行时异常处理机制的循环。

OpenMP，必须捕获并在同一区域中处理同一个线程并行区域中引发的异常。 转义并行区域的异常捕获了未经处理的异常处理程序，默认情况下会终止进程。

在并发运行时，当引发如传递给任务组的工作函数体中出现异常时[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象，或如并行算法[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)，运行时存储该异常，并将其封送到等待的任务组或算法来完成的上下文。 对于任务组，等待上下文是调用的上下文[task_group](reference/task-group-class.md#wait)， [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)， [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait)，或[concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait)。 有关并行算法的等待上下文是调用该算法的上下文。 运行时也会停止任务组，包括中的子任务组中的所有活动任务，并放弃任何尚未启动的任务。

## <a name="example"></a>示例

此示例演示如何处理异常中 OpenMP`parallel`区域，在调用`parallel_for`。 `do_work`函数执行的内存分配请求的不成功，并因此引发类型的异常[std:: bad_alloc](../../standard-library/bad-alloc-class.md)。 在使用 OpenMP 的版本，则引发异常的线程必须还捕获它。 换而言之，OpenMP 并行循环每次迭代必须处理该异常。 在使用并发运行时版本，主线程会捕获由另一个线程引发的异常。

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

在此示例使用 OpenMP 的版本中，异常中发生，并由每个循环迭代处理。 在使用并发运行时版本，运行时将异常存储、 停止所有活动任务，放弃任何尚未启动的任务和封送到调用上下文的异常`parallel_for`。

如果您需要使用 OpenMP 的版本后会发生异常终止，可以使用一个布尔型标志将信号发送到其他循环迭代发生的错误。 如本主题中的示例中所示[如何：转换使用并发运行时，使用取消的 OpenMP 循环](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)，如果设置了标志后续循环迭代会执行任何操作。 相反，如果您需要使用并发运行时的循环继续后会发生异常，处理并行循环主体本身中的异常。

并发运行时，异步代理和轻量级任务等其他组件不会传输异常。 相反，通过默认情况下终止进程的未处理的异常处理程序中捕获到未经处理的异常。 有关异常处理的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

有关详细信息`parallel_for`和其他并行算法，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`concrt-omp-exceptions.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc /openmp concrt-omp-exceptions.cpp**

## <a name="see-also"></a>请参阅

[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)
