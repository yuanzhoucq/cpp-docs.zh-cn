---
title: "omp_unset_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_unset_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_unset_lock OpenMP function"
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# omp_unset_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

释放锁。  
  
## 语法  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
## 备注  
 其中，  
  
 `lock`  
 初始化 [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md)，拥有通过线程和执行函数类型 [omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md) 的变量。  
  
## 备注  
 有关更多信息，请参见 [3.2.4 omp\_unset\_lock and omp\_unset\_nest\_lock Functions](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。  
  
## 示例  
 有关使用示例 `omp_unset_lock`参见 [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md) 。  
  
## 请参阅  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)