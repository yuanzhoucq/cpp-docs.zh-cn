---
title: "E. 实现定义的行为在 OpenMP C/c + + |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe890248ad2eb3bcee024bf12ccf4039484e7b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. 实现定义的行为在 OpenMP C/c + +
本附录总结了描述为"实现定义"此 API 中的行为。  每个行为是交叉引用回主要规范中的说明。  
  
## <a name="remarks"></a>备注  
 实现时需要定义并记录在这些情况下，其行为，但此列表可能不完整。  
  
-   **线程数：**如果禁用了动态调整的线程数，而为并行区域请求的线程数超过了运行时系统可以提供的行为的号遇到并行区域该程序是实现定义的 （请参阅第 9 页）。  
  
     在 Visual c + +，对于非嵌套并行区域中，64 个线程 （最大值） 将提供。  
  
-   **处理器数：**实际承载在任何给定时间的线程的物理处理器的数目是实现定义的 （请参阅页面 10）。  
  
     Visual c + + 中此号码不是常量，并由操作系统控制。  
  
-   **创建的线程的团队：**是实现定义的团队执行嵌套并行区域中的线程数。 (请参阅页面 10）。  
  
     在 Visual c + +，这是由操作系统确定的。  
  
-   **schedule （runtime):**有关计划被推迟到运行时的决策。 通过设置，可以在运行时选择的计划类型和区块大小`OMP_SCHEDULE`环境变量。 如果未设置此环境变量，生成的计划是实现定义的 （请参阅第 13 页）。  
  
     在 Visual c + +，计划类型是`static`与任何块区大小。  
  
-   **默认计划：**在没有计划子句的情况下，默认计划是实现定义的 （请参阅第 13 页）。  
  
     在 Visual c + +，默认计划类型是`static`与任何块区大小。  
  
-   **原子：**它是实现定义是否实现替换所有`atomic`指令与**关键**具有相同的唯一名称 （请参阅页 20） 的指令。  
  
     在 Visual c + +，如果数据来修改[原子](../../parallel/openmp/reference/atomic.md)不在自然对齐或如果它是 1 或 2 个字节长所有满足该属性的原子操作将使用一个关键部分。 否则，将不使用临界区。  
  
-   **omp_get_num_threads:**的线程数具有未显式设置用户，如果默认值是实现定义的 (请参阅第 9，页和[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)在页上 37)。  
  
     Visual c + + 中的默认线程数等于处理器数。  
  
-   **omp_set_dynamic:**动态线程调整的默认值是实现定义 (请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上)。  
  
     在 Visual c + +，默认值是`FALSE`。  
  
-   **omp_set_nested:**时启用了嵌套并行机制，用于执行嵌套并行区域的线程数是实现定义的 (请参阅[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上)。  
  
     Visual c + + 中的线程数是由操作系统确定的。  
  
-   `OMP_SCHEDULE`环境变量： 此环境变量的默认值是实现定义的 (请参阅[第 4.1 节](../../parallel/openmp/4-1-omp-schedule.md)在页上 48)。  
  
     在 Visual c + +，计划类型是`static`与任何块区大小。  
  
-   `OMP_NUM_THREADS`环境变量： 如果为不指定任何值`OMP_NUM_THREADS`环境变量，或如果指定的值不是一个正整数，或如果值大于最大的系统可以支持的线程数，是要使用的线程数实现定义 (请参阅[部分 4.2](../../parallel/openmp/4-2-omp-num-threads.md)在页上 48)。  
  
     在 Visual c + + 中，如果指定值为零或更短，线程数等于处理器数。  如果值大于 64，线程数为 64。  
  
-   `OMP_DYNAMIC`环境变量： 是实现定义的默认值 (请参阅[部分 4.3](../../parallel/openmp/4-3-omp-dynamic.md)在页上 49)。  
  
     在 Visual c + +，默认值是`FALSE`。