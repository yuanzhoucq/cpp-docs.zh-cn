---
title: "OpenMP 指令 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e8d47e6376b3786b27305e65bdb55f0c292995d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="openmp-directives"></a>OpenMP 指令
提供指向 OpenMP API 中使用的指令。  
  
 Visual c + + 支持以下 OpenMP 指令：  
  
|指令|描述|  
|---------------|-----------------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|指定将以原子方式更新的内存位置。|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|同步所有线程在一个组;所有线程在屏障，都暂停，直到所有线程都执行屏障。|  
|[critical](../../../parallel/openmp/reference/critical.md)|指定代码仅执行一个线程上一次。|  
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|指定所有线程都具有相同的所有共享对象的内存的视图。|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|导致中完成的工作划分到线程的并行区域内的循环。|  
|[master](../../../parallel/openmp/reference/master.md)|指定仅 master threadshould 执行程序的一部分。|  
|[ordered](../../../parallel/openmp/reference/ordered-openmp-directives.md)|指定该代码在并行化循环应执行顺序循环类似。|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|定义并行区域，这是将由多个线程并行执行的代码。|  
|[sections](../../../parallel/openmp/reference/sections-openmp.md)|标识要作为被除数所有线程间的代码部分。|  
|[single](../../../parallel/openmp/reference/single.md)|允许您指定的代码部分应在单个线程，不一定是主线程上执行。|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|指定的变量是私有的线程。|  
  
## <a name="see-also"></a>请参阅  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)