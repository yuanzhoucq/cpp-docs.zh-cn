---
title: "如何：使用 parallel_invoke 来编写并行排序例程 | Microsoft Docs"
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
  - "task_handle 类, 示例"
  - "task_group 类, 示例"
  - "make_task 函数, 示例"
  - "structured_task_group 类, 示例"
  - "使用任务组提高并行性能 [并发运行时]"
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
caps.latest.revision: 23
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 parallel_invoke 来编写并行排序例程
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文档介绍如何使用 [parallel\_invoke](../Topic/parallel_invoke%20Function.md) 算法提升 bitonic 排序算法的性能。  bitonic 排序算法以递归方式将输入序列分为较小的排序分区。  bitonic 排序算法可以并行方式运行，因为每个分区操作均独立于所有其他操作。  
  
 尽管 bitonic 排序是对输入序列所有组合进行排序的排序网络的一个示例，但此示例将对其长度为 2 的幂的序列进行排序。  
  
> [!NOTE]
>  此示例仅供阐释之使用并行排序例程。  还可以使用 PPL 提供的内置排序算法：[concurrency::parallel\_sort](../Topic/parallel_sort%20Function.md)[concurrency::parallel\_buffered\_sort](../Topic/parallel_buffered_sort%20Function.md)[concurrency::parallel\_radixsort](../Topic/parallel_radixsort%20Function.md)、和。  有关详细信息，请参阅[并行算法](../../parallel/concrt/parallel-algorithms.md)。  
  
##  <a name="top"></a> 各节内容  
 本文档介绍了以下任务：  
  
-   [按顺序执行 Bitonic 排序](#serial)  
  
-   [使用 parallel\_invoke 并行执行 bitonic 排序](#parallel)  
  
##  <a name="serial"></a> 按顺序执行 Bitonic 排序  
 下面的示例演示了 bitonic 排序算法的序列化版本。  `bitonic_sort` 函数将序列分成两个分区，以相反方向对这些分区进行排序，然后合并结果。  此函数以递归方式调用自身两次以对每个分区进行排序。  
  
 [!CODE [concrt-parallel-bitonic-sort#1](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#1)]  
  
 \[[Top](#top)\]  
  
##  <a name="parallel"></a> 使用 parallel\_invoke 并行执行 bitonic 排序  
 本节介绍如何使用 `parallel_invoke` 算法并行执行 bitonic 排序算法。  
  
### 过程  
  
##### 以并行方式执行 bitonic 排序算法  
  
1.  为头文件 ppl.h 添加 `#include` 指令。  
  
     [!CODE [concrt-parallel-bitonic-sort#10](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#10)]  
  
2.  为`concurrency`命名空间添加 `using` 指令。  
  
     [!CODE [concrt-parallel-bitonic-sort#11](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#11)]  
  
3.  创建名为 `parallel_bitonic_mege` 的新函数，此函数使用 `parallel_invoke` 算法在具有要处理的大量工作时并行合并序列。  否则，调用 `bitonic_merge` 以连续合并序列。  
  
     [!CODE [concrt-parallel-bitonic-sort#2](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#2)]  
  
4.  执行与前面步骤中的进程类似但却适用于 `bitonic_sort` 函数的进程。  
  
     [!CODE [concrt-parallel-bitonic-sort#3](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#3)]  
  
5.  创建以递增的顺序排序数组的 `parallel_bitonic_sort` 函数的重载版本。  
  
     [!CODE [concrt-parallel-bitonic-sort#4](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#4)]  
  
 `parallel_invoke` 算法通过对调用上下文执行一系列任务中的最后一项任务来减少开销。  例如在 `parallel_bitonic_sort` 函数中，第一个任务在单独的上下文中运行，而第二个任务则在调用上下文中运行。  
  
 [!CODE [concrt-parallel-bitonic-sort#5](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#5)]  
  
 下面的完整示例执行 bitonic 排序算法的序列化版本和并行版本。  此示例还会将执行每个计算所需的时间打印到控制台。  
  
 [!CODE [concrt-parallel-bitonic-sort#8](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#8)]  
  
 下例是四处理器计算机的输出结果。  
  
  **序列化的时间：4353**  
**并行时间：1248** \[[Top](#top)\]  
  
## 编译代码  
 若要编译代码，请复制代码并将其粘贴到 Visual Studio项目中或一个名为 `parallel-bitonic-sort.cpp` 的文件中，然后在 Visual Studio命令提示符窗口中运行以下命令。  
  
 **cl.exe \/EHsc parallel\-bitonic\-sort.cpp**  
  
## 可靠编程  
 此示例使用 `parallel_invoke` 算法而不是 [concurrency::task\_group](../Topic/task_group%20Class.md) 类，因为每个任务组的生存期均未超出函数的生存期。  建议您尽可能使用 `parallel_invoke`，因为它的执行开销比 `task group` 对象少，因此可使您编写性能更佳的代码。  
  
 仅当有足够的工作要做时，某些算法的并行版本的性能才会较佳。  例如，如果序列中有 500 个或更少的元素，则 `parallel_bitonic_merge` 函数将调用序列化版本 `bitonic_merge`。  您还可以根据工作量计划整体的排序策略。  例如，如果数组包含的项目少于 500 个，则使用快速排序算法的串行版本可能更为高效，如下面的示例所示：  
  
 [!CODE [concrt-parallel-bitonic-sort#9](../CodeSnippet/VS_Snippets_ConcRT/concrt-parallel-bitonic-sort#9)]  
  
 与使用任何并行算法一样，建议您根据需要分析和调整代码。  
  
## 请参阅  
 [任务并行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [parallel\_invoke 函数](../Topic/parallel_invoke%20Function.md)