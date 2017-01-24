---
title: "if (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "if OpenMP clause"
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# if (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定是否应执行并行循环或序列化的。  
  
## 语法  
  
```  
if(expression)  
```  
  
## 备注  
 其中，  
  
 `expression`  
 的集成表达式，则为; 如果计算结果为 true \(非零\)，在并行区域导致代码并行执行。  如果表达式的计算结果为 false \(0\)，并行区域序列化的执行 \(由单个线程\)。  
  
## 备注  
 `if` 适用于以下指令:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关更多信息，请参见 [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## 示例  
  
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
  
  **val \= 0，序列化**  
**val \= 2，并行化与 2 线程**   
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)