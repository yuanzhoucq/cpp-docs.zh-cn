---
title: 使用原子指令 A.12 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 719d7a9843a0759b5a5bd558e07a2004f9ef1543
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691400"
---
# <a name="a12---using-the-atomic-directive"></a>A.12   使用 atomic 指令
下面的示例可避免争用条件 (的元素的同时更新*x*由多个线程) 通过使用`atomic`指令 ([部分 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md)第 19 页上):  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 使用的优点`atomic`在此示例中的指令是它允许更新的 x 会并行发生在两个不同的元素。 如果`critical`指令 ([部分 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md)第 18 页上) 已使用，则所有更新到的元素*x*将按顺序 （但不在任何保证顺序） 执行。  
  
 请注意，`atomic`指令仅适用于紧靠它的 C 或 c + + 语句。  因此，元素的*y*未在此示例中以原子方式更新。