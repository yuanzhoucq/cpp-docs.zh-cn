---
title: "如何： 使用 Alloc 和 Free 提高内存性能 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 984e39cbec3016a3baa747cfa382220a04db1bbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>如何：使用 Alloc 和 Free 提高内存性能

本文档演示如何使用[concurrency:: alloc](reference/concurrency-namespace-functions.md#alloc)和[concurrency:: free](reference/concurrency-namespace-functions.md#free)函数提高内存性能。 它将所需的元素进行反向数组中并行三种不同类型的时间进行比较各指定`new`和`delete`运算符。  

  
 `Alloc`和`Free`时多个线程频繁调用函数是很有用`Alloc`和`Free`。 运行时保存单独的内存缓存中，以便每个线程;因此，运行时管理内存而不使用锁或内存屏障。  
  
## <a name="example"></a>示例  
 下面的示例演示三种类型各指定`new`和`delete`运算符。 `new_delete`类使用全局`new`和`delete`运算符，`malloc_free`类使用 C 运行时[malloc](../../c-runtime-library/reference/malloc.md)和[免费](../../c-runtime-library/reference/free.md)函数，与`Alloc_Free`类使用并发运行时`Alloc`和`Free`函数。  
  
 [!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例显示 `swap` 和 `reverse_array` 函数。 `swap`函数的指定索引处的数组的内容进行交换。 它的临时变量的堆中分配内存。 `reverse_array`函数将创建一个大数组，计算反向多次中并行该数组所需的时间。  
  
 [!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]  
  
## <a name="example"></a>示例  
 下面的示例演示`wmain`函数来计算所需的时间`reverse_array`函数可对其执行操作`new_delete`， `malloc_free`，和`Alloc_Free`类型，其中每个使用不同的内存分配方案。  
  
 [!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]  
  
## <a name="example"></a>示例  
 以下是完整的示例。  
  
 [!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]  
  
 该示例产生下面的示例输出具有四个处理器的计算机。  
  
```Output  
Took 2031 ms with new/delete.  
Took 1672 ms with malloc/free.  
Took 656 ms with Alloc/Free.  
```  
  
 在此示例中，该类型，使用`Alloc`和`Free`函数提供最佳的内存性能，因为`Alloc`和`Free`函数进行了优化的频繁分配和释放从多个内存块的能力线程。  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`allocators.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc allocators.cpp**  
  
## <a name="see-also"></a>请参阅  
 [内存管理函数](../../parallel/concrt/memory-management-functions.md)   
 [Alloc 函数](reference/concurrency-namespace-functions.md#alloc)   
 [Free 函数](reference/concurrency-namespace-functions.md#free)

