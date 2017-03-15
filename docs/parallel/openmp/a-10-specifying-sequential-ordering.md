---
title: "A.10   Specifying Sequential Ordering | Microsoft Docs"
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
ms.assetid: 5c65a9b1-0fc5-4cad-a5a9-9ce10b25d25c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.10   Specifying Sequential Ordering
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

经过排序的节 \(在第 22 页\) 的[第2.6.6部分](../../parallel/openmp/2-6-6-ordered-construct.md) 为顺序将从并行执行的工作的输出很有用。  下面的过程打印分析索引顺序:  
  
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