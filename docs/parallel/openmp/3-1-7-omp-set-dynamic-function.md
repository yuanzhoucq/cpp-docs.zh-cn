---
title: "3.1.7 omp_set_dynamic 函数 |Microsoft 文档"
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
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 87cdd627dd01697fa3d3718a2dc769f4017630a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic 函数
**Omp_set_dynamic**函数启用或禁用动态调整可用的并行区域执行的线程数。 格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_dynamic(int dynamic_threads);  
```  
  
 如果*dynamic_threads*计算结果可能由运行时环境，以最大程度利用系统资源为非零值，用于执行后续的并行区域的线程数会自动调整。 因此，由用户指定的线程数是最大线程计数。 执行并行区域团队中的线程数该并行区域的持续时间内保持固定，并由报告**omp_get_num_threads**函数。  
  
 如果*dynamic_threads*计算结果为 0，禁用动态调整。  
  
 此函数具有从一部分的程序中调用时，上面所述的效果其中**omp_in_parallel**函数将返回零。 如果它从一部分的程序调用其中**omp_in_parallel**函数将返回一个非零值，此函数的行为是不确定。  
  
 调用**omp_set_dynamic**的优先级高于**OMP_DYNAMIC**环境变量。  
  
 线程动态调整默认值为实现定义。 因此，取决于特定数量的正确的执行线程的用户代码应显式禁用动态线程。 实现不需要使你能够动态调整的线程数，但需要它们来提供接口以支持跨所有平台进行移植。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **omp_get_num_threads**函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)在页上 37。  
  
-   **OMP_DYNAMIC**环境变量，请参阅[部分 4.3](../../parallel/openmp/4-3-omp-dynamic.md)页 49 上。  
  
-   **omp_in_parallel**函数中，请参阅[部分 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)在第 38 页上。