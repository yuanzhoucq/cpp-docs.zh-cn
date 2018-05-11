---
title: 4.2 OMP_NUM_THREADS |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6b4208d7fe7d453dd1f701d820a85fce5cd68ba
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS
**OMP_NUM_THREADS**环境变量设置默认的线程数以使用在执行期间，除非该数字显式更改通过调用**omp_set_num_threads**库例程或通过显式**num_threads**上的子句**并行**指令。  
  
 值**OMP_NUM_THREADS**环境变量必须是正整数。 其效果取决于是否启用动态调整的线程数。 获取完整的有关之间的交互的规则集**OMP_NUM_THREADS**环境变量和动态调整的线程，请参阅第 8 页上的 2.3 节。  
  
 如果为不指定任何值**OMP_NUM_THREADS**环境变量，或如果指定的值不是一个正整数，或如果值大于最大线程数系统可以支持，要使用的线程数是实现定义的。  
  
 示例:  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **num_threads**子句，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上。  
  
-   **omp_set_num_threads**函数中，请参阅[部分 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)页 36 上。  
  
-   **omp_set_dynamic**函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上。