---
title: 如何：并行执行映射和减少操作
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: 599e46c05a91a1f2ea6e317fe024d3c98a78977f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141708"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>如何：并行执行映射和减少操作

此示例演示如何使用[concurrency：:p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)和 concurrency： [:p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)算法，并使用[concurrency：： concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)类对文件中的单词进行计数。

*映射*操作将函数应用于序列中的每个值。 *化简*操作将序列的元素合并为一个值。 您可以使用C++标准库[std：： transform](../../standard-library/algorithm-functions.md#transform)和[std：：累积](../../standard-library/numeric-functions.md#accumulate)函数来执行映射和化简操作。 但是，为了提高许多问题的性能，你可以使用 `parallel_transform` 算法并行执行映射操作，并使用 `parallel_reduce` 算法并行执行化简操作。 在某些情况下，你可以使用 `concurrent_unordered_map` 以一步操作执行映射和化简。

## <a name="example"></a>示例

以下示例计算了文件中单词出现的次数。 它使用[std：： vector](../../standard-library/vector-class.md)来表示两个文件的内容。 映射操作计算了每个向量中每个单词出现的次数。 化简操作累积了跨这两个向量的字数统计。

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>编译代码

若要编译代码，请复制代码并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `parallel-map-reduce.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc parallel-map-reduce**

## <a name="robust-programming"></a>可靠的编程

在此示例中，你可以使用在 concurrent_unordered_map.h 中定义的 `concurrent_unordered_map` 类以一步操作执行映射和化简。

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

通常情况下，你只需并行化外部或内部循环。 如果你的文件相对较少并且每个文件中包含的单词很多，则可以并行化内部循环。 如果你的文件相对较多并且每个文件中包含的单词比较少，则可以并行化外部循环。

## <a name="see-also"></a>另请参阅

[并行算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform 函数](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce 函数](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map 类](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
