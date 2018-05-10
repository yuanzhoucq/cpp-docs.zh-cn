---
title: 如果 (OpenMP) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- if OpenMP clause
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2467c295c4f2724ec6d258e844f2bdaa84cfe29
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="if-openmp"></a>if (OpenMP)
指定是否应在并行或序列中执行循环。  
  
## <a name="syntax"></a>语法  
  
```  
if(expression)  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `expression`  
 一个整数表达式，如果其计算结果为 true （非零），则导致在并行区域来并行执行的代码。 如果表达式的计算结果为 false （零），则并行区域 （通过单个线程） 执行在序列中。  
  
## <a name="remarks"></a>备注  
 `if` 适用于以下指令：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [部分](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关详细信息，请参阅[2.3 parallel 构造](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>示例  
  
```  
// omp_if.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
void test(int val)  
{  
    #pragma omp parallel if (val)  
    if (omp_in_parallel())  
    {  
        #pragma omp single  
        printf_s("val = %d, parallelized with %d threads\n",  
                 val, omp_get_num_threads());  
    }  
    else  
    {  
        printf_s("val = %d, serialized\n", val);  
    }  
}  
  
int main( )  
{  
    omp_set_num_threads(2);  
    test(0);  
    test(2);  
}  
```  
  
```Output  
val = 0, serialized  
val = 2, parallelized with 2 threads  
```  
  
## <a name="see-also"></a>请参阅  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)