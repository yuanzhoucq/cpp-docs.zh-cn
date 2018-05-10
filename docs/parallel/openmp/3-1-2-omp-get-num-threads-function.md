---
title: 3.1.2 omp_get_num_threads 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df01d571b67ff6d252d85128fcc8c1d26a6e94a9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads 函数
**Omp_get_num_threads**函数返回的线程数当前团队执行在调用它的并行区域中。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_num_threads(void);  
```  
  
 **Num_threads**子句， **omp_set_num_threads**函数，与**OMP_NUM_THREADS**环境变量控制的团队中的线程数。  
  
 如果线程数不已显式由用户设置，默认值是实现定义的。 此函数将绑定到最近的封闭**并行**指令。 如果调用从串行一部分的程序，或从序列化的嵌套并行区域，该函数将返回 1。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **OMP_NUM_THREADS**环境变量，请参阅[部分 4.2](../../parallel/openmp/4-2-omp-num-threads.md)第 48 页。  
  
-   **num_threads**子句，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上。  
  
-   **并行**构造，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上。