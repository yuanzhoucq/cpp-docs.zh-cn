---
title: "如何：转换使用异常处理的 OpenMP 循环以使用并发运行时 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "异常处理, 从 OpenMP 转换为并发运行时"
  - "从 OpenMP 转换为并发运行时, 异常处理"
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：转换使用异常处理的 OpenMP 循环以使用并发运行时
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例演示如何转换执行异常处理的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 循环，以使用并发运行时异常处理机制。  
  
 在 OpenMP 中，必须在同一区域中由相同的线程捕获和处理并行区域中引发的异常。  转义并行区域的异常由未经处理的异常处理程序捕获，默认情况下该处理程序会终止进程。  
  
 在并发运行时中，当您在传递给任务组（例如 [concurrency::task\_group](../Topic/task_group%20Class.md) 或 [Concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 对象）或并行算法（例如 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md)）的工作函数的主体中引发异常时，运行时会存储该异常并将其封送至等待任务组或算法完成的上下文。  对于任务组，等待上下文是调用 [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md)、[concurrency::structured\_task\_group::wait](../Topic/structured_task_group::wait%20Method.md)、[concurrency::task\_group::run\_and\_wait](../Topic/task_group::run_and_wait%20Method.md) 或 [concurrency::structured\_task\_group::run\_and\_wait](../Topic/structured_task_group::run_and_wait%20Method.md) 的上下文。  对于并行算法，等待上下文是调用该算法的上下文。  运行时还停止任务组中所有活动的任务（包括子任务组中的活动任务），并放弃任何尚未开始的任务。  
  
## 示例  
 本示例演示如何处理 OpenMP `parallel` 区域和 `parallel_for` 调用中的异常。  `do_work` 函数执行不成功并进而引发 [std::bad\_alloc](../../standard-library/bad-alloc-class.md) 类型的异常的内存分配请求。  在使用 OpenMP 的版本中，引发异常的线程还必须捕获该异常。  也就是说，OpenMP 并行循环的每次迭代都必须处理异常。  在使用并发运行时的版本中，由主线程捕获其他线程引发的异常。  
  
 [!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **使用OpenMP…**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**类型“class std::bad\_alloc”发生错误。**  
**使用并发运行时...**  
**类型“class std::bad\_alloc”发生错误。** 本示例的版本使用 OpenMP，每次的循环迭代中发生的异常由该循环迭代进行处理。  在使用并发运行时的版本中，运行时存储异常、停止所有活动任务、放弃任何尚未开始的任务，并且将异常封送至调用 `parallel_for` 的上下文。  
  
 如果您需要使用 OpenMP 的版本在异常发生后终止，则可以使用布尔标志向发生错误的其他循环迭代发送信号。  如主题[如何：转换使用取消的 OpenMP 循环以使用并发运行时](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)中的示例所示，在设置了标志的情况下，后续的循环迭代不执行任何操作。  相反，如果您需要使用并发运行时的循环在异常发生后继续执行，则在并行循环主体自身中处理异常。  
  
 并发运行时的其他组件（例如异步代理和轻量级任务）不会传输异常。  而是由未经处理的异常处理程序来捕获未经处理的异常，默认情况下该处理程序会终止进程。  有关异常处理的更多信息，请参见[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 有关 `parallel_for` 和其他并行算法的更多信息，请参见[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 编译代码  
 复制该代码示例，并将其粘贴到 Visual Studio项目中或名为 `concrt-omp-exceptions.cpp`的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-exceptions.cpp**  
  
## 请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)