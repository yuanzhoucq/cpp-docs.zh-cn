---
title: "3.3.1 omp_get_wtime Function | Microsoft Docs"
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
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.3.1 omp_get_wtime Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_get_wtime` 功能 \(返回一个双精度浮点值等于 " 的壁钟时从时间 “时间过去”。  实际 “时间过去”是任意的，但是，确保不在应用程序执行更改。  格式如下所示：  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 预期如下面的示例所示，函数将用于测量时间:  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 返回的时间是 “每个线程都由哪些超时”这意味着不需要它们是全局一致的。所有线程之间参与应用程序的。