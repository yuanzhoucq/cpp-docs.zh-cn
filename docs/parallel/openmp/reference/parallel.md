---
title: "并行 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: parallel
dev_langs: C++
helpviewer_keywords: parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f6b10c681eb12d38d33c50fe9e652ffd095dd4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="parallel"></a>parallel
定义并行区域，这是将由多个线程并行执行的代码。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="remarks"></a>备注  
 其中，  
  
 `clause`（可选）  
 零个或多个子句。  请参阅支持的子句列表的备注部分**并行**。  
  
## <a name="remarks"></a>备注  
 **并行**指令支持以下 OpenMP 子句：  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [专用](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [共享](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **并行**也可以用于[部分](../../../parallel/openmp/reference/sections-openmp.md)和[为](../../../parallel/openmp/reference/for-openmp.md)指令。  
  
 有关详细信息，请参阅[2.3 parallel 构造](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何设置的线程数，并定义并行区域。 默认情况下，线程数等于计算机上的逻辑处理器数。 例如，如果你有具有一个具有已启用超线程的物理处理器的计算机，它将具有两个逻辑处理器和，因此，两个线程。  
  
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
  
```Output  
Hello from thread 0  
Hello from thread 1  
Hello from thread 2  
Hello from thread 3  
```  
  
## <a name="comment"></a>注释  
 请注意，在不同计算机上的输出顺序而异。  
  
## <a name="see-also"></a>请参阅  
 [指令](../../../parallel/openmp/reference/openmp-directives.md)