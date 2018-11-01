---
title: A.12   使用 atomic 指令
ms.date: 11/04/2016
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
ms.openlocfilehash: 0f75b182e2cae11f0e72d5ca1e67f887294e8f69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504421"
---
# <a name="a12---using-the-atomic-directive"></a>A.12   使用 atomic 指令

下面的示例可避免争用条件 (同时进行更新的元素*x*由多个线程) 通过使用`atomic`指令 ([部分 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md)第 19 页上):

```
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

使用的优点`atomic`指令在此示例中是允许更新的 x 会并行发生两个不同元素。 如果`critical`指令 ([部分 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 页上) 然后所有更新的元素到相反，使用*x*会按顺序 （尽管不在任何有保证的顺序） 执行。

请注意，`atomic`指令仅适用于紧随的 C 或 c + + 语句。  因此中的元素*y*不在此示例中以原子方式更新。