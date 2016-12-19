---
title: "A.25   Examples of the copyprivate Data Attribute Clause | Microsoft Docs"
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
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.25   Examples of the copyprivate Data Attribute Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**示例 1:** `copyprivate` 子句 \(在第 32 页\) 的[第2.7.2.8部分](../../parallel/openmp/2-7-2-8-copyprivate.md) 可用于广播个线程访问的值直接对私有变量的所有实例在其他线程上。  
  
```  
float x, y;  
#pragma omp threadprivate(x, y)  
  
void init( )   
{  
    float a;  
    float b;  
  
    #pragma omp single copyprivate(a,b,x,y)  
    {  
        get_values(a,b,x,y);  
    }  
  
    use_values(a, b, x, y);  
}  
```  
  
 如果实例 *init* 从一个序列化的区域调用，其行为不受指令的显示效果。  在对 *get\_values* 实例的调用由一个线程后执行了，线程不保留直到 *中*指定的私有对象的构造， *b*， *x*，因此，所有的 *y* 线程变为定义与读取的值。  
  
 与上面\) 的**示例 2:** ，假定必须由特定线程上执行读取的，指出主线程。  在这种情况下， `copyprivate` 子句不能用于直接执行广播的，但是，它可用于提供对临时共享对象。  
  
```  
float read_next( )   
{  
    float * tmp;  
    float return_val;  
  
    #pragma omp single copyprivate(tmp)  
    {  
        tmp = (float *) malloc(sizeof(float));  
    }  
  
    #pragma omp master  
    {  
        get_float( tmp );  
    }  
  
    #pragma omp barrier  
    return_val = *tmp;  
    #pragma omp barrier  
  
    #pragma omp single  
    {  
       free(tmp);  
    }  
  
    return return_val;  
}  
```  
  
 **示例 3:** 假定锁定对象数在并行区域内所需的无法轻松确定中输入之前。  `copyprivate` 子句来提供对该并行区域中分配的共享锁定对象。  
  
```  
#include <omp.h>  
  
omp_lock_t *new_lock()  
{  
    omp_lock_t *lock_ptr;  
  
    #pragma omp single copyprivate(lock_ptr)  
    {  
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));  
        omp_init_lock( lock_ptr );  
    }  
  
    return lock_ptr;  
}  
```