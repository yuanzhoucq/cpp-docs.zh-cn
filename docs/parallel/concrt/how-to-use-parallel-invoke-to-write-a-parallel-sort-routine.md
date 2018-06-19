---
title: 如何： 使用 parallel_invoke 来编写并行排序例程 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53b9699c7ee5d2bd4775f2d6b97dc4d1c5155ce0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689163"
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>如何：使用 parallel_invoke 来编写并行排序例程
本文档介绍如何使用[parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke)算法提高双调排序算法的性能。 双调排序算法以递归方式将输入的序列划分为较小排序分区。 双调排序算法可以并行运行，因为每个分区操作独立于所有其他操作。  
  
 尽管双调排序是一种*排序网络*按输入序列的所有组合，此示例中对其长度为 2 的幂的序列进行都排序。  
  
> [!NOTE]
>  为了便于说明，此示例使用并行排序例程。 你还可以使用 PPL 提供的内置排序算法： [concurrency:: parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)， [concurrency:: parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)，和[concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)。 有关详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="top"></a> 部分  
 本文档介绍了以下任务：  
  
- [按顺序执行双调排序](#serial)  
  
- [并行使用 parallel_invoke 来执行双调排序](#parallel)  
  
##  <a name="serial"></a> 按顺序执行双调排序  
 下面的示例演示双调排序算法的序列化版本。 `bitonic_sort`函数序列分成两个分区、 对按相反方向，这些分区进行排序，然后将合并结果。 此函数调用自身两次以递归方式进行排序的每个分区。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]  
  
 [[返回页首](#top)]  
  
##  <a name="parallel"></a> 并行使用 parallel_invoke 来执行双调排序  
 本部分介绍如何使用`parallel_invoke`中并行执行双调排序算法的算法。  
  
### <a name="procedures"></a>过程  
  
##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>若要并行执行双调排序算法  
  
1.  添加`#include`标头文件 ppl.h 指令。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]  
  
2.  添加`using`指令`concurrency`命名空间。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]  
  
3.  创建一个新函数，调用`parallel_bitonic_mege`，它使用`parallel_invoke`合并并行序列，如果没有足够的工作要做量的算法。 否则，调用`bitonic_merge`以连续合并序列。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]  
  
4.  执行类似于一个在以前步骤中，但对于过程`bitonic_sort`函数。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]  
  
5.  创建一个重载的版本的`parallel_bitonic_sort`进行排序以升序数组的函数。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]  
  
 `parallel_invoke`算法通过在调用上下文中执行的任务序列的最后一个可降低开销。 例如，在`parallel_bitonic_sort`函数，第一个任务运行在单独的上下文，并将在调用上下文运行第二个任务。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]  
  
 下面的完整示例执行序列和双调排序算法的并行版本。 该示例还会将执行每个计算所需的时间打印到控制台。  
  
 [!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]  
  
 以下是具有四个处理器的计算机的输出示例。  
  
```Output  
serial time: 4353  
parallel time: 1248  
```  
  
 [[返回页首](#top)]  
  
## <a name="compiling-the-code"></a>编译代码  
 若要编译代码，将其复制，然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-bitonic-sort.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc 并行双调 sort.cpp**  
  
## <a name="robust-programming"></a>可靠编程  
 此示例使用`parallel_invoke`算法而不是[concurrency:: task_group](reference/task-group-class.md)类，因为每个任务组的生存期均未超出函数。 我们建议你使用`parallel_invoke`何时可以因为它具有较少执行开销比`task group`对象，并因此允许你编写更好地执行代码。  
  
 只有在没有足够的工作要做时，某些算法的并行版本更好地执行。 例如，`parallel_bitonic_merge`函数调用序列化版本， `bitonic_merge`，如果序列中有 500 个或更少元素。 你还可以计划基于的工作量的整体排序策略。 例如，它可能是更高效，以使用快速排序算法的序列化版本，如果数组包含少于 500 个项，如下面的示例中所示：  
  
 [!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]  
  
 与任何并行算法，我们建议你分析和优化根据你的代码。  
  
## <a name="see-also"></a>请参阅  
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)

