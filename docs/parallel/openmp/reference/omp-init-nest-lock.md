---
title: "omp_init_nest_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_init_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_init_nest_lock OpenMP function"
ms.assetid: cf749ec5-de78-4186-9588-ac7c42b02463
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# omp_init_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

初始化锁。  
  
## 语法  
  
```  
void omp_init_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## 备注  
 其中，  
  
 `lock`  
 类型 [omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)的变量。  
  
## 备注  
 嵌套的计数则最初为零。  
  
 有关更多信息，请参见 [3.2.1 omp\_init\_lock and omp\_init\_nest\_lock Functions](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)。  
  
## 示例  
  
```  
// omp_init_nest_lock.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
omp_nest_lock_t my_lock;  
  
void Test() {  
   int tid = omp_get_thread_num( );  
   omp_set_nest_lock(&my_lock);  
   printf_s("Thread %d - starting nested locked region\n", tid);  
   printf_s("Thread %d - ending nested locked region\n", tid);  
   omp_unset_nest_lock(&my_lock);  
}  
  
int main() {  
   omp_init_nest_lock(&my_lock);  
  
   #pragma omp parallel num_threads(4)  
   {  
      int i, j;  
  
      for (i = 0; i < 5; ++i) {  
         omp_set_nest_lock(&my_lock);  
            if (i % 3)   
               Test();  
            omp_unset_nest_lock(&my_lock);  
        }  
    }  
  
    omp_destroy_nest_lock(&my_lock);  
}  
```  
  
  **线程 0 \- 启动嵌套锁定的区域**  
**线程 0 \- 结尾嵌套锁定的区域**  
**线程 0 \- 启动嵌套锁定的区域**  
**线程 0 \- 结尾嵌套锁定的区域**  
**线程 3 \- 启动嵌套锁定的区域**  
**线程 3 \- 结尾嵌套锁定的区域**  
**线程 3 \- 启动嵌套锁定的区域**  
**线程 3 \- 结尾嵌套锁定的区域**  
**线程 3 \- 启动嵌套锁定的区域**  
**线程 3 \- 结尾嵌套锁定的区域**  
**线程 2 \- 启动嵌套锁定的区域**  
**线程 2 \- 结尾嵌套锁定的区域**  
**线程 2 \- 启动嵌套锁定的区域**  
**线程 2 \- 结尾嵌套锁定的区域**  
**线程 2 \- 启动嵌套锁定的区域**  
**线程 2 \- 结尾嵌套锁定的区域**  
**线程 1 \- 启动嵌套锁定的区域**  
**线程 1 \- 结尾嵌套锁定的区域**  
**线程 1 \- 启动嵌套锁定的区域**  
**线程 1 \- 结尾嵌套锁定的区域**  
**线程 1 \- 启动嵌套锁定的区域**  
**线程 1 \- 结尾嵌套锁定的区域**  
**线程 0 \- 启动嵌套锁定的区域**  
**线程 0 \- 结尾嵌套锁定的区域**   
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)