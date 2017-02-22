---
title: "omp_get_nested | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_get_nested"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_nested OpenMP function"
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# omp_get_nested
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

返回一个值嵌套并行是否启用。  
  
## 语法  
  
```  
int omp_get_nested( );  
```  
  
## 返回值  
 非零，则嵌套并行有效。  
  
## 备注  
 嵌套并行指定与 [omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md) 和 [OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md)。  
  
 有关更多信息，请参见 [3.1.10 omp\_get\_nested Function](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。  
  
## 示例  
 有关使用示例 `omp_get_nested`参见 [omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md) 。  
  
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)