---
title: A.3   使用并行区域
ms.date: 11/04/2016
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
ms.openlocfilehash: 573c4f7c47c90bc6d567c4640360aa6abee5a48c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458985"
---
# <a name="a3---using-parallel-regions"></a>A.3   使用并行区域

`parallel`指令 ([2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页) 可以在粗粒度的并行程序中使用。 在以下示例中，每个线程中并行区域决定全局数组的哪个部分`x`，工作线程数：

```
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```