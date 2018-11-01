---
title: 如何：转换 OpenMP parallel for 循环以使用并发运行时
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, parallel for loops
- converting from OpenMP to the Concurrency Runtime, parallel loops
- parallel for loops, converting from OpenMP to the Concurrency Runtime
- parallel loops, converting from OpenMP to the Concurrency Runtime
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
ms.openlocfilehash: 9ab80df8bfe4c06ee36e0a60db4800be68576909
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488551"
---
# <a name="how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime"></a>如何：转换 OpenMP parallel for 循环以使用并发运行时

此示例演示如何将一个基本循环使用 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)并[有关](../../parallel/openmp/reference/for-openmp.md)指令以使用并发运行时[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法。

## <a name="example"></a>示例

此示例使用 OpenMP 和并发运行时计算数组中的随机值的质数的计数。

[!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]

本示例生成以下输出。

```Output
Using OpenMP...
found 107254 prime numbers.
Using the Concurrency Runtime...
found 107254 prime numbers.
```

`parallel_for`算法和 OpenMP 3.0 允许索引类型为带符号整型类型或无符号整型类型。 `parallel_for`算法还可确保指定的范围内不会溢出有符号的类型。 OpenMP 版本 2.0 和 2.5 允许仅适用于有符号整数的索引类型。 OpenMP 还不会验证索引范围。

此示例中使用并发运行时的版本也使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)对象来代替[原子](../../parallel/openmp/reference/atomic.md)指令的计数器值增加而无需同步。

有关详细信息`parallel_for`和其他并行算法，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。 有关详细信息`combinable`类，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="example"></a>示例

此示例修改上一个，以便做出[std:: array](../../standard-library/array-class-stl.md)对象而不是在本机数组。 因为对于仅在已签名整数索引类型允许使用 OpenMP 2.0 版和 2.5`parallel_for`构造，您不能使用迭代器访问并行中的 c + + 标准库容器的元素。 并行模式库 (PPL) 提供了[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法，将按并行，例如由 c + + 标准库提供对迭代容器执行任务。 它使用相同的分区逻辑的`parallel_for`算法使用。 `parallel_for_each`算法类似于 c + + 标准库[std:: for_each](../../standard-library/algorithm-functions.md#for_each)算法，不同之处在于`parallel_for_each`算法并发执行任务。

[!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/cpp/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`concrt-omp-count-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc /openmp concrt-omp-计数-primes.cpp**

## <a name="see-also"></a>请参阅

[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)

