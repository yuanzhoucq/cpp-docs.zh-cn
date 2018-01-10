---
title: "B. 运行时库函数的存根 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fdfdabe0-f678-4551-80d5-827b62354427
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 733a7cacebfcad6702d471425de7b617a241884f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="b-stubs-for-run-time-library-functions"></a>B. 运行时库函数的存根
本部分提供有关在 OpenMP C 和 c + + API 中定义的运行时库函数存根 （stub）。 存根 （stub） 用于启用到 OpenMP C 和 c + + API 不支持的平台的可移植性。 在这些平台上，必须使用包含这些存根 （stub） 函数的库链接 OpenMP 程序。 存根 （stub） 函数假设 OpenMP 程序中的指令将被忽略。 在这种情况下，它们模拟串行语义。  
  
> [!NOTE]
>  将出现在锁定函数的锁定变量必须以独占方式通过这些函数来访问。 它不应初始化或以其他方式修改在用户程序中。 用户不应假设 OpenMP C 和 c + + 实现用于实现基于使用存根 （stub） 函数的方案的锁的机制。  
  
### <a name="code"></a>代码  
  
```  
#include <stdio.h>  
#include <stdlib.h>  
#include "omp.h"  
#ifdef __cplusplus  
extern "C" {  
#endif  
  
void omp_set_num_threads(int num_threads)  
{  
}  
int omp_get_num_threads(void)  
{  
    return 1;  
}  
int omp_get_max_threads(void)  
{  
    return 1;  
}  
int omp_get_thread_num(void)  
{  
    return 0;  
}  
int omp_get_num_procs(void)  
{  
    return 1;  
}  
void omp_set_dynamic(int dynamic_threads)  
{  
}  
int omp_get_dynamic(void)  
{  
    return 0;  
}  
int omp_in_parallel(void)  
{  
    return 0;  
}  
void omp_set_nested(int nested)  
{  
}  
int omp_get_nested(void)  
{  
    return 0;  
}  
enum {UNLOCKED = -1, INIT, LOCKED};  
void omp_init_lock(omp_lock_t *lock)  
{  
    *lock = UNLOCKED;  
}  
void omp_destroy_lock(omp_lock_t *lock)  
{  
    *lock = INIT;  
}  
void omp_set_lock(omp_lock_t *lock)  
{  
    if (*lock == UNLOCKED)   
    {  
        *lock = LOCKED;  
    }   
    else   
        if (*lock == LOCKED)   
        {  
         fprintf_s(stderr, "error: deadlock in using lock variable\n");  
         exit(1);  
        } else {  
         fprintf_s(stderr, "error: lock not initialized\n");  
         exit(1);  
        }  
}  
  
void omp_unset_lock(omp_lock_t *lock)  
{  
    if (*lock == LOCKED)   
    {  
        *lock = UNLOCKED;  
    }   
    else   
        if (*lock == UNLOCKED)   
        {  
            fprintf_s(stderr, "error: lock not set\n");  
            exit(1);  
        } else {  
            fprintf_s(stderr, "error: lock not initialized\n");  
            exit(1);  
        }  
}  
  
int omp_test_lock(omp_lock_t *lock)  
{  
    if (*lock == UNLOCKED)   
    {  
        *lock = LOCKED;  
        return 1;  
    } else if (*lock == LOCKED) {  
        return 0;  
    } else {  
        fprintf_s(stderr, "error: lock not initialized\n");  
        exit(1);  
    }  
}  
  
#ifndef OMP_NEST_LOCK_T  
typedef struct {  // This really belongs in omp.h   
    int owner;  
    int count;  
} omp_nest_lock_t;  
#endif  
enum {MASTER = 0};  
void omp_init_nest_lock(omp_nest_lock_t *lock)  
{  
    lock->owner = UNLOCKED;  
    lock->count = 0;  
}  
void omp_destroy_nest_lock(omp_nest_lock_t *lock)  
{  
    lock->owner = UNLOCKED;  
    lock->count = UNLOCKED;  
}  
  
void omp_set_nest_lock(omp_nest_lock_t *lock)  
{  
    if (lock->owner == MASTER && lock->count >= 1)   
    {  
        lock->count++;  
    } else   
        if (lock->owner == UNLOCKED && lock->count == 0)   
        {  
            lock->owner = MASTER;  
            lock->count = 1;  
        } else   
        {  
       fprintf_s(stderr, "error: lock corrupted or not initialized\n");  
         exit(1);  
    }  
}  
  
void omp_unset_nest_lock(omp_nest_lock_t *lock)  
{  
    if (lock->owner == MASTER && lock->count >= 1)   
    {  
        lock->count--;  
        if (lock->count == 0)   
        {  
            lock->owner = UNLOCKED;  
        }  
    } else   
        if (lock->owner == UNLOCKED && lock->count == 0)   
        {  
            fprintf_s(stderr, "error: lock not set\n");  
            exit(1);  
        } else   
        {  
       fprintf_s(stderr, "error: lock corrupted or not initialized\n");  
       exit(1);  
    }  
}  
  
int omp_test_nest_lock(omp_nest_lock_t *lock)  
{  
    omp_set_nest_lock(lock);  
    return lock->count;  
}  
  
double omp_get_wtime(void)  
{  
    // This function does not provide a working  
    // wallclock timer. Replace it with a version  
    // customized for the target machine.  
    return 0.0;  
}  
  
double omp_get_wtick(void)  
{  
    // This function does not provide a working  
    // clock tick function. Replace it with  
    // a version customized for the target machine.  
    return 365. * 86400.;  
}  
  
#ifdef __cplusplus  
}  
#endif  
```