---
title: 如何：使用 Alloc 和 Free 提高内存性能
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: 8438e833262d42c6083f48f759501c573a35c772
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142786"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>如何：使用 Alloc 和 Free 提高内存性能

本文档演示如何使用[concurrency：：分配](reference/concurrency-namespace-functions.md#alloc)和[Concurrency：： Free](reference/concurrency-namespace-functions.md#free)函数提高内存性能。 它将对两个不同类型（每个指定 `new` 和 `delete` 运算符）的数组的元素进行并行反向所需的时间进行比较。

当多个线程频繁同时调用 `Alloc` 和 `Free`时，`Alloc` 和 `Free` 函数最有用。 运行时为每个线程保留单独的内存缓存;因此，运行时在不使用锁或内存屏障的情况下管理内存。

## <a name="example"></a>示例

下面的示例演示三种类型，分别指定 `new` 和 `delete` 运算符。 `new_delete` 类使用 global `new` 和 `delete` 运算符，`malloc_free` 类使用 C 运行时[malloc](../../c-runtime-library/reference/malloc.md)和[free](../../c-runtime-library/reference/free.md)函数，而 `Alloc_Free` 类使用并发运行时 `Alloc` 和 `Free` 函数。

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>示例

下面的示例显示 `swap` 和 `reverse_array` 函数。 `swap` 函数将交换指定索引处的数组内容。 它为临时变量从堆中分配内存。 `reverse_array` 函数将创建一个大型数组，并计算一次将此数组并行反转所需的时间。

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>示例

下面的示例演示了 `wmain` 函数，该函数计算 `reverse_array` 函数对 `new_delete`、`malloc_free`和 `Alloc_Free` 类型执行操作所需的时间，每个函数都使用不同的内存分配方案。

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>示例

下面是完整的示例。

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

此示例为具有四个处理器的计算机生成以下示例输出。

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

在此示例中，使用 `Alloc` 和 `Free` 函数的类型提供最佳的内存性能，因为 `Alloc` 和 `Free` 函数都是为经常分配和释放多个线程中的内存块而优化的。

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `allocators.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc 分配器**

## <a name="see-also"></a>另请参阅

[内存管理函数](../../parallel/concrt/memory-management-functions.md)<br/>
[分配函数](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free 函数](reference/concurrency-namespace-functions.md#free)
