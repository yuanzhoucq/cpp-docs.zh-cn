---
title: 如何：使用 parallel_invoke 来编写并行排序例程
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 9d84cdbecb7cc6d39cb30077780c558db85888c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222714"
---
# <a name="how-to-use-parallel_invoke-to-write-a-parallel-sort-routine"></a>如何：使用 parallel_invoke 来编写并行排序例程

本文档介绍如何使用[parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke)算法提高双调排序算法的性能。 双调排序算法以递归方式将输入序列划分为较小的排序分区。 双调排序算法可以并行运行，因为每个分区操作都独立于所有其他操作。

尽管双调排序是对输入序列的所有组合进行排序的*排序网络*的示例，但此示例对长度为2的幂的序列进行排序。

> [!NOTE]
> 为了便于说明，此示例使用并行排序例程。 你还可以使用 PPL 提供的内置排序算法： [concurrency：:p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)、 [concurrency：:p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)和[concurrency：:p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)。 有关详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="sections"></a><a name="top"></a>个

本文档介绍了下列任务：

- [按顺序执行双调排序](#serial)

- [使用 parallel_invoke 并行执行双调排序](#parallel)

## <a name="performing-bitonic-sort-serially"></a><a name="serial"></a>按顺序执行双调排序

下面的示例显示了双调排序算法的序列版本。 `bitonic_sort`函数将序列分为两个分区，按相反方向对这些分区进行排序，然后合并结果。 此函数以递归方式调用自身两次以对每个分区进行排序。

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[顶部](#top)]

## <a name="using-parallel_invoke-to-perform-bitonic-sort-in-parallel"></a><a name="parallel"></a>使用 parallel_invoke 并行执行双调排序

本部分介绍如何使用 `parallel_invoke` 算法并行执行双调排序算法。

### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>并行执行双调排序算法

1. `#include`为头文件 ppl 添加指令。

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. **`using`** 为命名空间添加指令 `concurrency` 。

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. 创建一个名为的新函数 `parallel_bitonic_mege` ，该函数使用 `parallel_invoke` 算法并行合并序列（如果有足够的工作要做）。 否则，调用 `bitonic_merge` 以按顺序合并序列。

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. 执行与上一步中的进程类似的进程，但对于函数，则执行 `bitonic_sort` 。

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. 创建 `parallel_bitonic_sort` 函数的重载版本，该函数按递增顺序对数组进行排序。

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

该 `parallel_invoke` 算法通过执行调用上下文中的一系列任务，来减少系统开销。 例如，在函数中 `parallel_bitonic_sort` ，第一个任务在单独的上下文中运行，第二个任务在调用上下文中运行。

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

下面的完整示例执行双调排序算法的串行和并行版本。 该示例还会将执行每个计算所需的时间打印到控制台。

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
serial time: 4353
parallel time: 1248
```

[[顶部](#top)]

### <a name="compiling-the-code"></a>编译代码

若要编译代码，请复制代码，然后将其粘贴到 Visual Studio 项目中，或粘贴到一个名为的文件中， `parallel-bitonic-sort.cpp` 然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl.exe/EHsc parallel-bitonic-sort**

## <a name="robust-programming"></a>可靠编程

此示例使用 `parallel_invoke` 算法而不是[concurrency：： task_group](reference/task-group-class.md)类，因为每个任务组的生存期不超出函数。 建议你使用， `parallel_invoke` 因为它的执行开销比对象的执行开销更少 `task group` ，因此你可以编写更好的代码。

仅当有足够的工作要完成时，某些算法的并行版本才能更好地执行。 例如， `parallel_bitonic_merge` `bitonic_merge` 如果序列中有500或更少元素，则函数将调用序列版本。 你还可以根据工作量计划总体排序策略。 例如，如果数组包含少于500项，则使用快速排序算法的串行版本可能更高效，如以下示例中所示：

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

与任何并行算法一样，我们建议你根据需要对代码进行分析和调整。

## <a name="see-also"></a>另请参阅

[任务并行度](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)
