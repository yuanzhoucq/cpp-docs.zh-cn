---
title: 内存管理函数
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: 9a7810267c3eaa11ad7592774440365620e7e8f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413861"
---
# <a name="memory-management-functions"></a>内存管理函数

本文档介绍并发运行时提供可帮助您分配和释放内存以并发方式的内存管理函数。

> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 因为任务计划程序可帮助您优化您的应用程序的性能，我们建议您开始[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)你是否新并发运行时。

并发运行时提供了两个针对分配和释放内存块的能力以并发方式进行了优化的内存管理函数。 [Concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)函数通过使用指定的大小分配的内存块。 [Concurrency:: free](reference/concurrency-namespace-functions.md#free)函数释放已分配的内存`Alloc`。

> [!NOTE]
>  `Alloc`和`Free`函数相互依赖。 使用`Free`函数仅用于释放通过使用分配的内存`Alloc`函数。 此外，使用`Alloc`函数来分配内存时，只能使用`Free`函数，以释放该内存。

使用`Alloc`和`Free`函数时分配和释放一组固定的分配大小从不同的线程或任务。 并发运行时将缓存它从 C 运行时堆中分配的内存。 并发运行时保存每个正在运行的线程; 的单独的内存缓存因此，在运行时管理内存而不使用锁或内存屏障。 应用程序受益越多，从`Alloc`和`Free`函数时更频繁地访问内存缓存。 例如，经常同时调用的线程`Alloc`并`Free`好处超过主要调用的线程`Alloc`或`Free`。

> [!NOTE]
>  当你使用这些内存管理函数，并输入你应用程序使用大量的内存，该应用程序可能内存不足的情况更快地比预期。 由于缓存的一个线程的内存块不是可用于任何其他线程，如果一个线程保留了大量的内存，则该内存不可用。

## <a name="example"></a>示例

有关使用示例`Alloc`并`Free`函数提高内存性能，请参阅[如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。

## <a name="see-also"></a>请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
