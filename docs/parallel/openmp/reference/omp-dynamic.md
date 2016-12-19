---
title: "OMP_DYNAMIC | Microsoft Docs"
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
  - "OMP_DYNAMIC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_DYNAMIC OpenMP environment variable"
ms.assetid: e306049d-b644-4b73-8b63-46c835bff98b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OMP_DYNAMIC
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

OpenMP 指定运行时是否在并行区域可以调整线程的数量。  
  
## 语法  
  
```  
set OMP_DYNAMIC[=TRUE | =FALSE]  
```  
  
## 备注  
 `OMP_DYNAMIC` 环境变量可由 [omp\_set\_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md) 功能重写。  
  
 在 OpenMP 标准的 Visual C\+\+ 实现的默认值为 `OMP_DYNAMIC=FALSE`。  
  
 有关更多信息，请参见 [4.3 OMP\_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。  
  
## 示例  
 以下命令将 `OMP_DYNAMIC` 环境变量为 true:  
  
```  
set OMP_DYNAMIC=TRUE  
```  
  
 下面的命令演示当前设置 `OMP_DYNAMIC` 环境变量:  
  
```  
set OMP_DYNAMIC  
```  
  
## 请参阅  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)