---
title: "3.2.1 omp_init_lock and omp_init_nest_lock Functions | Microsoft Docs"
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
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.1 omp_init_lock and omp_init_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这些功能提供初始化锁的唯一方法。  每个函数初始化锁定与参数 *锁* 用于对的后续调用。  格式如下所示：  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 初始状态取消锁定 \(即线程不拥有锁\)。  对于可套上的锁，初始嵌套计数为零。  它是不符合调用与已初始化的锁变量的这些实例之一。