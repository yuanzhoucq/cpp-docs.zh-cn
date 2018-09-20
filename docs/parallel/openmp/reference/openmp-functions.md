---
title: OpenMP 函数 |Microsoft Docs
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
ms.openlocfilehash: a5daa7737f63df437f31f349a85811befe0c8f5b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425595"
---
# <a name="openmp-functions"></a>OpenMP 函数

提供指向 OpenMP API 中使用的函数。

OpenMP 标准的 Visual c + + 实现包括以下函数。

|函数|描述|
|--------------|-----------------|
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|取消初始化锁。|
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|取消初始化可嵌套锁。|
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|返回一个值，该值指示是否后续并行区域中可用的线程数可以调整运行时。|
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|返回一个整数，如果无需并行区域可用的线程数大于或等于[num_threads](../../../parallel/openmp/reference/num-threads.md)此时在代码中定义。|
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|返回一个值，该值指示是否启用了嵌套并行度。|
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|返回调用函数时可用的处理器数。|
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|并行区域中返回线程的数。|
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|返回其线程团队中执行的线程的线程数。|
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|返回处理器时钟计时周期之间等待的秒数。|
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|返回从某一时刻已用的值以秒为单位的时间。|
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|返回非零，如果从并行区域内调用。|
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|初始化是简单的锁定。|
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|初始化一个锁。|
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|指示运行时可进行调整的后续并行区域中可用的线程数。|
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|块线程执行，直到锁可用。|
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|块线程执行，直到锁可用。|
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|启用嵌套并行度。|
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|在后续的并行区域设置的线程数，除非被重写[num_threads](../../../parallel/openmp/reference/num-threads.md)子句。|
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|尝试设置一个锁，但不会阻止线程执行。|
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|尝试设置可嵌套锁，但不会阻止线程执行。|
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|释放锁。|
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|释放可嵌套锁。|

## <a name="see-also"></a>请参阅

[库参考](../../../parallel/openmp/reference/openmp-library-reference.md)