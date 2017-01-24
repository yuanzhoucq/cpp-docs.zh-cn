---
title: "OpenMP Functions | Microsoft Docs"
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
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OpenMP Functions
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供指向用于 OpenMP API 的功能。  
  
 OpenMP 标准的 Visual C\+\+ 实现包括以下功能。  
  
|功能|说明|  
|--------|--------|  
|[omp\_destroy\_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|Uninitializes 锁。|  
|[omp\_destroy\_nest\_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|Uninitializes 可套上的锁。|  
|[omp\_get\_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|返回一个值线程数可用在后续并行区域是否可以在运行时调整。|  
|[omp\_get\_max\_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|返回等于或大于线程数可用的整数，如果没有 [num\_threads](../../../parallel/openmp/reference/num-threads.md) 的并行区域在代码此时定义。|  
|[omp\_get\_nested](../../../parallel/openmp/reference/omp-get-nested.md)|返回一个值嵌套并行是否启用。|  
|[omp\_get\_num\_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|返回可用处理器的数目，则在函数调用时。|  
|[omp\_get\_num\_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|在并行区域返回线程的数量。|  
|[omp\_get\_thread\_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|返回对其线程团队中的线程的线程数。|  
|[omp\_get\_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|返回秒数。处理器时钟计时周期之间的。|  
|[omp\_get\_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|时间的秒返回一个值从少数 elapsed 点。|  
|[omp\_in\_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|返回非零，则调用从并行区域内。|  
|[omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)|初始化一个简单的锁。|  
|[omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|初始化锁。|  
|[omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|指示线程的数目可用在后续并行区域可以在运行时调整。|  
|[omp\_set\_lock](../../../parallel/openmp/reference/omp-set-lock.md)|阻塞线程执行，直至锁可用。|  
|[omp\_set\_nest\_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|阻塞线程执行，直至锁可用。|  
|[omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md)|使嵌套并行。|  
|[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|在后续并行区域设置线程数，因此，除非重写由 [num\_threads](../../../parallel/openmp/reference/num-threads.md) 子句。|  
|[omp\_test\_lock](../../../parallel/openmp/reference/omp-test-lock.md)|尝试设置锁定，但不阻塞线程上执行。|  
|[omp\_test\_nest\_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|尝试设置可套上的锁定，但不阻塞线程上执行。|  
|[omp\_unset\_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|释放锁。|  
|[omp\_unset\_nest\_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|释放可套上的锁。|  
  
## 请参阅  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)