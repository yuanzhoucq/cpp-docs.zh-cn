---
title: "omp_get_max_threads |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_max_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_get_max_threads OpenMP function
ms.assetid: f47c3725-3e40-469f-8bc8-a1e47f264cc3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3caf2054cee2092ab55a4a65160b4621c3b597d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ompgetmaxthreads"></a>omp_get_max_threads
返回一个整数，等于或大于如果而无需并行区域可用的线程数[num_threads](../../../parallel/openmp/reference/num-threads.md)在该点在代码中定义。  
  
## <a name="syntax"></a>语法  
  
```  
int omp_get_max_threads( )  
```  
  
## <a name="remarks"></a>备注  
 有关详细信息，请参阅[3.1.3 omp_get_max_threads 函数](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)。  
  
## <a name="example"></a>示例  
  
```  
// omp_get_max_threads.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_num_threads(8);  
    printf_s("%d\n", omp_get_max_threads( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_max_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_max_threads( ));  
  
    #pragma omp parallel num_threads(3)  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_max_threads( ));  
        }  
  
    printf_s("%d\n", omp_get_max_threads( ));  
}  
```  
  
```Output  
8  
8  
8  
8  
8  
```  
  
## <a name="see-also"></a>请参阅  
 [函数](../../../parallel/openmp/reference/openmp-functions.md)