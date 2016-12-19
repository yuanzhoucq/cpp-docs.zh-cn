---
title: "omp_set_num_threads | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_num_threads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_num_threads OpenMP function"
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_set_num_threads
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

在后续并行区域设置线程数，因此，除非重写由 [num\_threads](../../../parallel/openmp/reference/num-threads.md) 子句。  
  
## 语法  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## 备注  
 其中，  
  
 `num_threads`  
 线程数在并行区域。  
  
## 备注  
 有关更多信息，请参见 [3.1.1 omp\_set\_num\_threads Function](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。  
  
## 示例  
 有关使用示例 `omp_set_num_threads`参见 [omp\_get\_num\_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) 。  
  
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)