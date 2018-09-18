---
title: omp_destroy_lock |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_lock OpenMP function
ms.assetid: b73ab036-b76f-4e42-82ff-c89db2edf7c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c24f09bbad550633c68c403c89362a293265111
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019900"
---
# <a name="ompdestroylock"></a>omp_destroy_lock
取消初始化锁。  
  
## <a name="syntax"></a>语法  
  
```  
void omp_destroy_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>参数
  
*lock*<br/>
类型的变量[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md)与初始化[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函数](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。  
  
## <a name="example"></a>示例  
 请参阅[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)有关的使用示例`omp_destroy_lock`。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)