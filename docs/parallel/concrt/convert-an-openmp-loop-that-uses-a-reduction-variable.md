---
title: 如何：转换使用缩减变量以使用并发运行时的 OpenMP 循环
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: d75e115bdb1d13c9e8f45ed67d0f3993eac1b387
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257314"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>如何：转换使用缩减变量以使用并发运行时的 OpenMP 循环

此示例演示如何将转换 OpenMP[并行](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[有关](../../parallel/openmp/reference/for-openmp.md)使用循环[减少](../../parallel/openmp/reference/reduction.md)子句，以使用并发运行时。

OpenMP`reduction`子句允许您指定遵循缩减操作并行区域末尾的一个或多个线程私有变量。 OpenMP 预定义一组减少运算符。 每个 reduction 变量必须是标量 (例如， `int`， `long`，和`float`)。 OpenMP 还定义如何在并行区域中使用缩减变量的多个限制。

并行模式库 (PPL) 提供了[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)类，该类提供可让你执行细化的计算，然后将这些计算合并到最终的可重用的线程本地存储结果。 `combinable`类是作用于标量和复杂类型的模板。 若要使用`combinable`类、 并行构造正文中执行子计算，然后调用[concurrency::combinable::combine](reference/combinable-class.md#combine)或[concurrency::combinable::combine_each](reference/combinable-class.md#combine_each)若要生成最终结果的方法。 `combine`并`combine_each`每个方法均采用*组合函数*，指定如何组合的每对元素。 因此，`combinable`类并不局限于一组固定的缩减运算符。

## <a name="example"></a>示例

此示例使用 OpenMP 和并发运行时计算第一次 35 斐波那契数字的总和。

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

本示例生成以下输出。

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

有关详细信息`combinable`类，请参阅[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`concrt-omp-fibonacci-reduction.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc /openmp concrt-omp-fibonacci-reduction.cpp**

## <a name="see-also"></a>请参阅

[从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)
