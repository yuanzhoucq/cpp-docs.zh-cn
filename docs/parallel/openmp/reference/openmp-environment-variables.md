---
title: "OpenMP Environment Variables | Microsoft Docs"
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
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OpenMP Environment Variables
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供指向用于 OpenMP API 的环境变量。  
  
 OpenMP 标准的 Visual C\+\+ 实现包括下列环境变量。  这些环境变量阅读程序启动，并更改其值的修改将被忽略在运行时 \(例如，使用 [\_putenv、\_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)\)。  
  
|环境变量|说明|  
|----------|--------|  
|[OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|OpenMP 指定运行时是否在并行区域可以调整线程的数量。|  
|[OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md)|指定嵌套并行是否启用，，除非嵌套并行启用或禁用到 `omp_set_nested`。|  
|[OMP\_NUM\_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|在并行区域设置线程的最大项数，，除非重写由 [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) 或 [num\_threads](../../../parallel/openmp/reference/num-threads.md)。|  
|[OMP\_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|，当 `schedule(runtime)` 在 `for` 或 `parallel for` 指令时，指定修改 [schedule](../../../parallel/openmp/reference/schedule.md) 子句的行为。|  
  
## 请参阅  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)