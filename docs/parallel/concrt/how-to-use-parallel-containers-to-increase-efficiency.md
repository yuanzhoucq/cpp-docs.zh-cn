---
title: 如何：使用并行容器提高效率
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: a9c428ee54853fbd8106901434823e69b402eace
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439177"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>如何：使用并行容器提高效率

本主题演示如何使用并行容器来高效地存储和访问数据并行。

示例代码计算质数和并行 Carmichael 数字的组。 然后，对于每个 Carmichael 号码，代码将计算该数字的主要因素。

## <a name="example"></a>示例

下面的示例演示`is_prime`函数，它确定输入的值是否为质数，和`is_carmichael`确定输入的值是否为 Carmichael 数的函数。

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>示例

下面的示例使用`is_prime`和`is_carmichael`函数来计算质数和 Carmichael 数字的集。 该示例使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)并[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)并行算法来计算每个设置。 有关并行算法的详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。

此示例使用[concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)对象以保存的一套 Carmichael 数字因为更高版本会将该对象用作工作队列。 它使用[concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)对象以保存组质数，因为它更高版本将循环访问此设置为查找质数因子。

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>示例

下面的示例演示`prime_factors_of`使用试用版的部门来查找所有质数因子的给定值的函数。

此函数使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法循环访问质数的集合。 `concurrent_vector`对象使并行循环，以同时向结果添加质数因子。

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>示例

本示例处理 Carmichael 数字的队列中的每个元素通过调用`prime_factors_of`函数来计算其主要因素。 它使用任务组来并行执行这项工作。 有关任务组的详细信息，请参阅[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

如果该数字有四个主要因素，此示例会输出每个 Carmichael 数的主要因素。

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>示例

下面的代码演示使用并行容器来计算 Carmichael 数字质数因子的完整示例。

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

此示例生成下面的示例输出。

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`carmichael-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc carmichael primes.cpp**

## <a name="see-also"></a>请参阅

[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector 类](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue 类](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke 函数](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for 函数](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group 类](reference/task-group-class.md)
