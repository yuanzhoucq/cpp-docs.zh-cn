---
title: "omp_set_lock |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_lock
dev_langs: C++
helpviewer_keywords: omp_set_lock OpenMP function
ms.assetid: ded839cb-ca19-403f-8622-eb52ce512d31
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f2d63074ce989aa4bc96c829639386e3477ff523
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="ompsetlock"></a>omp_set_lock
块线程执行，直到锁可用。  
  
## <a name="syntax"></a>语法  
  
```  
void omp_set_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `lock`  
 类型的变量的[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md)初始化与[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[3.2.3 omp_set_lock 和 omp_set_nest_lock 函数](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。  
  
## <a name="examples"></a>示例  
 请参阅[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)有关的使用示例`omp_set_lock`。  
  
## <a name="see-also"></a>另请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)