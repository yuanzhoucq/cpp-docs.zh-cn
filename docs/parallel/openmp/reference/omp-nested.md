---
title: "OMP_NESTED | Microsoft Docs"
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
  - "OMP_NESTED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OMP_NESTED OpenMP environment variable"
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OMP_NESTED
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定嵌套并行是否启用，，除非嵌套并行启用或禁用到 `omp_set_nested`。  
  
## 语法  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## 备注  
 `OMP_NESTED` 环境变量可由 [omp\_set\_nested](../../../parallel/openmp/reference/omp-set-nested.md) 功能重写。  
  
 在 OpenMP 标准的 Visual C\+\+ 实现的默认值为 `OMP_DYNAMIC=FALSE`。  
  
 有关更多信息，请参见 [4.4 OMP\_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。  
  
## 示例  
 以下命令将 `OMP_NESTED` 环境变量为 true:  
  
```  
set OMP_NESTED=TRUE  
```  
  
 下面的命令演示当前设置 `OMP_NESTED` 环境变量:  
  
```  
set OMP_NESTED  
```  
  
## 请参阅  
 [Environment Variables](../../../parallel/openmp/reference/openmp-environment-variables.md)