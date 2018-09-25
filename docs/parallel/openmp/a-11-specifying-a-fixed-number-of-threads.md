---
title: A.11 指定固定的数目的线程 |Microsoft Docs
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
ms.openlocfilehash: 892140425dc9f7083c606fce3ffe671a107a65ca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422982"
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   指定固定数目的线程

某些程序依赖于固定的预先指定的正确执行的线程数。  指动态调整的线程数的默认设置是实现定义的因为此类程序可以选择关闭动态线程功能，并设置显式要确保可移植性的线程数。 下面的示例演示如何执行此操作使用`omp_set_dynamic`([部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上)，和`omp_set_num_threads`([部分 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)第 36 页上):

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

在此示例中，程序才会执行正确通过 16 个线程执行。 如果该实现不能支持 16 个线程，此示例中的行为是实现定义的。

请注意，在并行区域，而不考虑动态线程设置期间，执行并行区域的线程数量保持不变。 动态线程机制确定要使用并行区域开始时的线程数并将其保留常量区域的持续时间。