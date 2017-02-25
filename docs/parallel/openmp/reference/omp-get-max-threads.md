---
title: "omp_get_max_threads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_get_max_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_max_threads OpenMP function"
ms.assetid: f47c3725-3e40-469f-8bc8-a1e47f264cc3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# omp_get_max_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

返回等于或大于线程数可用的整数，如果没有 [num\_threads](../../../parallel/openmp/reference/num-threads.md) 的并行区域在代码此时定义。  
  
## 语法  
  
```  
int omp_get_max_threads( )  
```  
  
## 备注  
 有关更多信息，请参见 [3.1.3 omp\_get\_max\_threads Function](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)。  
  
## 示例  
  
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
  
  **8**  
**8**  
**8**  
**8**  
**8**   
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)