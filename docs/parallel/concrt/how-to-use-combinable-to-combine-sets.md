---
title: 如何： 使用 combinable 来组合集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69f48ed099fe033ba1847a3414ed8e5c5ce88f71
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433668"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>如何：使用 combinable 来组合集

本主题演示如何使用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类来计算质数的组。

## <a name="example"></a>示例

以下示例将计算组质数两次。 每个计算存储中的结果[std::bitset](../../standard-library/bitset-class.md)对象。 该示例首先按顺序计算集，然后计算并行组。 示例还控制台输出了进行两种计算所需的时间。

此示例使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)算法和`combinable`对象生成线程本地设置。 然后，它使用[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)方法，可以合并到最后一组线程本地设置。

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

以下是具有四个处理器的计算机的输出示例。

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`parallel-combine-primes.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc 并行组合 primes.cpp**

## <a name="see-also"></a>请参阅

[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable 类](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable:: combine_each 方法](reference/combinable-class.md#combine_each)

