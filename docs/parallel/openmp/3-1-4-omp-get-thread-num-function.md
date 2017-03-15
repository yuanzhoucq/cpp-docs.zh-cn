---
title: "3.1.4 omp_get_thread_num Function | Microsoft Docs"
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
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.4 omp_get_thread_num Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_get_thread_num` 函数返回线程数，在其团队，线程中执行该函数。  线程数放在 0 和 **omp\_get\_num\_threads \(\)**– 1 之间，包含。  团队的主线程是线程 0。  
  
 格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_thread_num(void);  
```  
  
 如果调用从一个序列化的区域， `omp_get_thread_num` 返回 0。  如果调用从序列化的嵌套并行区域内，此函数返回 0。  
  
## 交叉引用:  
  
-   `omp_get_num_threads` 功能，请参见中的第 37 页的 [第3.1.2部分](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) 。