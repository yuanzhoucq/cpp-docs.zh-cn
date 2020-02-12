---
title: 如何：使用 combinable 组合多个集
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: 7ccbb3e8bad5c4d3b6f4177afbfdba3e200681a5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142121"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>如何：使用 combinable 组合多个集

本主题说明如何使用[concurrency：：可组合](../../parallel/concrt/reference/combinable-class.md)类来计算质数集。

## <a name="example"></a>示例

下面的示例计算质数集两次。 每个计算将结果存储在[std：：位组](../../standard-library/bitset-class.md)对象中。 该示例首先按顺序计算集合，然后并行计算该集。 示例还控制台输出了进行两种计算所需的时间。

此示例使用[concurrency：:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法和 `combinable` 对象生成线程本地集。 然后，它使用[concurrency：：可组合：： combine_each](reference/combinable-class.md#combine_each)方法将线程本地集合并到最终集。

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `parallel-combine-primes.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc parallel-combine-primes**

## <a name="see-also"></a>另请参阅

[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable 类](../../parallel/concrt/reference/combinable-class.md)<br/>
[组合：： combine_each 方法](reference/combinable-class.md#combine_each)
