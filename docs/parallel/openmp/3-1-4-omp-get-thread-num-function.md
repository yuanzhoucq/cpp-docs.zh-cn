---
title: 3.1.4 omp_get_thread_num 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad749b91470f7834169fe8ed734f1d627aa228e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num 函数
`omp_get_thread_num`函数返回的线程数目，在其团队中的线程执行函数。 线程号在于使用介于 0 和**omp_get_num_threads()**-1 （含)。 团队主线程为线程 0。  
  
 格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 如果从串行区域中，调用`omp_get_thread_num`返回 0。 如果从调用在序列化的嵌套并行区域内，此函数将返回 0。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   `omp_get_num_threads` 函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)在页上 37。