---
title: "如何：转换 OpenMP parallel for 循环以使用并发运行时 | Microsoft Docs"
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
  - "从 OpenMP 转换为并发运行时，parallel for 循环"
  - "从 OpenMP 转换为并发运行时，并行循环"
  - "parallel for 循环，从 OpenMP 转换为并发运行时"
  - "并行循环，从 OpenMP 转换为并发运行时"
ms.assetid: d8a7b656-f86c-456e-9c5d-a7d52f94646e
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：转换 OpenMP parallel for 循环以使用并发运行时
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本示例演示如何转换使用 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) 和 [for](../../parallel/openmp/reference/for-openmp.md) 指令的基本循环，以便使用并发运行时 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 算法。  
  
## 示例  
 本示例使用 OpenMP 和并发运行时计算随机值数组中质数的计数。  
  
 [!code-cpp[concrt-openmp#1](../../parallel/concrt/codesnippet/CPP/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **使用OpenMP…**  
**生成 107254 个质数。**  
**使用并发运行时...**  
**生成 107254 个质数。** `parallel_for` 算法和 OpenMP 3.0 允许索引类型成为带符号的整数类型或不带符号的整数类型。  `parallel_for` 算法还确保指定范围不会溢出带符号类型。  OpenMP 2.0 和 2.5 版只允许带符号的整数索引类型。  OpenMP 也不验证索引范围。  
  
 使用并发运行时的此示例版本还使用 [atomic](../../parallel/openmp/reference/atomic.md) 指令中的 [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) 对象在无需同步的情况下递增计数器值。  
  
 有关 `parallel_for` 和其他并行算法的更多信息，请参见[并行算法](../../parallel/concrt/parallel-algorithms.md)。  有关 `combinable` 类的更多信息，请参见[并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)。  
  
## 示例  
 此示例修改了前面的示例，以便作用于 [std::array](../../standard-library/array-class-stl.md) 对象而不是本机数组。  因为 OpenMP 2.0 和 2.5 版只在 `parallel` `for` 构造中允许带符号的整数索引类型，所以您无法使用迭代器并行访问标准模板库 \(STL\) 容器中的元素。  并行模式库 \(PPL\) 提供 [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 算法，以便在迭代容器上并行执行任务（如 STL 提供的任务）。  此算法使用的分区逻辑与 `parallel_for` 算法使用的分区逻辑相同。  `parallel_for_each` 算法与 STL [std::for\_each](../Topic/for_each.md) 算法类似，只是 `parallel_for_each` 算法并发执行任务。  
  
 [!code-cpp[concrt-openmp#10](../../parallel/concrt/codesnippet/CPP/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime_2.cpp)]  
  
## 编译代码  
 复制该代码示例，并将其粘贴到Visual Studio 项目中或名为`concrt-omp-count-primes.cpp`的文件中，然后在Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-count\-primes.cpp**  
  
## 请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)   
 [并行容器和对象](../../parallel/concrt/parallel-containers-and-objects.md)