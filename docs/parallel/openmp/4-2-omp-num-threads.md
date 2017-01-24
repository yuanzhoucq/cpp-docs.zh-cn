---
title: "4.2 OMP_NUM_THREADS | Microsoft Docs"
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
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.2 OMP_NUM_THREADS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**OMP\_NUM\_THREADS** 环境变量中设置线程的默认周期数在执行时，，除非该数字显式更改被调用 **omp\_set\_num\_threads** 库实例或已在 **并行** 指令的显式 **num\_threads** 子句。  
  
 **OMP\_NUM\_THREADS** 环境变量的值必须是正整数。  其效果取决于线程数动态调整是否启用。  有关全面设置有关交互的规则线程的 **OMP\_NUM\_THREADS** 环境变量和动态调整之间，请参见有关第 8. 页的第 2.3 节。  
  
 如果值不为 **OMP\_NUM\_THREADS** 环境变量指定，或者，如果指定的值不是正整数，或者，如果值大于线程的最大数量大于系统可以支持，使用线程的数量实现中定义。  
  
 示例：  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## 交叉引用:  
  
-   **num\_threads** 子句，请参见中的第 8. 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md) 。  
  
-   **omp\_set\_num\_threads** 功能，请参见中的第 36 页的 [第3.1.1部分](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) 。  
  
-   **omp\_set\_dynamic** 功能，请参见中的第 39 页的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。