---
title: "A.12   Using the atomic Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.12   Using the atomic Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的示例避免争用条件 \( *x 元素的* 同时更新由多个线程的\) 使用 `atomic` 指令 \(在第 19 页\) 的[第2.6.4部分](../../parallel/openmp/2-6-4-atomic-construct.md) :  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 使用 `atomic` 指令的优点在此示例中为它允许 x 的两个不同元素更新并行生成。  如果使用了 `critical` 指令 \(在第 18 页\) 的[第2.6.2部分](../../parallel/openmp/2-6-2-critical-construct.md) ，则为 *x 元素的* 所有更新将按顺序执行 \(尽管不以任何确保的顺序\)。  
  
 请注意 `atomic` 指令仅适用于后的 C 或 C\+\+ 语句。  因此， *y 的* 元素不在此示例中更新基本。