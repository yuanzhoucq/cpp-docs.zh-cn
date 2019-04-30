---
title: 如何：使用 Alloc 和 Free 提高内存性能
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: f55bf360ac2b4c7162c1ed2b917ac6ce8c7cd11f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410014"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>如何：使用 Alloc 和 Free 提高内存性能

本文档演示如何使用[concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)并[concurrency:: free](reference/concurrency-namespace-functions.md#free)函数提高内存性能。 它将进行比较的时间所需的元素进行反向数组中并行的三个不同类型，每个指定`new`和`delete`运算符。

`Alloc`并`Free`多个线程频繁调用时，函数是最有用`Alloc`和`Free`。 在运行时保存每个线程，则单独的内存缓存因此，在运行时管理内存而不使用锁或内存屏障。

## <a name="example"></a>示例

下面的示例演示三种类型，每个指定`new`和`delete`运算符。 `new_delete`类使用的全局`new`和`delete`运算符`malloc_free`类使用 C 运行时[malloc](../../c-runtime-library/reference/malloc.md)并[免费](../../c-runtime-library/reference/free.md)函数和`Alloc_Free`类使用并发运行时`Alloc`和`Free`函数。

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>示例

下面的示例显示 `swap` 和 `reverse_array` 函数。 `swap`函数的指定索引处的数组内容进行交换。 它会临时变量的堆中分配内存。 `reverse_array`函数创建一个大数组，并计算反向多次并行该数组所需的时间。

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>示例

下面的示例演示`wmain`函数来计算所需的时间`reverse_array`函数，以便做出`new_delete`， `malloc_free`，和`Alloc_Free`类型，其中每个使用不同的内存分配方案。

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>示例

以下是完整的示例。

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

此示例生成了四个处理器的计算机的以下示例输出。

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

在此示例中，该类型，使用`Alloc`并`Free`函数提供最佳的内存性能，因为`Alloc`和`Free`函数针对频繁分配和释放的内存从多个块进行了优化线程数。

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`allocators.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc allocators.cpp**

## <a name="see-also"></a>请参阅

[内存管理函数](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc 函数](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free 函数](reference/concurrency-namespace-functions.md#free)
