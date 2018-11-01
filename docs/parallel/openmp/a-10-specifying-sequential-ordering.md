---
title: A.10   指定顺序排序
ms.date: 11/04/2016
ms.assetid: 5c65a9b1-0fc5-4cad-a5a9-9ce10b25d25c
ms.openlocfilehash: 4e3a146e1bca988f46cf7a7ee504644f96dab67e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575244"
---
# <a name="a10---specifying-sequential-ordering"></a>A.10   指定顺序排序

排序部分 ([部分 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) 22 页上) 可用于按顺序排序的并行完成工作的输出。 以下程序将输出按顺序排列的索引：

```
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```