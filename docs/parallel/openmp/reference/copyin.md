---
title: "copyin | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "copyin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copyin OpenMP clause"
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# copyin
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供线程访问主线程的值， [threadprivate](../../../parallel/openmp/reference/threadprivate.md) 变量中。  
  
## 语法  
  
```  
copyin(var)  
```  
  
## 备注  
 其中，  
  
 `var`  
 将初始化变量的值在主线程上， `threadprivate` 变量，它在并行构造之前存在。  
  
## 备注  
 `copyin` 适用于以下指令:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 有关更多信息，请参见 [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md)。  
  
## 示例  
 有关使用示例 `copyin`参见 [threadprivate](../../../parallel/openmp/reference/threadprivate.md) 。  
  
## 请参阅  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)