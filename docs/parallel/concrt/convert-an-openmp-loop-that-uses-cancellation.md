---
title: "如何： 转换使用取消来使用并发运行时的 OpenMP 循环 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d3c4d37dfe5182e375e7581d6f5ef8188b922e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>如何：转换使用取消的 OpenMP 循环以使用并发运行时
某些并行循环不需要执行所有迭代。 例如，搜索值的算法可以终止后找到此值。 OpenMP 不提供一种机制来中断并行循环。 但是，你可以使用布尔值或标志，若要启用的循环，以指示已找到解决方案的一个迭代。 并发运行时提供的功能，使一个任务，以取消尚未开始其他任务。  
  
 此示例演示如何将转换 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[为](../../parallel/openmp/reference/for-openmp.md)不需要所有迭代中的运行以使用并发运行时取消机制的循环。  
  
## <a name="example"></a>示例  

 此示例使用 OpenMP 和并发运行时来实现的并行版本[std::any_of](../../standard-library/algorithm-functions.md#any_of)算法。 此示例的 OpenMP 版本使用一个标志来协调未满足的条件的所有并行循环迭代。 使用并发运行时的版本使用[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)方法来满足的条件时停止整个操作。  

  
 [!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
Using OpenMP...  
9114046 is in the array.  
Using the Concurrency Runtime...  
9114046 is in the array.  
```  
  
 在使用 OpenMP 的版本中，所有的循环迭代执行，甚至当标志设置。 此外，如果任务是具有任何子任务，该标志将还必须可供这些子任务取消传。 在并发运行时中，在任务组被取消时，运行时将取消的工作，包括子任务的整个树。 [Concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法使用任务来执行工作。 因此，当循环的一次迭代取消根任务，计算整个树也将被取消。 当工作树中的被取消时，运行时不会启动新任务。 但是，运行时允许已经开始完成的任务。 因此中的情况下`parallel_for_each`算法，活动的循环迭代可以清除其资源。  
  
 在此示例中这两个版本，如果数组包含多个副本的值来进行搜索，多个循环迭代可以每同时设置结果并取消整个操作。 如果你的问题需要满足的条件时，仅一个任务执行工作，可以使用一个同步基元，例如临界区。  
  
 你还可以使用异常处理来取消使用 PPL 任务。 有关取消的详细信息，请参阅[PPL 中的取消](cancellation-in-the-ppl.md)。  
  
 有关详细信息`parallel_for_each`和其他并行算法，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`concrt-omp-parallel-any-of.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc /openmp concrt-omp-并行-任何-of.cpp**  
  
## <a name="see-also"></a>请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [PPL 中的取消](cancellation-in-the-ppl.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)

