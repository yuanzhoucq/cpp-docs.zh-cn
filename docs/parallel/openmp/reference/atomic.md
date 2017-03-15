---
title: "atomic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "atomic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atomic OpenMP directive"
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# atomic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定将更新基本的内存位置。  
  
## 语法  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### 参数  
 `expression`  
 包含要防止多个编写的左值内存位置的语句。  有关法律 word 窗体的更多信息，请参见 OpenMP 规范。  
  
## 备注  
 `atomic` 指令不支持 OpenMP 子句。  
  
 有关更多信息，请参见 [2.6.4 atomic Construct](../../../parallel/openmp/2-6-4-atomic-construct.md)。  
  
## 示例  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
  **线程的数量:10**   
## 请参阅  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)