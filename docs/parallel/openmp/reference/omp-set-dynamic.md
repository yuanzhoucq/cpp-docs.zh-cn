---
title: omp_set_dynamic |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18521113125eb49fa413568b6a62472bb50a7924
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
指示运行时可以进行调整了后续并行区域中的可用线程数。  
  
## <a name="syntax"></a>语法  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `val`  
 一个值，该值指示是否可以由运行时调整后续并行区域中的可用线程数。  如果不为零，运行时可以调整的线程数，如果为零，则运行时将不会动态调整线程的数。  
  
## <a name="remarks"></a>备注  
 线程数将永远不会超过所设置的值[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)。  
  
 使用[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)要显示的当前设置`omp_set_dynamic`。  
  
 有关设置`omp_set_dynamic`将替代的设置[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)环境变量。  
  
 有关详细信息，请参阅[3.1.7 omp_set_dynamic 函数](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## <a name="example"></a>示例  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)