---
title: "如何：编写 parallel_for_each 循环 | Microsoft Docs"
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
  - "编写 parallel_for_each 循环 [并发运行时]"
  - "parallel_for_each 函数, 示例"
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：编写 parallel_for_each 循环
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例演示如何使用 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 算法并行计算 [std::array](../../standard-library/array-class-stl.md) 对象中质数的计数。  
  
## 示例  
 下面的示例分两次计算一个数组中质数的计数。  此示例先使用 [std::for\_each](../Topic/for_each.md) 算法按顺序计算该计数，  然后使用 `parallel_for_each` 算法并行执行同一任务。  此示例还会将执行两个计算所需的时间输出到控制台。  
  
 [!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-each-loop_1.cpp)]  
  
 下例是四处理器计算机的输出结果。  
  
  **序列化版本：**  
**生成 17984 个质数。**  
**执行了 6115 毫秒**  
**并行版本**  
**生成 17984 个质数。**  
**执行了 1653 毫秒**   
## 编译代码  
 若要编译代码，请复制代码并将其粘贴到Visual Studio 项目中或一个名为`parallel-count-primes.cpp`的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc parallel\-count\-primes.cpp**  
  
## 可靠编程  
 此示例传递给 `parallel_for_each` 算法的 lambda 表达式使用 `InterlockedIncrement` 函数来启用循环的并行迭代，以同时增大计数器。  如果使用函数（如 `InterlockedIncrement`）同步对共享资源的访问，则可以展现代码中的性能瓶颈。  可以使用无锁同步机制（如 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 类）取消对共享资源的同步访问。  有关按此方式使用 `combinable` 类的示例，请参见[如何：使用 combinable 提高性能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。  
  
## 请参阅  
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for\_each 函数](../Topic/parallel_for_each%20Function.md)