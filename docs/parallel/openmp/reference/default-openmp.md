---
title: "default (OpenMP) | Microsoft Docs"
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
  - "default"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default OpenMP clause"
  - "defaults, OpenMP clause"
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# default (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

在并行区域指定 unscoped 变量的行为。  
  
## 语法  
  
```  
default(shared | none)  
```  
  
## 备注  
 `shared`，实际上是，如果 `default` 未指定子句，这意味着任何变量在并行区域将处理，就象指定了一 [shared](../../../parallel/openmp/reference/shared-openmp.md) 子句。  `none` 意味着没有范围与 [private](../../../parallel/openmp/reference/private-openmp.md)用于并行区域， [shared](../../../parallel/openmp/reference/shared-openmp.md)、 [reduction](../../../parallel/openmp/reference/reduction.md)、 [firstprivate](../../../parallel/openmp/reference/firstprivate.md)或 [lastprivate](../../../parallel/openmp/reference/lastprivate.md) 子句的所有变量将导致编译器错误。  
  
 `default` 适用于以下指令:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关更多信息，请参见 [2.7.2.5 default](../../../parallel/openmp/2-7-2-5-default.md)。  
  
## 示例  
 有关使用示例 `default`参见 [private](../../../parallel/openmp/reference/private-openmp.md) 。  
  
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)