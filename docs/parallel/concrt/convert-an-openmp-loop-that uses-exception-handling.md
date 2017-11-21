---
title: "如何： 转换使用异常处理以使用并发运行时的 OpenMP 循环 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: beac8ca095388428986569433f0461a505f2a7e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>如何：转换使用异常处理的 OpenMP 循环以使用并发运行时
此示例演示如何将转换 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)执行异常处理来使用并发运行时异常处理机制的循环。  
  
 OpenMP，必须捕获和由同一个线程在同一区域中处理并行区域中引发的异常。 转义并行区域的异常捕获了未经处理的异常处理程序中，默认情况下会终止进程。  
  

 并发运行时，当引发如传递给任务组的工作函数正文中异常中[concurrency:: task_group](reference/task-group-class.md)或[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)对象，或如并行算法[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)，则运行时存储该异常并将其封送到等待任务组或算法来完成的上下文。 对于任务组的等待上下文是调用的上下文[concurrency::task_group::wait](reference/task-group-class.md#wait)， [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait)， [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait)，或[concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait)。 有关并行算法的等待上下文是调用该算法的上下文。 运行时还将停止任务组，包括子任务组中的那些中的所有活动任务，并放弃任何尚未启动的任务。  


  
## <a name="example"></a>示例  
 此示例演示如何在 OpenMP 中处理异常`parallel`区域和对的调用中`parallel_for`。 `do_work`函数执行的不成功，并因此引发异常的类型的内存分配请求[std:: bad_alloc](../../standard-library/bad-alloc-class.md)。 在使用 OpenMP 的版本，会引发异常的线程必须也会捕获它。 换而言之，OpenMP 并行循环的每个迭代必须处理的异常。 在版本中使用并发运行时，主线程捕捉由另一个线程引发异常。  
  
 [!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]  
  
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
  
 在此示例中，使用 OpenMP 版本中，异常中发生，并且由每个循环迭代处理。 在版本中使用并发运行时，运行时将异常存储、 停止所有活动任务、 放弃任何尚未启动的任务和封送到调用上下文异常`parallel_for`。  
  
 如果你需要使用 OpenMP 版本终止在异常发生后，你可以使用一个布尔型标志来通知其他循环迭代指示发生了错误。 如主题中示例所示[如何： 转换使用并发运行时该使用取消的 OpenMP 循环](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)，如果将标志设置后续循环迭代将不执行任何操作。 相反，如果你需要在异常发生后，将继续使用并发运行时的循环，处理并行循环本体当中中的异常。  
  
 并发运行时，异步代理和轻量级任务，如其他组件不会传输异常。 相反，默认情况下终止进程的未处理的异常处理程序捕获未经处理的异常。 有关异常处理的详细信息，请参阅[异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 有关详细信息`parallel_for`和其他并行算法，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`concrt-omp-exceptions.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc /openmp concrt-omp-exceptions.cpp**  
  
## <a name="see-also"></a>另请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [异常处理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)

