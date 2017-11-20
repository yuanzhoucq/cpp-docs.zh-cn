---
title: "内存管理函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c090041969bae959ecb386486032f3f848a1440b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management-functions"></a>内存管理函数
本文档介绍并发运行时提供的可帮助你分配和释放内存以并发方式的内存管理函数。  
  
> [!TIP]
>  并发运行时提供了一个默认计划程序，因此无需在应用程序中创建一个。 由于任务计划程序有助于细微调整你的应用程序的性能，我们建议你开始使用[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)或[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)如果你是新的并发运行。  
  
 并发运行时提供两个针对分配和释放内存块的能力以并发方式进行了优化的内存管理函数。 [Concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)函数通过使用指定的大小中分配的内存块。 [Concurrency:: free](reference/concurrency-namespace-functions.md#free)函数释放已分配的内存`Alloc`。  
  
> [!NOTE]
>  `Alloc`和`Free`函数相互依赖。 使用`Free`函数仅用于释放通过使用分配的内存`Alloc`函数。 此外，当使用`Alloc`函数以分配内存时，只能使用`Free`函数来释放该内存。  
  
 使用`Alloc`和`Free`函数时分配和释放一组固定的分配大小从不同的线程或任务。 并发运行时缓存它从 C 运行时堆中分配的内存。 并发运行时保存单独的内存缓存中，以便每个正在运行的线程;因此，运行时管理内存而不使用锁或内存屏障。 应用程序受益越多从`Alloc`和`Free`函数时更频繁地访问内存缓存。 例如，经常同时调用的线程`Alloc`和`Free`好处超过主要调用线程`Alloc`或`Free`。  
  
> [!NOTE]
>  当您使用这些内存管理函数，并输入你的应用程序使用大量内存，应用程序可能内存不足的情况更快地比预期。 因为通过某个线程缓存的内存块均不可用于其他任何线程，如果一个线程持有大量内存，则该内存不可用。  
  
## <a name="example"></a>示例  
 有关示例，使用`Alloc`和`Free`函数提高内存性能，请参阅[如何： 使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
## <a name="see-also"></a>另请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

