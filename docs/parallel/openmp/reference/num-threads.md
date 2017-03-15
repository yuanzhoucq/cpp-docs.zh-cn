---
title: "num_threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "num_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_threads OpenMP clause"
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# num_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

设置线程数。线程团队。  
  
## 语法  
  
```  
num_threads(num)  
```  
  
## 备注  
 其中，  
  
 `num`  
 线程数  
  
## 备注  
 `num_threads` 子句具有与 [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) 功能相同。  
  
 `num_threads` 适用于以下指令:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关更多信息，请参见 [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## 示例  
 有关使用示例 `num_threads` 子句参见 [parallel](../../../parallel/openmp/reference/parallel.md) 。  
  
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)