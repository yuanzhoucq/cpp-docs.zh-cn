---
title: "Copyprivate 数据属性子句的 A.25 示例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cdf7598e00bab72966fe79454567b0a59dcbaae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25   copyprivate 数据特性子句示例
**示例 1:** `copyprivate`子句 ([部分 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)在页上 32) 可以用于广播获取通过单个线程直接到其他线程中的私有变量的所有实例的值。  
  
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
  
 如果例程*init*称为从串行区域中，其行为不受指令的存在。 在调用后*get_values*例程已由一个线程中执行，无需对线程离开之前指定的私有对象的构造， *b*， *x*，和*y*中所有线程变得定义为具有读取的值。  
  
 **示例 2:**与前面的示例中，假设必须由特定线程，即主线程执行读取。 在这种情况下，`copyprivate`子句不能用于执行广播直接，但它可以用于提供对共享的临时对象的访问。  
  
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
  
 **示例 3:**假设之前输入中的并行区域内所需的锁对象的数目不能方便地确定。 `copyprivate`子句可以用于提供对该并行区域内分配的共享的锁对象的访问。  
  
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