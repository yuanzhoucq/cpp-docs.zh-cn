---
title: "OpenMP Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OpenMP Data Types
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供指向用于 OpenMP API 的数据类型。  
  
 OpenMP 标准的 Visual C\+\+ 实现包括以下数据类型。  
  
|数据类型|说明|  
|----------|--------|  
|[omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md)|持有锁的状态类型，锁是否可用，或者线程拥有锁。|  
|[omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)|包含以下信息之一有关锁定的类型:锁是否可用并且拥有锁和嵌套计数线程的标识。|  
  
## 请参阅  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)