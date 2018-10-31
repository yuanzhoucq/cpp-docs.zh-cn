---
title: A.4   使用 nowait 子句
ms.date: 11/04/2016
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
ms.openlocfilehash: 7f839397787c35e88ea325c2db81b15b3a4e7508
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454920"
---
# <a name="a4---using-the-nowait-clause"></a>A.4   使用 nowait 子句

如果有多个独立循环并行区域内的，则可以使用`nowait`子句 ([部分 2.4.1](../../parallel/openmp/2-4-1-for-construct.md)第 11 页上) 以避免隐式末尾的屏障`for`指令，如下所示：

```
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```