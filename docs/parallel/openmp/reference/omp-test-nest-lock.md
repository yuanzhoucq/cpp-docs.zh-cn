---
title: "omp_test_nest_lock | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_test_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_test_nest_lock OpenMP function"
ms.assetid: 4c909bbe-80e0-4100-aca6-d415d7dc5294
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_test_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

尝试设置可套上的锁定，但不阻塞线程上执行。  
  
## 语法  
  
```  
int omp_test_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## 备注  
 其中，  
  
 `lock`  
 初始化 [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)类型 [omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) 的变量。  
  
## 备注  
 有关更多信息，请参见 [3.2.5 omp\_test\_lock and omp\_test\_nest\_lock Functions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。  
  
## 示例  
  
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
  
  **线程 1 \- 获取的 nestable\_lock**  
**0 \- 未能的线程获取 nestable\_lock**  
**线程 1 \- 获取的 nestable\_lock 再次**  
**0 \- 未能的线程获取 nestable\_lock**  
**线程 1 \- 释放的 nestable\_lock**  
**0 \- 未能的线程获取 nestable\_lock**  
**线程 1 \- 释放的 nestable\_lock**  
**0 \- 未能的线程获取 nestable\_lock**  
**线程 3 \- 获取的 nestable\_lock**  
**0 \- 未能的线程获取 nestable\_lock**  
**线程 3 \- 获取的 nestable\_lock 再次**  
**0 \- 未能的线程获取 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**线程 3 \- 释放的 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**线程 3 \- 释放的 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**线程 0 \- 获取的 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**线程 0 \- 获取的 nestable\_lock 再次**  
**2 \- 未能的线程获取 nestable\_lock**  
**线程 0 \- 释放的 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**线程 0 \- 释放的 nestable\_lock**  
**2 \- 未能的线程获取 nestable\_lock**  
**线程 2 \- 获取的 nestable\_lock**  
**线程 2 \- 获取的 nestable\_lock 再次**  
**线程 2 \- 释放的 nestable\_lock**  
**线程 2 \- 释放的 nestable\_lock**   
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)