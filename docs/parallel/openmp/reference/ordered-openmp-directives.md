---
title: "ordered (OpenMP Directives) | Microsoft Docs"
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
  - "ordered"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ordered OpenMP directive"
ms.assetid: e1aa703e-d07d-4f6a-9b2a-f4f25203d850
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ordered (OpenMP Directives)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定应执行在 for 循环并行化的下面的代码与串行循环。  
  
## 语法  
  
```  
#pragma omp ordered  
   structured-block  
```  
  
## 备注  
 **排序** 指令必须在 [for](../../../parallel/openmp/reference/for-openmp.md) 或 **并行。** 构造中的动态区域与 **排序** 子句中。  
  
 **排序** 指令不支持 OpenMP 子句。  
  
 有关更多信息，请参见 [2.6.6 ordered Construct](../../../parallel/openmp/2-6-6-ordered-construct.md)。  
  
## 示例  
  
```  
// omp_ordered.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
static float a[1000], b[1000], c[1000];  
  
void test(int first, int last)   
{  
    #pragma omp for schedule(static) ordered  
    for (int i = first; i <= last; ++i) {  
        // Do something here.  
        if (i % 2)   
        {  
            #pragma omp ordered   
            printf_s("test() iteration %d\n", i);  
        }  
    }  
}  
  
void test2(int iter)   
{  
    #pragma omp ordered  
    printf_s("test2() iteration %d\n", iter);  
}  
  
int main( )   
{  
    int i;  
    #pragma omp parallel  
    {  
        test(1, 8);  
        #pragma omp for ordered  
        for (i = 0 ; i < 5 ; i++)  
            test2(i);  
    }  
}  
```  
  
  **测试 \(\) 迭代 1**  
**测试 \(\) 迭代 3**  
**测试 \(\) 迭代 5**  
**测试 \(\) 迭代 7**  
**test2 \(\) 迭代 0**  
**test2 \(\) 迭代 1**  
**test2 \(\) 迭代 2**  
**test2 \(\) 迭代 3**  
**test2 \(\) 迭代 4**   
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)