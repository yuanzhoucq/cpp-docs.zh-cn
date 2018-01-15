---
title: "omp_nest_lock_t |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_nest_lock_t
dev_langs: C++
helpviewer_keywords: omp_nest_lock_t OpenMP data type
ms.assetid: fceac9fb-96d2-42b0-af19-c9b078380618
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bbf62ae43ed1ebd0d28157b03fabace9b2b9d18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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