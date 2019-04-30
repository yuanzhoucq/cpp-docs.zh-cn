---
title: 如何：使用 combinable 提高性能
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: c8f4c40be84b2204e5b5632fe6d3d5a5d22b8719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410001"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>如何：使用 combinable 提高性能

此示例演示如何使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类，以计算中的数字的总和[std:: array](../../standard-library/array-class-stl.md)质数的对象。 `combinable`类消除共享的状态，从而提高了性能。

> [!TIP]
>  在某些情况下，并行映射 ([concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform))，并减少 ([并发:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) 可以通过提供性能改进`combinable`。 有关使用映射和化简操作即可生成与此示例中相同的结果的示例，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="example"></a>示例

下面的示例使用[std:: accumulate](../../standard-library/numeric-functions.md#accumulate)函数来计算质数数组中元素的总和。 在此示例中，`a`是`array`对象和`is_prime`函数将确定其输入的值是否为质数。

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example"></a>示例

下面的示例显示了并行化上一示例的简单方法。 此示例使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法来处理并行数组和一个[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)对象对访问进行同步`prime_sum`变量. 此示例不会进行扩展，因为每个线程必须等待共享资源变为可用状态。

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example"></a>示例

下面的示例使用`combinable`对象以提高性能的上一个示例。 此示例不需要的同步对象。因为它具有的伸缩性`combinable`对象使每个线程来独立地执行其任务。

一个`combinable`对象通常用在了两个步骤。 首先，通过并行执行工作来生成一系列的细化的计算。 接下来，将合并 （或减少） 计算为最终的结果。 此示例使用[concurrency::combinable::local](reference/combinable-class.md#local)方法来获取对本地之和的引用。 然后，它使用[concurrency::combinable::combine](reference/combinable-class.md#combine)方法和一个[std::plus](../../standard-library/plus-struct.md)要合并为最终结果将本地计算对象。

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example"></a>示例

下面的完整示例串行和并行计算素数数字的总和。 该示例向控制台显示所需执行这两个计算的时间。

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>编译代码

若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-sum-of-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 并行的总和-的-primes.cpp**

## <a name="robust-programming"></a>可靠编程

有关使用映射和化简操作即可生成相同的结果的示例，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

## <a name="see-also"></a>请参阅

[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable 类](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section 类](../../parallel/concrt/reference/critical-section-class.md)
