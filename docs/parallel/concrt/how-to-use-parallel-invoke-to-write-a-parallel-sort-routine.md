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
ms.openlocfilehash: e72d99cb1b9168e3de1e109d93c163e21cb7fad7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440152"
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>如何：使用 parallel_invoke 来编写并行排序例程

本文档介绍如何使用[parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke)算法提高双调排序算法的性能。 双调排序算法以递归方式将输入的序列划分为较小的已排序分区。 双调排序算法可以并行运行，因为每个分区操作独立于所有其他操作。

尽管双调排序是举例*排序网络*，使其按输入序列的所有组合，此示例中对其长度为 2 的幂的序列进行都排序。

> [!NOTE]
>  为了便于说明，此示例使用并行排序例程。 此外可以使用 PPL 提供的内置排序算法： [concurrency:: parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)， [concurrency:: parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)，和[concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort)。 有关详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

##  <a name="top"></a> 部分

本文档介绍了以下任务：

- [按顺序执行双调排序](#serial)

- [并行使用 parallel_invoke 来执行双调排序](#parallel)

##  <a name="serial"></a> 按顺序执行双调排序

下面的示例演示双调排序算法的序列化版本。 `bitonic_sort`函数将序列划分为两个分区中，对这些分区按相反方向进行排序，然后将合并结果。 此函数调用自身两次以递归方式进行排序的每个分区。

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[返回页首](#top)]

##  <a name="parallel"></a> 并行使用 parallel_invoke 来执行双调排序

本部分介绍如何使用`parallel_invoke`算法并行执行双调排序算法。

### <a name="procedures"></a>过程

##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>若要并行执行双调排序算法

1. 添加`#include`标头文件 ppl.h 指令。

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. 添加`using`指令`concurrency`命名空间。

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. 创建一个名为的新函数`parallel_bitonic_mege`，使用`parallel_invoke`算法合并并行序列是否存在足够长的可执行的操作。 否则，调用`bitonic_merge`按顺序合并序列。

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. 执行过程中在上一步，但对于类似`bitonic_sort`函数。

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. 创建的一个重载的版本`parallel_bitonic_sort`对按升序排列数组进行排序的函数。

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke`算法通过对调用上下文中执行的任务序列的最后一个减少开销。 例如，在`parallel_bitonic_sort`函数，第一个任务运行在单独的上下文，并在调用的上下文中的第二个任务运行。

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

若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-bitonic-sort.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 并行双调 sort.cpp**

## <a name="robust-programming"></a>可靠编程

此示例使用`parallel_invoke`算法而不是[concurrency:: task_group](reference/task-group-class.md)类，因为每个任务组的生存期不超出函数。 我们建议你使用`parallel_invoke`何时可以因为它具有较少执行开销比`task group`对象，并因此使你可以编写更好的执行代码。

只有在没有足够的可执行的操作时，某些算法的并行版本更好地执行。 例如，`parallel_bitonic_merge`函数调用序列化版本， `bitonic_merge`，如果序列中有 500 或更少元素。 您还可以规划整体排序策略根据工作的量。 例如，可能会更高效，若要使用快速排序算法的序列化版本，如果数组包含少于 500 个项，如下面的示例中所示：

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

与任何并行算法，我们建议你分析和调整相应代码。

## <a name="see-also"></a>请参阅

[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)

