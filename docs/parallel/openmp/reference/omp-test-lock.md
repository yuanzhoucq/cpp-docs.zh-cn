---
title: "omp_test_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_test_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_test_lock OpenMP function"
ms.assetid: 314ca85e-0749-4c16-800f-b0f36fed256d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# omp_test_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

尝试设置锁定，但不阻塞线程上执行。  
  
## 语法  
  
```  
int omp_test_lock(  
   omp_lock_t *lock  
);  
```  
  
## 备注  
 其中，  
  
 `lock`  
 初始化 [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)类型 [omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md) 的变量。  
  
## 备注  
 有关更多信息，请参见 [3.2.5 omp\_test\_lock and omp\_test\_nest\_lock Functions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)。  
  
## 示例  
  
```  
// omp_test_lock.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
omp_lock_t simple_lock;                   
  
int main() {  
    omp_init_lock(&simple_lock);  
  
    #pragma omp parallel num_threads(4)  
    {  
        int tid = omp_get_thread_num();  
  
        while (!omp_test_lock(&simple_lock))  
            printf_s("Thread %d - failed to acquire simple_lock\n",  
                     tid);  
  
        printf_s("Thread %d - acquired simple_lock\n", tid);  
  
        printf_s("Thread %d - released simple_lock\n", tid);  
        omp_unset_lock(&simple_lock);  
    }  
  
    omp_destroy_lock(&simple_lock);  
}  
```  
  
  **线程 1 \- 获取的 simple\_lock**  
**线程 1 \- 释放的 simple\_lock**  
**0 \- 未能的线程获取 simple\_lock**  
**3 \- 未能的线程获取 simple\_lock**  
**0 \- 未能的线程获取 simple\_lock**  
**3 \- 未能的线程获取 simple\_lock**  
**线程 2 \- 获取的 simple\_lock**  
**0 \- 未能的线程获取 simple\_lock**  
**3 \- 未能的线程获取 simple\_lock**  
**0 \- 未能的线程获取 simple\_lock**  
**3 \- 未能的线程获取 simple\_lock**  
**线程 2 \- 释放的 simple\_lock**  
**0 \- 未能的线程获取 simple\_lock**  
**3 \- 未能的线程获取 simple\_lock**  
**线程 0 \- 获取的 simple\_lock**  
**3 \- 未能的线程获取 simple\_lock**  
**线程 0 \- 释放的 simple\_lock**  
**3 \- 未能的线程获取 simple\_lock**  
**线程 3 \- 获取的 simple\_lock**  
**线程 3 \- 释放的 simple\_lock**   
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)