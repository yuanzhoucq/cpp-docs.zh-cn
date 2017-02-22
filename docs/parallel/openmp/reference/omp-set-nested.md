---
title: "omp_set_nested | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_nested"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_nested OpenMP function"
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# omp_set_nested
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

使嵌套并行。  
  
## 语法  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## 备注  
 其中，  
  
 `val`  
 如果非零，启用嵌套并行。  如果零，禁用嵌套并行。  
  
## 备注  
 OMP 嵌套并行可打开与 `omp_set_nested`，或者通过设置 [OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md) 环境变量。  
  
 设置 `omp_set_nested` 的将重写设置 `OMP_NESTED` 环境变量。  
  
 当启用，环境变量可以中断一否则操作的过程，因为线程数成指数增加，如果嵌套并行区域时。  例如递归 6 计时与 OMP 线程数设置为 4 的功能需要 4,096 \(4 到 6 的次幂\) 线程应用程序的性能会通常，会降低，如果线程的数量超出处理器的数目。  此操作的一个例外是 I\/O 绑定应用程序。  
  
 使用 [omp\_get\_nested](../../../parallel/openmp/reference/omp-get-nested.md) 显示当前设置 `omp_set_nested`。  
  
 有关更多信息，请参见 [3.1.9 omp\_set\_nested Function](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。  
  
## 示例  
  
```  
// omp_set_nested.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_nested(1);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_nested( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_nested( ));  
        }  
}  
```  
  
  **1**  
**1**   
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)