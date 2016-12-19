---
title: "A.1   Executing a Simple Loop in Parallel | Microsoft Docs"
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
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.1   Executing a Simple Loop in Parallel
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下面的示例演示如何并行化一个简单的循环使用 `parallel for` 指令 \(在第 16 页\) 的[第2.5.1部分](../../parallel/openmp/2-5-1-parallel-for-construct.md) 。  默认情况下循环迭代变量是私有的，因此，显式指定它在私有子句并不是必需的。  
  
```  
#pragma omp parallel for  
    for (i=1; i<n; i++)  
        b[i] = (a[i] + a[i-1]) / 2.0;  
```