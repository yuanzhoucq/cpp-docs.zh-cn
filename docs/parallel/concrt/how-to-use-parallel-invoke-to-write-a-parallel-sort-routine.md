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
ms.openlocfilehash: 6acac3f6bc82db6e6981f83715c7ee88cfd06fbd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855392"
---
# <a name="how-to-use-parallel_invoke-to-write-a-parallel-sort-routine"></a>如何：使用 parallel_invoke 来编写并行排序例程

本文档介绍如何使用[parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke)算法提高双调排序算法的性能。 双调排序算法以递归方式将输入序列划分为较小的排序分区。 双调排序算法可以并行运行，因为每个分区操作都独立于所有其他操作。

尽管双调排序是对输入序列的所有组合进行排序的*排序网络*的示例，但此示例对长度为2的幂的序列进行排序。

> [!NOTE]
> 为了便于说明，此示例使用并行排序例程。 你还可以使用 PPL 提供的内置排序算法： [concurrency：:p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)、 [concurrency：:p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)和[concurrency：:p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)。 有关详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="top"></a> 部分

本文档介绍了下列任务：

- [按顺序执行双调排序](#serial)

- [使用 parallel_invoke 并行执行双调排序](#parallel)

## <a name="serial"></a>按顺序执行双调排序

下面的示例显示了双调排序算法的序列版本。 `bitonic_sort` 函数将序列分为两个分区，按相反的方向对这些分区进行排序，然后合并结果。 此函数以递归方式调用自身两次以对每个分区进行排序。

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[返回页首](#top)]

## <a name="parallel"></a>使用 parallel_invoke 并行执行双调排序

本部分介绍如何使用 `parallel_invoke` 算法并行执行双调排序算法。

### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>并行执行双调排序算法

1. 为头文件 ppl 添加 `#include` 指令。

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. 为 `concurrency` 命名空间添加 `using` 指令。

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. 创建名为 `parallel_bitonic_mege`的新函数，该函数使用 `parallel_invoke` 算法并行合并序列（如果有足够的工作要做）。 否则，调用 `bitonic_merge` 以按顺序合并序列。

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. 执行与上一步中类似的进程，但对于 `bitonic_sort` 函数。

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. 创建 `parallel_bitonic_sort` 函数的重载版本，该函数按递增顺序对数组进行排序。

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke` 算法通过执行调用上下文上的一系列任务中的最后一个来减少系统开销。 例如，在 `parallel_bitonic_sort` 函数中，第一个任务在单独的上下文中运行，第二个任务在调用上下文中运行。

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

下面的完整示例执行双调排序算法的串行和并行版本。 该示例还会将执行每个计算所需的时间打印到控制台。

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
serial time: 4353
parallel time: 1248
```

[[返回页首](#top)]

### <a name="compiling-the-code"></a>编译代码

若要编译代码，请复制代码并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `parallel-bitonic-sort.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc parallel-bitonic-sort**

## <a name="robust-programming"></a>可靠的编程

此示例使用 `parallel_invoke` 算法而不是[concurrency：： task_group](reference/task-group-class.md)类，因为每个任务组的生存期不超出函数。 我们建议你在可能的情况下使用 `parallel_invoke`，因为它的执行开销低于 `task group` 对象，因此你可以编写更好的代码。

仅当有足够的工作要完成时，某些算法的并行版本才能更好地执行。 例如，如果序列中有500或更少元素，则 `parallel_bitonic_merge` 函数将调用序列版本 `bitonic_merge`。 你还可以根据工作量计划总体排序策略。 例如，如果数组包含少于500项，则使用快速排序算法的串行版本可能更高效，如以下示例中所示：

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

与任何并行算法一样，我们建议你根据需要对代码进行分析和调整。

## <a name="see-also"></a>另请参阅

[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)
