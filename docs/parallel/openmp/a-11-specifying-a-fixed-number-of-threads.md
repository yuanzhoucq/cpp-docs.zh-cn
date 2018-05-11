---
title: 指定固定的数量的线程的 A.11 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71d09c470b76b61c6737566f7833334aeec6c63a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   指定固定数目的线程
某些程序依赖于固定、 预先指定的正确执行的线程数。  由于线程数的动态调整的默认设置是实现定义，此类程序可以选择关闭动态线程功能和设置显式要确保可移植性的线程数。 下面的示例演示如何执行此操作使用`omp_set_dynamic`([部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上)，和`omp_set_num_threads`([部分 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)在页上 36):  
  
```  
omp_set_dynamic(0);  
omp_set_num_threads(16);  
#pragma omp parallel shared(x, npoints) private(iam, ipoints)  
{  
    if (omp_get_num_threads() != 16)   
      abort();  
    iam = omp_get_thread_num();  
    ipoints = npoints/16;  
    do_by_16(x, iam, ipoints);  
}  
```  
  
 在此示例中，程序才会执行正确由 16 线程执行。 如果实现是不能够支持 16 线程，此示例的行为是实现定义的。  
  
 请注意，在并行区域，而不考虑动态的线程数设置过程中执行并行区域的线程数量保持不变。 动态线程机制确定要在并行区域开始时使用的线程数，并使它为区域的持续时间常量。