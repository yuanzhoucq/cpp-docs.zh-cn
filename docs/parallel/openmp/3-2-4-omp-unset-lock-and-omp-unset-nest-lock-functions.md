---
title: "3.2.4 omp_unset_lock and omp_unset_nest_lock Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.4 omp_unset_lock and omp_unset_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些功能提供释放锁的所有权方法。  格式如下所示：  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 对这些函数中的参数必须指向线程所拥有的一个锁初始化的变量执行该函数。  ，如果线程没有该锁，该行为不确定。  
  
 对于简单的锁， `omp_unset_lock` 函数从锁的所有权释放执行该函数的线程。  
  
 为可套上的锁，因此，如果所得计数为零， `omp_unset_nest_lock` 函数递减嵌套计数，然后从锁的所有权释放执行该函数的线程。