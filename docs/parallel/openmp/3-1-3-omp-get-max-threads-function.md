---
title: "3.1.3 omp_get_max_threads 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e021f0873aa94f53a1218a3278a744a0c7740e65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads 函数
**Omp_get_max_threads**函数返回一个整数，它可以保证至少与将用于形成一个组合，如果没有并行区域的线程数一样大**num_threads**子句已在该点遇到在代码中。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_max_threads(void);  
```  
  
 下面的值表示下限**omp_get_max_threads**:  
  
```  
  
threads-used-for-next-team  
 <= omp_get_max_threads  
  
```  
  
 请注意，如果后续并行区域使用**num_threads**子句来请求特定的线程数，结果的下限上保证**omp_get_max_threads**并未长。  
  
 **Omp_get_max_threads**函数的返回值可以用于动态团队在后续的并行区域格式中的所有线程分配足够的存储空间。  
  
## <a name="cross-references"></a>交叉引用：  
  
-   **omp_get_num_threads**函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)在页上 37。  
  
-   **omp_set_num_threads**函数中，请参阅[部分 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)页 36 上。  
  
-   **omp_set_dynamic**函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)页 39 上。  
  
-   **num_threads**子句，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页上。