---
title: "OpenMP Directives | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OpenMP Directives
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供指向用于 OpenMP API 的指令。  
  
 Visual C\+\+ 支持以下 OpenMP 指令:  
  
|指令|说明|  
|--------|--------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|指定将更新基本的内存位置。|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|同步团队的所有线程;所有线程暂停在关卡，，直到所有线程执行关卡。|  
|[critical](../../../parallel/openmp/reference/critical.md)|指定代码在一个线程次仅执行。|  
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|指定所有线程的内存同一视图所有共享对象的。|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|在循环中而生成的已完成的工作在线程中拆分并行区域内。|  
|[master](../../../parallel/openmp/reference/master.md)|仅指定母版 threadshould 执行程序的一部分。|  
|[ordered](../../../parallel/openmp/reference/ordered-openmp-directives.md)|指定应执行在 for 循环并行化的下面的代码与串行循环。|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|定义并行区域，是将由多个线程并行执行。|  
|[sections](../../../parallel/openmp/reference/sections-openmp.md)|标识在所有线程中拆分代码部分。|  
|[single](../../../parallel/openmp/reference/single.md)|允许您不必指定应在单个线程上执行代码的一部分，主线程。|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|指定变量是私有的。线程。|  
  
## 请参阅  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)