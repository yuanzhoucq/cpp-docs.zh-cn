---
title: 如何：转换 OpenMP parallel for 循环以使用并发运行时
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 2d96ba23582368fe72e61003823826a6f3ab807a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141762"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>如何：转换 OpenMP parallel for 循环以使用并发运行时

此示例演示如何转换使用 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)和[for](../../parallel/openmp/reference/for-openmp.md)指令的基本循环，以使用并发运行时[Concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。

## <a name="example---prime-count"></a>示例-质数计数

此示例使用 OpenMP 和并发运行时来计算随机值数组中质数的计数。

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

本示例生成以下输出。

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for` 算法和 OpenMP 3.0 允许索引类型为带符号整型类型或无符号整数类型。 `parallel_for` 算法还可确保指定的范围不会溢出已签名的类型。 OpenMP 版本2.0 和2.5 仅允许已签名的整型索引类型。 OpenMP 也不验证索引范围。

此示例中使用并发运行时的版本还使用[Concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md)对象代替[原子](../../parallel/openmp/reference/atomic.md)指令来递增计数器值，而无需同步。

有关 `parallel_for` 和其他并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。 有关 `combinable` 类的详细信息，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="example---use-stdarray"></a>示例-使用 std：： array

此示例修改了上一个，以对[std：： array](../../standard-library/array-class-stl.md)对象而不是在本机数组上执行操作。 由于 OpenMP 版本2.0 和2.5 仅允许在 `parallel_for` 构造中使用已签名整数索引类型，因此不能使用迭代器并行访问C++标准库容器的元素。 并行模式库（PPL）提供并发的[：:p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法，该算法并行执行任务（如C++标准库提供的迭代容器）。 它使用 `parallel_for` 算法使用的分区逻辑相同。 `parallel_for_each` 算法类似于C++标准库[std：： for_each](../../standard-library/algorithm-functions.md#for_each)算法，不同之处在于 `parallel_for_each` 算法并发执行任务。

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `concrt-omp-count-primes.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc/openmp concrt-omp-count-primes**

## <a name="see-also"></a>另请参阅

[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)
