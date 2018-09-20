---
title: 如何： 编写 parallel_for_each 循环 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c68afa77c46e4d57ef01984b44ecb6f4951494a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427077"
---
# <a name="how-to-write-a-parallelforeach-loop"></a>如何：编写 parallel_for_each 循环

此示例演示如何使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)算法来计算质数的计数[std:: array](../../standard-library/array-class-stl.md)并行中的对象。

## <a name="example"></a>示例

以下示例将计算数组中的质数的计数两次。 该示例首先使用[std:: for_each](../../standard-library/algorithm-functions.md#for_each)算法要按顺序计算其计数。 该示例然后使用`parallel_for_each`算法并行执行相同的任务。 示例还控制台输出了进行两种计算所需的时间。

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>编译代码

若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-count-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 并行计数 primes.cpp**

## <a name="robust-programming"></a>可靠编程

该示例将传递给 lambda 表达式`parallel_for_each`算法使用`InterlockedIncrement`函数，以使并行迭代的循环，以同时递增计数器。 如果使用函数如`InterlockedIncrement`来同步对共享资源的访问，可以提供性能瓶颈在代码中。 您可以使用免锁定同步机制，例如，则[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类中，以消除对共享资源同时访问。 有关使用示例`combinable`类以这种方式，请参阅[如何： 使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。

## <a name="see-also"></a>请参阅

[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each 函数](reference/concurrency-namespace-functions.md#parallel_for_each)

