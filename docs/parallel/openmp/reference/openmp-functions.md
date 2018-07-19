---
title: OpenMP 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a39fe44ff053a2e49a1067d0af071353e0a50ece
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693271"
---
# <a name="openmp-functions"></a>OpenMP 函数
提供指向 OpenMP API 中使用的函数。  
  
 标准 OpenMP 的 Visual c + + 实现包括以下函数。  
  
|函数|描述|  
|--------------|-----------------|  
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|取消初始化锁。|  
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|取消初始化 nestable 锁。|  
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|返回一个值，该值指示是否可以由运行时调整后续并行区域中的可用线程数。|  
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|返回一个整数，等于或大于如果而无需并行区域可用的线程数[num_threads](../../../parallel/openmp/reference/num-threads.md)在该点在代码中定义。|  
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|返回一个值，该值指示是否启用了嵌套并行度。|  
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|返回调用函数时都可用的处理器数。|  
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|并行区域中返回线程的数。|  
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|返回在其线程团队中的线程正在执行线程的数。|  
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|返回处理器时钟计时周期之间的秒数。|  
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|返回从某一时刻已用时间的秒中的值。|  
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|返回非零，如果从调用并行区域内。|  
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|初始化一个简单的锁定。|  
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|初始化锁。|  
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|指示运行时可以进行调整了后续并行区域中的可用线程数。|  
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|块线程执行，直到锁可用。|  
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|块线程执行，直到锁可用。|  
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|启用嵌套并行度。|  
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|在后续的并行区域设置的线程数，除非通过重写[num_threads](../../../parallel/openmp/reference/num-threads.md)子句。|  
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|尝试设置锁，但不会阻止线程执行。|  
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|尝试设置 nestable 锁定，但不会阻止线程执行。|  
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|释放锁。|  
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|释放 nestable 锁定。|  
  
## <a name="see-also"></a>请参阅  
 [库参考](../../../parallel/openmp/reference/openmp-library-reference.md)