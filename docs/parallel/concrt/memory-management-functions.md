---
title: "内存管理函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内存管理函数 [并发运行时]"
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
caps.latest.revision: 6
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 内存管理函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档描述了并发运行时提供的内存管理函数如何帮助您以并发方式分配和释放内存。  
  
> [!TIP]
>  并发运行时提供默认的计划程序，因此您不需要在应用程序中再创建一个计划程序。  由于任务计划程序可帮助您优化应用程序的性能，因此，如果您初次接触并发运行时，则建议您先使用 [并行模式库 \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 或 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)。  
  
 并发运行时提供两个内存管理函数，它们进行了优化以便以并发方式分配和释放内存块。  [concurrency::Alloc](../Topic/Alloc%20Function.md) 函数通过使用指定的大小来分配内存块。  [concurrency::Free](../Topic/Free%20Function.md) 函数释放由 `Alloc` 分配的内存。  
  
> [!NOTE]
>  `Alloc` 和 `Free` 函数相互依赖。  `Free` 函数仅用于释放使用 `Alloc` 函数分配的内存。  同样，当使用 `Alloc` 函数分配内存时，只能使用 `Free` 函数释放该内存。  
  
 当从不同的线程或任务分配和释放一组固定的分配大小时，使用 `Alloc` 和 `Free` 函数。  并发运行时将缓存它从 C 运行时堆分配的内存。  由于并发运行时为每个正在运行的线程保留单独的内存缓存，因此运行时无需使用锁或内存屏障即可管理内存。  系统访问内存缓存越频繁，应用程序从 `Alloc` 和 `Free` 函数受益越多。  例如，经常同时调用 `Alloc` 和 `Free` 的线程要比主要调用 `Alloc` 或 `Free` 的线程受益多。  
  
> [!NOTE]
>  在使用这些内存管理函数，并且您的应用程序使用许多内存时，应用程序可能比预期更早地出现内存不足情况。  由于一个线程缓存的内存块不可用于其他任何线程，因此如果一个线程占有大量内存，则该内存不可用。  
  
## 示例  
 有关使用 `Alloc` 和 `Free` 函数来提高内存性能的示例，请参见[如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)。  
  
## 请参阅  
 [任务计划程序](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [如何：使用 Alloc 和 Free 提高内存性能](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)