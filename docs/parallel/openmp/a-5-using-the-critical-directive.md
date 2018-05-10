---
title: 使用关键指令 A.5 |Microsoft 文档
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
ms.openlocfilehash: c1a41e9664faaca24b6708c737a044828eb460bd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="a5---using-the-critical-directive"></a>A.5   使用 critical 指令
下面的示例包括几个`critical`指令 ([部分 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 页上)。 该示例阐释了一个任务是取消排队和处理的队列模型。 若要防止出队相同的任务的多个线程，取消排队操作必须为`critical`部分。 由于在此示例中的两个队列都是独立的它们通过保护`critical`具有不同名称的指令*xaxis*和*y 轴*。  
  
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