---
title: A.25   copyprivate 数据特性子句示例
ms.date: 11/04/2016
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
ms.openlocfilehash: 6c3c174780023f17cc2aa47a54bff14fccf99306
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493881"
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25   copyprivate 数据特性子句示例

**示例 1:** `copyprivate`子句 ([部分 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md)第 32 页上) 可用于广播由单线程直接向私有变量在其他线程中的所有实例获取的值。

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

如果例行*init*称为从串行区域，其行为不影响通过指令的存在。 在调用*get_values*例程已执行由一个线程，没有线程直到指定的专用对象使构造， *b*， *x*，并*y*中所有线程变得与定义为具有读取的值。

**示例 2:** 与前面的示例，假设必须由特定线程，说的主线程执行读取。 在这种情况下，`copyprivate`子句不能用于执行广播直接，但它可用于提供对临时共享对象的访问。

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

**示例 3:** 假设并行区域内所需的锁对象的数目不能轻松地确定之前输入它。 `copyprivate`子句可用于提供对该并行区域内分配的共享的锁对象的访问。

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