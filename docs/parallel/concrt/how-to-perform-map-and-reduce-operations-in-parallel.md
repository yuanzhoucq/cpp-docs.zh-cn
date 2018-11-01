---
title: 如何：并行执行映射和减少操作
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: b73e46e63fc1b320a84322bf2b0efd7adf244ccb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651840"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>如何：并行执行映射和减少操作

此示例演示如何使用[concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)并[concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)算法和[concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)类的文件中单词出现次数进行计数。

一个*映射*操作将函数应用于序列中的每个值。 一个*减少*操作组合为一个值序列的元素。 可以使用 c + + 标准库[std:: transform](../../standard-library/algorithm-functions.md#transform)并[std:: accumulate](../../standard-library/numeric-functions.md#accumulate)函数来执行映射和化简操作。 但是，为了提高许多问题的性能，你可以使用 `parallel_transform` 算法并行执行映射操作，并使用 `parallel_reduce` 算法并行执行化简操作。 在某些情况下，你可以使用 `concurrent_unordered_map` 以一步操作执行映射和化简。

## <a name="example"></a>示例

以下示例计算了文件中单词出现的次数。 它使用[std:: vector](../../standard-library/vector-class.md)来表示两个文件的内容。 映射操作计算了每个向量中每个单词出现的次数。 化简操作累积了跨这两个向量的字数统计。

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>编译代码

若要编译代码，将其复制然后将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-map-reduce.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 并行映射 reduce.cpp**

## <a name="robust-programming"></a>可靠编程

在此示例中，你可以使用在 concurrent_unordered_map.h 中定义的 `concurrent_unordered_map` 类以一步操作执行映射和化简。

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

通常情况下，你只需并行化外部或内部循环。 如果你的文件相对较少并且每个文件中包含的单词很多，则可以并行化内部循环。 如果你的文件相对较多并且每个文件中包含的单词比较少，则可以并行化外部循环。

## <a name="see-also"></a>请参阅

[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform 函数](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce 函数](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map 类](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
