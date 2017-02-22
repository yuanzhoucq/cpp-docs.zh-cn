---
title: "如何：使用 combinable 提高性能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combinable 类, 示例"
  - "使用 combinable 提高并行性能 [并发运行时]"
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：使用 combinable 提高性能
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例演示如何使用 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 类计算 [std::array](../../standard-library/array-class-stl.md) 对象中的质数和。  `combinable` 类通过消除共享状态来提高性能。  
  
> [!TIP]
>  在某些情况下，并行映射[concurrency::parallel\_transform](../Topic/parallel_transform%20Function.md)并减少 \([concurrency::parallel\_reduce](../Topic/parallel_reduce%20Function.md)\) 能够提供 `combinable`提升的性能。  有关使用映射和化简操作产生结果和此示例相同的示例，请参见 [并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 示例  
 下面的示例使用 [std::accumulate](../Topic/accumulate.md) 函数计算数组中质数元素的和。  在此示例中，`a` 为 `array` 对象，`is_prime` 函数将确定其输入值是否为质数。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_1.cpp)]  
  
## 示例  
 下面的示例演示一种将上一示例并行化的低级方式。  此示例使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 算法以并行方式处理数组和 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 对象，以同步对 `prime_sum` 变量的访问。  此示例不会缩放，因为每个线程都必须等待共享资源变为可用。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_2.cpp)]  
  
## 示例  
 下面的示例使用 `combinable` 对象提高上一示例的性能。  该示例不再需要同步对象；由于 `combinable` 对象使每个线程能够单独执行其任务，因此该示例将可以缩放。  
  
 通常分两个步骤使用 `combinable` 对象。  第一步，通过并行执行工作产生一系列细化的计算。  第二步，将这些计算合并（或减少）为一个最终结果。  此示例使用 [concurrency::combinable::local](../Topic/combinable::local%20Method.md) 方法获取对局部和的引用。  然后，此示例使用 [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) 方法和 [std::plus](../../standard-library/plus-struct.md) 对象将本地计算合并为最终结果。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_3.cpp)]  
  
## 示例  
 下面的完整示例按串行方式和并行方式分别计算质数的和。  该示例会将执行两个计算所需的时间输出到控制台。  
  
 [!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-improve-performance_4.cpp)]  
  
 下例是四处理器计算机的输出结果。  
  
  **1709600813**  
**序列化时间：6178 ms**  
**1709600813**  
**并行时间：1638 ms**   
## 编译代码  
 若要编译代码，请复制代码并将其粘贴到Visual Studio项目中或一个名为`parallel-sum-of-primes.cpp` 的文件中，然后在 Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc parallel\-sum\-of\-primes.cpp**  
  
## 可靠编程  
 有关使用、映射和化简操作产生相同的结果的示例，请参见 [并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 请参阅  
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable 类](../../parallel/concrt/reference/combinable-class.md)   
 [critical\_section 类](../../parallel/concrt/reference/critical-section-class.md)