---
title: "3.2.3 omp_set_lock and omp_set_nest_lock Functions | Microsoft Docs"
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
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.3 omp_set_lock and omp_set_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些功能中的每个块执行该函数的线程，直到指定的锁可用然后设置锁定。  ，则取消锁定，简单的锁可用。  可套上的锁可用，则取消锁定，或者通过执行函数的线程已拥有。  格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_lock(omp_lock_t *lock);  
void omp_set_nest_lock(omp_nest_lock_t *lock);  
```  
  
 对于简单的锁，对 `omp_set_lock` 函数的参数必须指向一个锁初始化的变量。  锁定的所有权授予执行该函数的线程。  
  
 为可套上的锁，对 `omp_set_nest_lock` 函数的参数必须指向一个锁初始化的变量。  嵌套计数递增，并且，授予线程还是保留，固定的所有权。