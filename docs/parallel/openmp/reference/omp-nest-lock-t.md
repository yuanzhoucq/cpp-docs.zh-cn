---
title: omp_nest_lock_t |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- omp_nest_lock_t OpenMP data type
ms.assetid: fceac9fb-96d2-42b0-af19-c9b078380618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c47581e2587ea7c82ff3b84ad41d0c83d1659b7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691737"
---
# <a name="ompnestlockt"></a>omp_nest_lock_t
一种保存有关锁的信息的以下部分： 是否锁定，并且可线程的标识的拥有锁和嵌套的计数。  
  
 以下函数使用**omp_nest_lock_t**:  
  
-   [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)  
  
-   [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)  
  
-   [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)  
  
-   [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)  
  
-   [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)  
  
 有关详细信息，请参阅[3.2 锁函数](../../../parallel/openmp/3-2-lock-functions.md)。  
  
## <a name="example"></a>示例  
 请参阅[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)有关的使用示例**omp_nest_lock_t**。  
  
## <a name="see-also"></a>请参阅  
 [数据类型](../../../parallel/openmp/reference/openmp-data-types.md)