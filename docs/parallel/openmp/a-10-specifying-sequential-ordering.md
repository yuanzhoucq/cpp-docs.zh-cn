---
title: 指定顺序排序的 A.10 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5c65a9b1-0fc5-4cad-a5a9-9ce10b25d25c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48e512a669025403b76b76b49c5bb496b5eacd23
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="a10---specifying-sequential-ordering"></a>A.10   指定顺序排序
排序部分 ([部分 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md)页 22 上) 可用于按顺序排序的输出中并行执行的工作。 下面的程序输出顺序中的索引：  
  
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