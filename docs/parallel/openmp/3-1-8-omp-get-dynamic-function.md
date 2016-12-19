---
title: "3.1.8 omp_get_dynamic Function | Microsoft Docs"
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
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.8 omp_get_dynamic Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**omp\_get\_dynamic** 函数返回非零值，如果线程的动态调整启用，并且否则返回 0。  格式如下所示：  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 如果实现不实现线程数动态调整，此函数始终返回 0。  
  
## 交叉引用:  
  
-   有关动态线程调整的说明，请参见在第 39 页的 [第3.1.7部分](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 。