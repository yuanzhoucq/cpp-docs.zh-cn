---
title: omp_set_nest_lock |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nest_lock OpenMP function
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e49a63fc4bc8d31583478ee6f61fe7b374bb9f0b
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691009"
---
# <a name="ompsetnestlock"></a>omp_set_nest_lock
块线程执行，直到锁可用。  
  
## <a name="syntax"></a>语法  
  
```  
void omp_set_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `lock`  
 类型的变量的[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)初始化与[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[3.2.3 omp_set_lock 和 omp_set_nest_lock 函数](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。  
  
## <a name="examples"></a>示例  
 请参阅[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)有关的使用示例`omp_set_nest_lock`。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)