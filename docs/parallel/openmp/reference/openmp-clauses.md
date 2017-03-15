---
title: "OpenMP Clauses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OpenMP Clauses
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供指向用于 OpenMP API 的子句。  
  
 Visual C\+\+ 支持以下 OpenMP 子句:  
  
|子句|说明|  
|--------|--------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|提供线程访问主线程的值， [threadprivate](../../../parallel/openmp/reference/threadprivate.md) 变量中。|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|指定应该在所有线程共享一个或多个变量。|  
|[default](../../../parallel/openmp/reference/default-openmp.md)|在并行区域指定 unscoped 变量的行为。|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|指定每个线程都应具有其变量自己的实例，因此，应该初始化该变量与变量的值，，因为它在并行构造之前存在。|  
|[if](../../../parallel/openmp/reference/if-openmp.md)|指定是否应执行并行循环或序列化的。|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|指定变量的封闭上下文的版本使用专用版本将被设置为等于线程执行最终迭代 \(对于循环构造\) 或前一节 \(\#pragma 节\)。|  
|[nowait](../../../parallel/openmp/reference/nowait.md)|重写关卡隐式在指令。|  
|[num\_threads](../../../parallel/openmp/reference/num-threads.md)|设置线程数。线程团队。|  
|[ordered](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|需要在并行 [for](../../../parallel/openmp/reference/for-openmp.md) 语句，如果 [ordered](../../../parallel/openmp/reference/ordered-openmp-directives.md) 指令将用于循环。|  
|[private](../../../parallel/openmp/reference/private-openmp.md)|指定每个线程都应具有其变量自己的实例。|  
|[reduction](../../../parallel/openmp/reference/reduction.md)|指定是私有的。每个线程的一个或多个变量是减少操作的主题在并行区域末端。|  
|[schedule](../../../parallel/openmp/reference/schedule.md)|适用于 [for](../../../parallel/openmp/reference/for-openmp.md) 指令。|  
|[shared](../../../parallel/openmp/reference/shared-openmp.md)|指定应该在所有线程共享一个或多个变量。|  
  
## 请参阅  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)