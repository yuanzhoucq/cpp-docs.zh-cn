---
title: A.5 使用 critical 指令 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f9ab513ae1df5a7e1e62cfefcefe404637c063
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444562"
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