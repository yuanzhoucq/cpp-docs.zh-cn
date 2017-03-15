---
title: "3.1.3 omp_get_max_threads Function | Microsoft Docs"
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
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.3 omp_get_max_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**omp\_get\_max\_threads** 函数返回确保至少具有与大线程数将可用于构成团队的整数，如果没有 **num\_threads** 子句的并行区域将只有在代码中遇到。  格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 以下表示在 **omp\_get\_max\_threads**的值的下限:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 请注意，因此，如果一个后续并行区域使用 **num\_threads** 子句请求线程的特定编号，在 **omp\_get\_max\_threads** 结果的下限的确保不长保存。  
  
 **omp\_get\_max\_threads** 函数的返回值可以使用动态分配所有线程的足够的存储在团队形成该后续并行区域。  
  
## 交叉引用:  
  
-   **omp\_get\_num\_threads** 功能，请参见中的第 37 页的 [第3.1.2部分](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 。  
  
-   **omp\_set\_num\_threads** 功能，请参见中的第 36 页的 [第3.1.1部分](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 。  
  
-   **omp\_set\_dynamic** 功能，请参见中的第 39 页的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。  
  
-   **num\_threads** 子句，请参见中的第 8. 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。