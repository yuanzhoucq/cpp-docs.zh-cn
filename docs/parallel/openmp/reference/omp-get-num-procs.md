---
title: "omp_get_num_procs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_get_num_procs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_num_procs OpenMP function"
ms.assetid: 14a10b8f-e59b-4211-a292-687648c9f760
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# omp_get_num_procs
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

返回可用处理器的数目，则在函数调用时。  
  
## 语法  
  
```  
int omp_get_num_procs();  
```  
  
## 备注  
 有关更多信息，请参见 [3.1.5 omp\_get\_num\_procs Function](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)。  
  
## 示例  
  
```  
// omp_get_num_procs.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    printf_s("%d\n", omp_get_num_procs( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_num_procs( ));  
        }  
}  
```  
  
  **，当此示例在两个处理器的计算机上，运行 \/\/需要以下输出:**  
**2**  
**2**   
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)