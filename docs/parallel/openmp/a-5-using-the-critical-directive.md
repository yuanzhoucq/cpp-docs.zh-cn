---
title: A.5   使用 critical 指令
ms.date: 11/04/2016
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
ms.openlocfilehash: 82497d63acc057fbbcf26f585e42fc8611c08ec4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545081"
---
# <a name="a5---using-the-critical-directive"></a>A.5   使用 critical 指令

下面的示例包括若干`critical`指令 ([部分 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 页上)。 该示例阐释了队列的模型在其中取消排队和从事一项任务。 若要防止多个线程取消排队相同的任务，取消排队操作必须为`critical`部分。 由于在此示例中的两个队列都是独立的它们受`critical`具有不同名称的指令*xaxis*并*y 轴*。

```
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```