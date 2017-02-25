---
title: "parallel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "parallel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parallel OpenMP directive"
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# parallel
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

定义并行区域，是将由多个线程并行执行。  
  
## 语法  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## 备注  
 其中，  
  
 `clause`（可选）  
 零或多个子句。  为 **并行**支持子句的列表参见 " 备注 " 节。  
  
## 备注  
 **并行** 指令支持以下 OpenMP 子句:  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num\_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [shared](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **并行** 也可以用于 [sections](../../../parallel/openmp/reference/sections-openmp.md) 和 [for](../../../parallel/openmp/reference/for-openmp.md) 指令。  
  
 有关更多信息，请参见 [2.3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## 示例  
 下面的示例演示如何设置线程的数量和定义并行区域。  默认情况下，线程的数量与逻辑处理器数相等计算机上的。  例如，因此，如果您具有已启用 hyperthreading 的实际处理器的计算机，则会有两个逻辑处理器，因此，因此，两个线程。  
  
```  
// omp_parallel.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(4)  
   {  
      int i = omp_get_thread_num();  
      printf_s("Hello from thread %d\n", i);  
   }  
}  
```  
  
  **hello 从线程 0**  
**hello 从线程 1**  
**hello 从线程 2**  
**hello 从线程 3**   
## 注释  
 请注意输出顺序在不同的计算机可能会有所不同。  
  
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)