---
title: "sections (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "section"
  - "SECTIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sections OpenMP directive"
ms.assetid: 4cd1d776-e198-470e-930a-01fb0ab0a0bd
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# sections (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

标识在所有线程中拆分代码部分。  
  
## 语法  
  
```  
#pragma omp [parallel] sections [clauses]  
{  
   #pragma omp section  
   {  
      code_block   
   }   
}  
```  
  
## 备注  
 其中，  
  
 `clause`（可选）  
 零个或多个子句。  为 **部分**支持子句的列表参见 " 备注 " 节。  
  
## 备注  
 **部分** 指令可以包含零个或多 **部分** 指令。  
  
 **部分** 指令支持以下 OpenMP 子句:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
 如果 **并行** 还指定， `clause` 可以是 **并行** 或 **部分** 指令接受的所有子句，但 `nowait`。  
  
 有关更多信息，请参见 [2.4.2 sections Construct](../../../parallel/openmp/2-4-2-sections-construct.md)。  
  
## 示例  
  
```  
// omp_sections.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
    #pragma omp parallel sections num_threads(4)  
    {  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
        #pragma omp section  
        printf_s("Hello from thread %d\n", omp_get_thread_num());  
    }  
}  
```  
  
  **hello 从线程 0**  
**hello 从线程 0**   
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)