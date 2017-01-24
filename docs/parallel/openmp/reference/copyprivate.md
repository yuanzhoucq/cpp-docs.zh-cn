---
title: "copyprivate | Microsoft Docs"
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
  - "copyprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copyprivate OpenMP clause"
ms.assetid: 02c0209d-abe8-4797-8365-a82b53c3f15d
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# copyprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定应该在所有线程共享一个或多个变量。  
  
## 语法  
  
```  
copyprivate(var)  
```  
  
## 备注  
 其中，  
  
 `var`  
 对共享的一个或多个变量。  如果多于变量中指定，用逗号分隔变量名称。  
  
## 备注  
 `copyprivate` 适用于 [single](../../../parallel/openmp/reference/single.md) 指令。  
  
 有关更多信息，请参见 [2.7.2.8 copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md)。  
  
## 示例  
  
```  
// omp_copyprivate.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
float x, y, fGlobal = 1.0;  
#pragma omp threadprivate(x, y)  
  
float get_float() {  
   fGlobal += 0.001;  
   return fGlobal;  
}  
  
void use_float(float f, int t) {  
   printf_s("Value = %f, thread = %d\n", f, t);  
}  
  
void CopyPrivate(float a, float b) {  
   #pragma omp single copyprivate(a, b, x, y)   
   {  
      a = get_float();  
      b = get_float();  
      x = get_float();  
      y = get_float();  
    }  
  
   use_float(a, omp_get_thread_num());     
   use_float(b, omp_get_thread_num());     
   use_float(x, omp_get_thread_num());  
   use_float(y, omp_get_thread_num());  
}  
  
int main() {  
   float a = 9.99, b = 123.456;  
  
   printf_s("call CopyPrivate from a single thread\n");  
   CopyPrivate(9.99, 123.456);  
  
   printf_s("call CopyPrivate from a parallel region\n");  
   #pragma omp parallel       
   {  
      CopyPrivate(a, b);  
   }  
}  
```  
  
  **调用从一个线程的 CopyPrivate**  
**值为 1.001000，线程 \= 0**  
**值为 1.002000，线程 \= 0**  
**值为 1.003000，线程 \= 0**  
**值为 1.004000，线程 \= 0**  
**调用从并行区域的 CopyPrivate**  
**值为 1.005000，线程 \= 0**  
**值为 1.005000，线程 \= 1**  
**值为 1.006000，线程 \= 0**  
**值为 1.006000，线程 \= 1**  
**值为 1.007000，线程 \= 0**  
**值为 1.007000，线程 \= 1**  
**值为 1.008000，线程 \= 0**  
**值为 1.008000，线程 \= 1**   
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)