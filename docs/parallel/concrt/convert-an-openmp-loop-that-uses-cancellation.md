---
title: 如何：转换使用取消的 OpenMP 循环以使用并发运行时
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: df55a58617b802f24e4caf13784ac080222b93bc
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631531"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>如何：转换使用取消的 OpenMP 循环以使用并发运行时

某些并行循环不要求执行所有迭代。 例如, 搜索值的算法可以在找到值后终止。 OpenMP 未提供中断并行循环的机制。 但是, 可以使用布尔值或标志来启用循环迭代, 以指示已找到解决方案。 并发运行时提供了一项功能, 该功能可让一个任务取消其他尚未开始的任务。

此示例演示如何转换 OpenMP [parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../../parallel/openmp/reference/for-openmp.md)循环, 该循环不要求所有迭代都运行以使用并发运行时取消机制。

## <a name="example"></a>示例

此示例使用 OpenMP 和并发运行时来实现[std:: any_of](../../standard-library/algorithm-functions.md#any_of)算法的并行版本。 此示例的 OpenMP 版本使用标志在满足条件的所有并行循环迭代之间进行协调。 使用并发运行时的版本使用[Concurrency:: structured_task_group:: cancel](reference/structured-task-group-class.md#cancel)方法在满足条件时停止整个操作。

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

本示例生成以下输出。

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

在使用 OpenMP 的版本中, 即使设置了标志, 也会执行循环的所有迭代。 此外, 如果某个任务具有任何子任务, 则该标志还必须对这些子任务可用才能进行取消。 在并发运行时中, 当取消任务组时, 运行时将取消整个工作树, 包括子任务。 [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法使用任务来执行工作。 因此, 当循环的一次迭代取消根任务时, 也将取消整个计算树。 当取消工作树时, 运行时不会启动新任务。 但是, 运行时允许已启动的任务完成。 因此, 在`parallel_for_each`算法中, 活动循环迭代可以清理其资源。

在此示例的两个版本中, 如果数组包含要搜索的值的多个副本, 则每个循环迭代可以同时设置结果并取消整个操作。 如果问题要求在满足条件时只有一个任务执行工作, 则可以使用同步基元 (如临界区)。

你还可以使用异常处理来取消使用 PPL 的任务。 有关取消的详细信息, 请参阅[PPL 中的取消](cancellation-in-the-ppl.md)操作。

有关`parallel_for_each`和其他并行算法的详细信息, 请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 visual studio 项目中, 或粘贴到一个名`concrt-omp-parallel-any-of.cpp`为的文件中, 然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl/EHsc/openmp concrt-omp-parallel-any-of**

## <a name="see-also"></a>请参阅

[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[PPL 中的取消操作](cancellation-in-the-ppl.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)
