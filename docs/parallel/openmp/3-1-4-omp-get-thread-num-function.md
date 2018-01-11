---
title: "3.1.4 omp_get_thread_num 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7b968d103631dafcdd2132cb749ae8feed30085
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
-   `omp_get_num_threads`函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)在页上 37。