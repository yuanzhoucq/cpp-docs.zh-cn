---
title: "如何：使用 Alloc 和 Free 提高内存性能 | Microsoft Docs"
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
  - "Alloc 和 Free, 使用 [并发运行时]"
  - "使用 Alloc 和 Free [并发运行时]"
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 Alloc 和 Free 提高内存性能
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档演示如何使用 [concurrency::Alloc](../Topic/Alloc%20Function.md) 和 [concurrency::Free](../Topic/Free%20Function.md) 函数提高内存性能。  本文将比较为三个不同的类型（每个类型都指定 `new` 和 `delete` 运算符）以并行方式反转数组的元素所需的时间。  
  
 `Alloc` 和 `Free` 函数在多个线程频繁调用 `Alloc` 和 `Free` 时非常有用。  由于运行时为每个线程保留单独的内存缓存，因此运行时无需使用锁或内存屏障即可管理内存。  
  
## 示例  
 下面的示例演示三个类型，每个类型都指定 `new` 和 `delete` 运算符。  `new_delete` 类使用全局 `new` 和 `delete` 运算符，`malloc_free` 类使用 C 运行时 [malloc](../../c-runtime-library/reference/malloc.md) 和 [free](../../c-runtime-library/reference/free.md) 函数，而 `Alloc_Free` 类使用并发运行时 `Alloc` 和 `Free` 函数。  
  
 [!CODE [concrt-allocators#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-allocators#1)]  
  
## 示例  
 下面的示例显示 `swap` 和 `reverse_array` 函数。  `swap` 函数将交换指定索引处的数组的内容。  此函数将为临时变量分配堆中的内存。  `reverse_array` 函数将创建一个大型数组，并计算以并行方式反转该数组多次所需的时间。  
  
 [!CODE [concrt-allocators#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-allocators#2)]  
  
## 示例  
 下面的示例显示 `wmain` 函数，此函数将计算 `reverse_array` 函数对 `new_delete`、`malloc_free` 和 `Alloc_Free` 类型（每个类型都使用不同的内存分配方案）进行操作所需的时间。  
  
 [!CODE [concrt-allocators#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-allocators#3)]  
  
## 示例  
 下面是完整的示例。  
  
 [!CODE [concrt-allocators#4](../CodeSnippet/VS_Snippets_ConcRT/concrt-allocators#4)]  
  
 下例是四处理器计算机的输出结果。  
  
  **new\/delete 花费 2031 毫秒。**  
**mallocc\/free花费1672 毫秒。**  
**Alloc\/Free花费656 毫秒。** 在此示例中，使用 `Alloc` 和 `Free` 函数的类型提供了最佳内存性能，因为 `Alloc` 和 `Free` 函数进行了优化，以便能够频繁分配和释放来自多个线程的内存块。  
  
## 编译代码  
 复制代码示例，再将此代码粘贴到 Visual Studio项目中或一个名为 `allocators.cpp` 的文件中，然后在 Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc allocators.cpp**  
  
## 请参阅  
 [内存管理函数](../../parallel/concrt/memory-management-functions.md)   
 [Alloc 函数](../Topic/Alloc%20Function.md)   
 [Free 函数](../Topic/Free%20Function.md)