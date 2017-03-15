---
title: "3.1.2 omp_get_num_threads Function | Microsoft Docs"
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
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.2 omp_get_num_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**omp\_get\_num\_threads** 函数返回当前线程的数目在执行调用的并行区域的团队。  格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_num_threads(void);  
```  
  
 **num\_threads** 子句、 **omp\_set\_num\_threads** 功能和 **OMP\_NUM\_THREADS** 环境变量控制线程数。团队。  
  
 如果线程的数目尚未由用户显式设置，默认实现中定义。  此函数绑定到最接近的封闭 **并行** 指令。  如果调用从程序的一个序列化的部分，或从序列化的嵌套并行区域，此函数返回 1。  
  
## 交叉引用:  
  
-   **OMP\_NUM\_THREADS** 环境变量，请参见中的第 48 页的 [第4.2部分](../../parallel/openmp/4-2-omp-num-threads.md) 。  
  
-   **num\_threads** 子句，请参见中的第 8. 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。  
  
-   **并行** 构造，请参见中的第 8. 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。