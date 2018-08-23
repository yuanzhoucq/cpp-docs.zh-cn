---
title: omp_unset_lock |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_lock OpenMP function
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 243ff6d2336d3e293d009f82ba4a39243e076f94
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690682"
---
# <a name="ompunsetlock"></a>omp_unset_lock
释放锁。  
  
## <a name="syntax"></a>语法  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `lock`  
 类型的变量的[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md)初始化与[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)、 所拥有的线程和函数中执行。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。  
  
## <a name="example"></a>示例  
 请参阅[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)有关的使用示例`omp_unset_lock`。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)