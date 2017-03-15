---
title: "E. Implementation-Defined Behaviors in OpenMP C/C++ | Microsoft Docs"
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
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# E. Implementation-Defined Behaviors in OpenMP C/C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此附录摘要中描述为 “实现定义”此 API 的行为。  每个行为交叉引用回其母版规范的说明。  
  
## 备注  
 实现在这些情况下定义和文档其行为，但是，此列表可能无法完成。  
  
-   **线程的数量:** ，如果并行区域遇到，当线程数动态调整禁用了和并行区域请求的线程的数目超过该数字为由运行时系统可以提供，程序的行为实现中定义 \(请参见第 9 页。\)  
  
     在 Visual C\+\+ 中，非嵌套并行区域的，则将提供 64 个线程 \(最大\)。  
  
-   **处理器数目:** 实际承载线程的实际处理器数在任何给定时间实现中定义 \(请参见第 10 页。\)  
  
     在 Visual C\+\+ 中，此数字不是常数和由操作系统的控制。  
  
-   **创建线程团队:** 执行嵌套并行区域线程数。团队的实现中定义。\(请参见第 10 页。\)  
  
     在 Visual C\+\+ 中，操作系统取决于。  
  
-   **计划 \(运行时\):** 有关计划决策将延迟到运行时。  计划类型和块范围可以选择在运行时设置 `OMP_SCHEDULE` 环境变量。  如果此未设置环境变量，生成计划实现中定义 \(请参见第 13 页\)。  
  
     在 Visual C\+\+ 中，时间表类型是 `static` 没有块范围。  
  
-   在没有计划子句中**默认计划:** ，这个默认计划实现中定义 \(请参见第 13 页\)。  
  
     在 Visual C\+\+ 中，这个默认计划类型是 `static` 没有块范围。  
  
-   **基本:** 它实现中定义的实现是否将具有相同的唯一名称的 **重要** 指令替换所有 `atomic` 指令 \(请参见第 20 页\)。  
  
     在 Visual C\+\+，因此，如果 [atomic](../../parallel/openmp/reference/atomic.md) 修改的数据不在自然对齐，或者长度为 1 个或 2 个字节满足该属性的任何基本操作将使用一个临界区。  否则，将不使用临界区。  
  
-   **omp\_get\_num\_threads:** ，如果线程的数目尚未由用户显式设置时，默认实现的定义 \(参见在第 37 页\) 的第 9 页和 [第3.1.2部分](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 。  
  
     在 Visual C\+\+ 中，线程的默认数量与处理器的数目相等。  
  
-   **omp\_set\_dynamic:** 动态线程调整的默认实现的定义 \(参见在第 39 页\) 的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。  
  
     在 Visual C\+\+ 中，默认值为 `FALSE`。  
  
-   **omp\_set\_nested:** ，当嵌套并行启用时，用于执行的线程的数目嵌套并行区域实现中定义 \(请参见在第 40 页\) 的 [第3.1.9部分](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 。  
  
     在 Visual C\+\+ 中，操作系统依靠线程的数量。  
  
-   `OMP_SCHEDULE` 环境变量:此环境变量的默认实现的定义 \(参见在第 48 页\) 的 [第4.1部分](../../parallel/openmp/4-1-omp-schedule.md) 。  
  
     在 Visual C\+\+ 中，时间表类型是 `static` 没有块范围。  
  
-   `OMP_NUM_THREADS` 环境变量:如果值不为 `OMP_NUM_THREADS` 环境变量指定，或者，如果指定的值不是正整数，或者，如果值大于线程的最大数量大于系统可以支持，使用线程的数量实现中定义 \(请参见在第 48 页\) 的 [第4.2部分](../../parallel/openmp/4-2-omp-num-threads.md) 。  
  
     在 Visual C\+\+ 中，; 如果指定的值为零或更小，线程的数量与处理器的数目相等。  如果值大于 64，线程数为 64。  
  
-   `OMP_DYNAMIC` 环境变量:默认实现的定义 \(参见在第 49 页\) 的 [第4.3部分](../../parallel/openmp/4-3-omp-dynamic.md) 。  
  
     在 Visual C\+\+ 中，默认值为 `FALSE`。