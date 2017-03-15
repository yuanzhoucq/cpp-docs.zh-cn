---
title: "shared (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Shared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shared OpenMP clause"
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# shared (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定应该在所有线程共享一个或多个变量。  
  
## 语法  
  
```  
shared(var)  
```  
  
## 备注  
 其中，  
  
 `var`  
 一对共享的更多变量。  如果多于变量中指定，用逗号分隔变量名称。  
  
## 备注  
 另一种共享变量在线程与 [copyprivate](../../../parallel/openmp/reference/copyprivate.md) 子句。  
  
 `shared` 适用于以下指令:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关更多信息，请参见 [2.7.2.4 shared](../../../parallel/openmp/2-7-2-4-shared.md)。  
  
## 示例  
 有关使用示例 `shared`参见 [private](../../../parallel/openmp/reference/private-openmp.md) 。  
  
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)