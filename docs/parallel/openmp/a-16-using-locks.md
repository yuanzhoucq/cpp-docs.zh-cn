---
title: "A.16   Using Locks | Microsoft Docs"
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
ms.assetid: 873bf32b-6cfe-4ce1-b994-bef80b50f399
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.16   Using Locks
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在下面的示例中， \(对于第 41 页\) 的 [第3.2部分](../../parallel/openmp/3-2-lock-functions.md) 请注意到死锁函数的参数应具有类型，`omp_lock_t`，并且不需要刷新它。  死锁功能会导致线程空闲，当等待项到第一个临界区，但是，时执行其他工作，当等待项到第二时。  `omp_set_lock` 功能块，但是， `omp_test_lock` 功能，不允许在跳过的工作 \(\) 已完成。  
  
## 示例  
  
### 代码  
  
```  
// omp_using_locks.c  
// compile with: /openmp /c  
#include <stdio.h>  
#include <omp.h>  
  
void work(int);  
void skip(int);  
  
int main() {  
   omp_lock_t lck;  
   int id;  
  
   omp_init_lock(&lck);  
   #pragma omp parallel shared(lck) private(id)  
   {  
      id = omp_get_thread_num();  
  
      omp_set_lock(&lck);  
      printf_s("My thread id is %d.\n", id);  
  
      // only one thread at a time can execute this printf  
      omp_unset_lock(&lck);  
  
      while (! omp_test_lock(&lck)) {  
         skip(id);   // we do not yet have the lock,  
                     // so we must do something else   
      }  
      work(id);     // we now have the lock  
                    // and can do the work   
      omp_unset_lock(&lck);  
   }  
   omp_destroy_lock(&lck);  
}  
```