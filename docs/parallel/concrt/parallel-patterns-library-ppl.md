---
title: 并行模式库 (PPL)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
ms.openlocfilehash: 11440d56b9618d4763e1b7e47a21b365bbdc0c15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301846"
---
# <a name="parallel-patterns-library-ppl"></a>并行模式库 (PPL)

并行模式库 (PPL) 提供命令式编程模型，以促进开发并发应用程序的可扩展性和易用性。 PPL 构建在并发运行时的计划和资源管理组件上。 通过提供并行作用于数据的泛型安全算法和容器，提高应用程序代码与基础线程机制之间的抽象级别。 使用 PPL 还可以开发通过为共享状态提供替代方案实现缩放的应用程序。

PPL 提供以下功能：

- *任务并行*： 一种机制，基于 Windows 线程池来并行执行多个工作项 （任务）

- *并行算法*： 基于并发运行时操作适用于并行中的数据集合的泛型算法

- *并行容器和对象*： 提供对其元素的安全并发访问的泛型容器类型

## <a name="example"></a>示例

PPL 提供类似于编程模型C++标准库。 下面的示例展示 PPL 的多种功能。 串行和并行计算若干 Fibonacci 数字。 这两种计算都作用于[std:: array](../../standard-library/array-class-stl.md)对象。 示例还控制台输出了进行两种计算所需的时间。

串行版本使用C++标准库[std:: for_each](../../standard-library/algorithm-functions.md#for_each)算法来遍历该数组，并将存储中的结果[std:: vector](../../standard-library/vector-class.md)对象。 并行版本执行相同的任务，但使用的是 PPL [concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法，并将存储中的结果[concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)对象。 `concurrent_vector` 类可以使每个循环迭代并发添加元素，而无需同步对容器的写访问。

由于 `parallel_for_each` 并发操作，因此本示例的并行版本必须排列 `concurrent_vector` 对象的顺序才能生成与串行版本相同的结果。

请注意，该示例使用一个简单方法来计算斐波那契数字;但是，此方法说明了并发运行时如何提高的长计算性能。

[!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
serial time: 9250 ms
parallel time: 5726 ms

fib(24): 46368
fib(26): 121393
fib(41): 165580141
fib(42): 267914296
```

完成每个循环迭代所需的时间各不相同。 `parallel_for_each` 的性能由最后完成的操作决定。 因此，本示例的串行版本与并行版本不会有线性的性能提高。

## <a name="related-topics"></a>相关主题

|Title|描述|
|-----------|-----------------|
|[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|描述 PPL 中任务和任务组的角色。|
|[并行算法](../../parallel/concrt/parallel-algorithms.md)|描述如何使用并行算法，如 `parallel_for` 和 `parallel_for_each`。|
|[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)|描述 PPL 提供的各种并行容器和对象。|
|[PPL 中的取消操作](cancellation-in-the-ppl.md)|说明如何取消并行算法当前正在执行的工作。|
|[并发运行时](../../parallel/concrt/concurrency-runtime.md)|描述可以简化并发编程并包含相关主题链接的并发运行时。|
