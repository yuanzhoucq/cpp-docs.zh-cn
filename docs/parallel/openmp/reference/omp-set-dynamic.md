---
title: "omp_set_dynamic | Microsoft Docs"
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
  - "omp_set_dynamic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_dynamic OpenMP function"
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_set_dynamic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指示线程的数目可用在后续并行区域可以在运行时调整。  
  
## 语法  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## 备注  
 其中，  
  
 `val`  
 一个值线程数可用在后续并行区域是否可以在运行时调整。  如果非零，则运行时会调整线程数，因此，如果零，运行时不会动态调整线程的数量。  
  
## 备注  
 线程数不超过 [OMP\_NUM\_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)集由 [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) 或值。  
  
 使用 [omp\_get\_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md) 显示当前设置 `omp_set_dynamic`。  
  
 设置 `omp_set_dynamic` 的将重写设置 [OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md) 环境变量。  
  
 有关更多信息，请参见 [3.1.7 omp\_set\_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## 示例  
  
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
  
  **1**  
**1**   
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)