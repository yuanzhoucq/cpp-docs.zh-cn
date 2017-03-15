---
title: "3.1.1 omp_set_num_threads Function | Microsoft Docs"
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
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.1 omp_set_num_threads Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_set_num_threads` 功能设置线程的默认周期数为未指定 `num_threads` 子句的后续并行区域使用。  格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_num_threads(int num_threads);  
```  
  
 参数 *num\_threads 的* 值必须是正整数。  其效果取决于线程数动态调整是否启用。  有关全面设置有关交互的规则线程的 `omp_set_num_threads` 功能和动态调整之间，请参见有关第 8. 页的第 2.3 节。  
  
 该函数具有中描述的效果顶部，在调用从 `omp_in_parallel` 函数返回零程序的一部分。  如果从 `omp_in_parallel` 函数返回非零值程序的一部分调用，此功能的行为未定义。  
  
 这称为在 `OMP_NUM_THREADS` 环境变量的优先级。  线程数默认值，才能建立通过调用 `omp_set_num_threads` 或通过设置 `OMP_NUM_THREADS` 环境变量，单一 **并行** 指令中显式重写通过指定 `num_threads` 子句。  
  
## 交叉引用:  
  
-   `omp_set_dynamic` 功能，请参见中的第 39 页的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。  
  
-   `omp_get_dynamic` 功能，请参见中的第 40 页的 [第3.1.8部分](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) 。  
  
-   `OMP_NUM_THREADS` 环境变量，请参见中的第 48 页的有关第 8. 页的 [第4.2部分](../../parallel/openmp/4-2-omp-num-threads.md) 和第 2.3 部分。  
  
-   `num_threads` 子句，请参见中的第 8 页的 [第2.3部分](../../parallel/openmp/2-3-parallel-construct.md)