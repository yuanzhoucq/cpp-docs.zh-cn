---
title: "使用原子指令 A.12 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9aa619d9bbe635a41d15a39d6c05780a4416520e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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