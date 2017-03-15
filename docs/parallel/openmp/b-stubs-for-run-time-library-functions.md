---
title: "B. Stubs for Run-time Library Functions | Microsoft Docs"
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
ms.assetid: fdfdabe0-f678-4551-80d5-827b62354427
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# B. Stubs for Run-time Library Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本节提供有关在 OpenMP C 和 C\+\+ API 定义的运行库函数提供存根。  提供存根启用可移植性到不支持 OpenMP C 和 C\+\+ API 的平台。  在这些平台上，必须使用包含这些函数存根的库链接 OpenMP 程序。  存根功能，假设在 OpenMP 程序的指令被忽略。  因此，它们来模拟序列化的语义。  
  
> [!NOTE]
>  出现死锁功能的锁变量必须通过这些功能完全访问。  在用户程序不应初始化或修改它。  用户不应对 OpenMP C 和 C\+\+ 实现使用结构的假设根据该模式的实现锁定使用由存根功能。  
  
### 代码  
  
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