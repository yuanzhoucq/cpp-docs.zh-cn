---
title: "3.1.1 omp_set_num_threads 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 568f01aacd361437929606307186bb7cd2eaad7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads 函数
`omp_set_num_threads`函数设置默认线程数以用于后续的并行区域未指定`num_threads`子句。 格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_num_threads(int num_threads);  
```  
  
 参数的值*num_threads*必须是正整数。 其效果取决于是否启用动态调整的线程数。 获取完整的有关之间的交互的规则集`omp_set_num_threads`函数和动态调整的线程，请参阅第 8 页上的 2.3 节。  
  
 此函数具有从一部分的程序中调用时，上面所述的效果其中`omp_in_parallel`函数将返回零。 如果它从一部分的程序调用其中`omp_in_parallel`函数将返回一个非零值，此函数的行为是不确定。  
  
 此调用的优先级高于`OMP_NUM_THREADS`环境变量。 可能由调用的线程数的默认值`omp_set_num_threads`或通过设置`OMP_NUM_THREADS`环境变量，可以显式重写在单个上**并行**通过指定指令`num_threads`子句。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   `omp_set_dynamic`函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上。  
  
-   `omp_get_dynamic`函数中，请参阅[部分 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) 40 页上。  
  
-   `OMP_NUM_THREADS`环境变量，请参阅[部分 4.2](../../parallel/openmp/4-2-omp-num-threads.md)在页 48 和第 8 页第 2.3 节。  
  
-   `num_threads`子句，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页