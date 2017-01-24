---
title: "omp_get_dynamic | Microsoft Docs"
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
  - "omp_get_dynamic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_dynamic OpenMP function"
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_get_dynamic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

返回一个值线程数可用在后续并行区域是否可以在运行时调整。  
  
## 语法  
  
```  
int omp_get_dynamic();  
```  
  
## 返回值  
 非零，线程的动态调整有效。  
  
## 备注  
 线程的动态调整指定与 [omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) 和 [OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)。  
  
 有关更多信息，请参见 [3.1.7 omp\_set\_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## 示例  
 有关使用示例 `omp_get_dynamic`参见 [omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) 。  
  
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)