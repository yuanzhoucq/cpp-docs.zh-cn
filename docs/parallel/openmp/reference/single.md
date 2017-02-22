---
title: "single | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Single"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single OpenMP directive"
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# single
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

允许您不必指定应在单个线程上执行代码的一部分，主线程。  
  
## 语法  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### 参数  
 `clause`（可选）  
 零个或多个子句。  为 **单个**支持子句的列表参见 " 备注 " 节。  
  
## 备注  
 **单个** 指令支持以下 OpenMP 子句:  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
 [master](../../../parallel/openmp/reference/master.md) 指令允许您指定在主线程只应执行代码的一部分。  
  
 有关更多信息，请参见 [2.4.3 single Construct](../../../parallel/openmp/2-4-3-single-construct.md)。  
  
## 示例  
  
```  
// omp_single.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(2)  
   {  
      #pragma omp single  
      // Only a single thread can read the input.  
      printf_s("read input\n");  
  
      // Multiple threads in the team compute the results.  
      printf_s("compute results\n");  
  
      #pragma omp single  
      // Only a single thread can write the output.  
      printf_s("write output\n");  
    }  
}  
```  
  
  **读取输入**  
**计算结果**  
**计算结果**  
**写入输出**   
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)