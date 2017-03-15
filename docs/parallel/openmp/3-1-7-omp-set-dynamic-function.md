---
title: "3.1.7 omp_set_dynamic Function | Microsoft Docs"
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
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.7 omp_set_dynamic Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**omp\_set\_dynamic** 功能启用或禁用线程数动态调整可用于并行区域的执行。  格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 如果 *dynamic\_threads* 计算为非零值，对于执行后续并行区域使用线程的数目可能由种运行时环境自动调整以最佳利用系统资源。  因此，用户指定的线程的数目最大线程计数。  线程数在执行并行区域的团队保持固定为该并行区域的持续时间以及由 **omp\_get\_num\_threads** 函数报告。  
  
 如果 *dynamic\_threads* 计算结果为 0，动态调整被禁用。  
  
 该函数具有中描述的效果顶部，在调用从 **omp\_in\_parallel** 函数返回零程序的一部分。  如果从 **omp\_in\_parallel** 函数返回非零值程序的一部分调用，此功能的行为未定义。  
  
 为 **omp\_set\_dynamic** 的调用在 **OMP\_DYNAMIC** 环境变量的优先级。  
  
 线程的动态调整的默认实现中定义。  因此，依赖于线程的特定数字正确执行的用户代码应显式禁用动态线程。  不需要实现能够动态地调整线程数，但是，要求他们提供接口以便支持在所有平台上的可移植性。  
  
## 交叉引用:  
  
-   **omp\_get\_num\_threads** 功能，请参见中的第 37 页的 [第3.1.2部分](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 。  
  
-   **OMP\_DYNAMIC** 环境变量，请参见中的第 49 页的 [第4.3部分](../../parallel/openmp/4-3-omp-dynamic.md) 。  
  
-   **omp\_in\_parallel** 功能，请参见中的第 38 页的 [第3.1.6部分](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) 。