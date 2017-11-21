---
title: "omp_test_nest_lock |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_test_nest_lock
dev_langs: C++
helpviewer_keywords: omp_test_nest_lock OpenMP function
ms.assetid: 4c909bbe-80e0-4100-aca6-d415d7dc5294
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 938a79bc164a940050dea126dc513d2f61cb9feb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="omptestnestlock"></a>omp_test_nest_lock
尝试设置 nestable 锁定，但不会阻止线程执行。  
  
## <a name="syntax"></a>语法  
  
```  
int omp_test_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `lock`  
 类型的变量的[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)初始化与[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)。  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[3.2.5 omp_test_lock 和 omp_test_nest_lock 函数](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。  
  
## <a name="example"></a>示例  
  
```  
// omp_test_nest_lock.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
omp_nest_lock_t nestable_lock;      
  
int main() {  
   omp_init_nest_lock(&nestable_lock);  
  
   #pragma omp parallel num_threads(4)  
   {  
      int tid = omp_get_thread_num();  
      while (!omp_test_nest_lock(&nestable_lock))  
         printf_s("Thread %d - failed to acquire nestable_lock\n",  
                tid);  
  
      printf_s("Thread %d - acquired nestable_lock\n", tid);  
  
      if (omp_test_nest_lock(&nestable_lock)) {  
         printf_s("Thread %d - acquired nestable_lock again\n",  
                tid);  
         printf_s("Thread %d - released nestable_lock\n",   
                tid);  
         omp_unset_nest_lock(&nestable_lock);  
      }  
  
      printf_s("Thread %d - released nestable_lock\n", tid);  
      omp_unset_nest_lock(&nestable_lock);  
   }  
  
   omp_destroy_nest_lock(&nestable_lock);  
}  
```  
  
```Output  
Thread 1 - acquired nestable_lock  
Thread 0 - failed to acquire nestable_lock  
Thread 1 - acquired nestable_lock again  
Thread 0 - failed to acquire nestable_lock  
Thread 1 - released nestable_lock  
Thread 0 - failed to acquire nestable_lock  
Thread 1 - released nestable_lock  
Thread 0 - failed to acquire nestable_lock  
Thread 3 - acquired nestable_lock  
Thread 0 - failed to acquire nestable_lock  
Thread 3 - acquired nestable_lock again  
Thread 0 - failed to acquire nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 3 - released nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 3 - released nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 0 - acquired nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 0 - acquired nestable_lock again  
Thread 2 - failed to acquire nestable_lock  
Thread 0 - released nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 0 - released nestable_lock  
Thread 2 - failed to acquire nestable_lock  
Thread 2 - acquired nestable_lock  
Thread 2 - acquired nestable_lock again  
Thread 2 - released nestable_lock  
Thread 2 - released nestable_lock  
```  
  
## <a name="see-also"></a>另请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)