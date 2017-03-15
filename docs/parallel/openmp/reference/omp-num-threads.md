---
title: "OMP_NUM_THREADS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OMP_NUM_THREADS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_NUM_THREADS OpenMP environment variable"
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# OMP_NUM_THREADS
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

在并行区域设置线程的最大项数，，除非重写由 [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) 或 [num\_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
## 语法  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## 备注  
 其中，  
  
 `num`  
 在并行区域希望线程， 64 的最大数在 Visual C\+\+ 中实现。  
  
## 备注  
 **OMP\_NUM\_THREADS** 环境变量可以重写由 [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) 函数或由 [num\_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
 `num` 的默认值在 OpenMP 标准的 Visual C\+\+ 实现的是虚拟处理器的数目，包括 hyperthreading CPU。  
  
 有关更多信息，请参见 [4.2 OMP\_NUM\_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。  
  
## 示例  
 以下命令将 **OMP\_NUM\_THREADS** 环境变量设置为 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 下面的命令演示当前设置 **OMP\_NUM\_THREADS** 环境变量:  
  
```  
set OMP_NUM_THREADS  
```  
  
## 请参阅  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)