---
title: "3.2.1 omp_init_lock 和 omp_init_nest_lock 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3802822465d6527e4c98a0be6a8c274d767b0f52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函数
这些函数提供初始化锁的唯一的方法。 每个函数初始化与参数相关联的锁*锁*在后续调用中使用。 格式如下所示：  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 初始状态处于解除锁定状态 （即，无需对线程拥有的锁定）。 Nestable 锁，初始嵌套计数为零。 它不符合要求，这些例程已初始化的锁变量任一调用。