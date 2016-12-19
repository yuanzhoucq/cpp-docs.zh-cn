---
title: "master | Microsoft Docs"
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
  - "master"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "master OpenMP directive"
ms.assetid: 559ed974-e02a-486e-a23f-31556429b2c4
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# master
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

仅指定母版 threadshould 执行程序的一部分。  
  
## 语法  
  
```  
#pragma omp master  
{  
   code_block  
}  
```  
  
## 备注  
 **母版** 指令不支持 OpenMP 子句。  
  
 [single](../../../parallel/openmp/reference/single.md) 指令允许您不必指定应在单个线程上执行代码的一部分，主线程。  
  
 有关更多信息，请参见 [2.6.1 master Construct](../../../parallel/openmp/2-6-1-master-construct.md)。  
  
## 示例  
  
```  
// omp_master.cpp  
// compile with: /openmp   
#include <omp.h>  
#include <stdio.h>  
  
int main( )   
{  
    int a[5], i;  
  
    #pragma omp parallel  
    {  
        // Perform some computation.  
        #pragma omp for  
        for (i = 0; i < 5; i++)  
            a[i] = i * i;  
  
        // Print intermediate results.  
        #pragma omp master  
            for (i = 0; i < 5; i++)  
                printf_s("a[%d] = %d\n", i, a[i]);  
  
        // Wait.  
        #pragma omp barrier  
  
        // Continue with the computation.  
        #pragma omp for  
        for (i = 0; i < 5; i++)  
            a[i] += i;  
    }  
}  
```  
  
  **\[\] 0 \= 0**  
**\[\] 1 \= 1**  
**\[\] 2 \= 4**  
**\[\] 3 \= 9**  
**\[\] 4 \= 16**   
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)