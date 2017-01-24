---
title: "3.2.5 omp_test_lock and omp_test_nest_lock Functions | Microsoft Docs"
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
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.5 omp_test_lock and omp_test_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些函数尝试设置锁定，但不阻塞线程的执行。  格式如下所示：  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 参数必须指向一个锁初始化的变量。  这些函数尝试设置锁定与 `omp_set_lock` 和 `omp_set_nest_lock`相同，不同之处在于，它们不阻塞线程的执行。  
  
 对于简单的锁，因此，如果锁已成功设置， `omp_test_lock` 函数返回非零值;否则，它返回零。  
  
 为可套上的锁，因此，如果锁已成功设置， `omp_test_nest_lock` 函数返回新的嵌套计数;否则，它返回零。