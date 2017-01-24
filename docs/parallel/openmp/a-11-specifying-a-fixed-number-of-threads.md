---
title: "A.11   Specifying a Fixed Number of Threads | Microsoft Docs"
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
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.11   Specifying a Fixed Number of Threads
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

某些程序依赖线程的内置，预先指定数量的正确执行。  由于设置为线程数动态调整的默认实现中定义，此类程序可以选择关闭动态线程功能和显式设置线程的数目确保可移植性。  下面的示例演示如何使用 `omp_set_dynamic` \(在第 39 页\) 的[第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 和 `omp_set_num_threads` \(在第 36 页\) 的[第3.1.1部分](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) :  
  
```  
omp_set_dynamic(0);  
omp_set_num_threads(16);  
#pragma omp parallel shared(x, npoints) private(iam, ipoints)  
{  
    if (omp_get_num_threads() != 16)   
      abort();  
    iam = omp_get_thread_num();  
    ipoints = npoints/16;  
    do_by_16(x, iam, ipoints);  
}  
```  
  
 在此示例中，时，才能由 16 个线程，执行程序正确执行。  如果实现不能支持 16 个线程，此示例行为实现中定义。  
  
 请注意执行并行区域的线程数保持不变在并行区域内，无论动态线程设置，。  动态线程 framework 确定线程数在并行区域的开始使用并使该常数为该区域的持续时间。