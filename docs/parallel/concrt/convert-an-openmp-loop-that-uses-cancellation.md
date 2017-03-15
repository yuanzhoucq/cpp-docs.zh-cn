---
title: "如何：转换使用取消的 OpenMP 循环以使用并发运行时 | Microsoft Docs"
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
  - "从 OpenMP 转换为并发运行时, 取消"
  - "取消, 从 OpenMP 转换为并发运行时"
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：转换使用取消的 OpenMP 循环以使用并发运行时
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

某些并行循环不需要执行所有迭代。  例如，搜索值的算法可以在找到值后终止。  OpenMP 不提供算法以跳出并行循环。  但是，您可以使用布尔值或标志，以允许循环的迭代指示已找到解决方案。  并发运行时提供允许一个任务取消其他尚未开始任务的功能。  
  
 本示例演示如何转换不需要运行所有迭代的 OpenMP [parallel](../../parallel/openmp/reference/parallel.md) [for](../../parallel/openmp/reference/for-openmp.md) 循环，以使用并发运行时取消机制。  
  
## 示例  
 本示例使用 OpenMP 和并发运行时实现 [std::any\_of](../Topic/any_of.md) 算法的并行版本。  本示例的 OpenMP 版本使用标志协调所有满足条件的并行循环迭代。  使用并发运行时的版本使用 [concurrency::structured\_task\_group::cancel](../Topic/structured_task_group::cancel%20Method.md) 方法在满足条件时停止全部操作。  
  
 [!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/CPP/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]  
  
 该示例产生下面的输出。  
  
  **使用OpenMP…**  
**9114046 在数组中。**  
**使用并发运行时...**  
**9114046 在数组中。** 在使用 OpenMP 的版本中，即使设置了标志，也会执行循环的所有迭代。  另外，如果任务具有任何子任务，则标志也必须可用于这些子任务以完成通信取消。  在并发运行时中，当取消任务组时，运行时会取消整个工作树，包括子任务。  [concurrency::parallel\_for\_each](../Topic/parallel_for_each%20Function.md) 算法使用任务执行工作。  因此，当循环的一个迭代取消根任务时，整个计算树也将被取消。  当取消工作树时，运行时不会开始新的任务。  但是，运行时允许已开始的任务完成。  因此，在执行 `parallel_for_each` 算法时，活动循环迭代可以清除它们的资源。  
  
 在本示例的两个版本中，如果数组包含多个要搜索的值的副本，则多个循环迭代可以各自同时设置结果并取消全部操作。  如果您的问题要求在满足条件时仅一个任务执行工作，则可以使用同步基元（例如临界区）。  
  
 您还可以使用异常处理取消使用 PPL 的任务。  有关取消操作的更多信息，请参见 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
 有关 `parallel_for_each` 和其他并行算法的更多信息，请参见[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## 编译代码  
 复制示例代码并将其粘贴到 Visual Studio项目中，或将其粘贴到名为`concrt-omp-parallel-any-of.cpp` 的文件中，然后在Visual Studio命令提示窗口中运行以下命令。  
  
 **cl.exe \/EHsc \/openmp concrt\-omp\-parallel\-any\-of.cpp**  
  
## 请参阅  
 [从 OpenMP 迁移至并发运行时](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [并行算法](../../parallel/concrt/parallel-algorithms.md)