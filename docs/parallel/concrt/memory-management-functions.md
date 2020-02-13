---
title: 内存管理函数
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: aa1951211283ddf7e4823a920d5cdf19bd6d977d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141839"
---
# <a name="memory-management-functions"></a>内存管理函数

本文档介绍并发运行时提供的内存管理函数，可帮助你以并发方式分配和释放内存。

> [!TIP]
> 并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序有助于微调应用程序的性能，因此，如果你不熟悉并发运行时，则建议你从[并行模式库（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)开始。

并发运行时提供了两个内存管理函数，它们经过优化，可用于以并发方式分配和释放内存块。 [Concurrency：：分配](reference/concurrency-namespace-functions.md#alloc)函数使用指定的大小分配内存块。 [Concurrency：： Free](reference/concurrency-namespace-functions.md#free)函数释放 `Alloc`分配的内存。

> [!NOTE]
> `Alloc` 和 `Free` 函数相互依赖。 仅使用 `Free` 函数来释放使用 `Alloc` 函数分配的内存。 此外，当你使用 `Alloc` 函数分配内存时，请仅使用 `Free` 函数来释放该内存。

从不同的线程或任务分配并释放一组固定的分配大小时，请使用 `Alloc` 和 `Free` 函数。 并发运行时会缓存它从 C 运行时堆中分配的内存。 并发运行时保存每个正在运行的线程的单独内存缓存，因此，运行时在不使用锁或内存屏障的情况下管理内存。 当更频繁地访问内存缓存时，应用程序会从 `Alloc` 和 `Free` 函数中获益更多。 例如，经常调用 `Alloc` 和 `Free` 优点的线程比主要调用 `Alloc` 或 `Free`的线程多。

> [!NOTE]
> 当你使用这些内存管理函数时，如果你的应用程序使用了大量内存，则该应用程序可能会比预期更快地进入低内存状态。 由于一个线程缓存的内存块不能用于任何其他线程，因此如果一个线程包含大量内存，则该内存不可用。

## <a name="example"></a>示例

有关使用 `Alloc` 和 `Free` 函数来提高内存性能的示例，请参阅[如何：使用分配和自由提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。

## <a name="see-also"></a>另请参阅

[任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
