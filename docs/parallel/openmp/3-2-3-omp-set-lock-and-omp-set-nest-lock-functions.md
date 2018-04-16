---
title: "3.2.3 omp_set_lock 和 omp_set_nest_lock 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e709e43a0b32b68bc34c4e76e8680ae371e30670
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函数
其中每个函数会阻止执行函数，直到指定的锁可用，然后将设置锁的线程。 简单锁是解锁是否可用。 如果处于解除锁定状态或已归执行函数的线程，则可用 nestable 锁。 格式如下所示：  
  
```  
#include <omp.h>  
void omp_set_lock(omp_lock_t *lock);  
void omp_set_nest_lock(omp_nest_lock_t *lock);  
```  
  
 简单锁的自变量`omp_set_lock`函数必须指向一个初始化的锁定变量。 锁定的所有权授予执行函数的线程。  
  
 Nestable 锁的自变量`omp_set_nest_lock`函数必须指向一个初始化的锁定变量。 嵌套的计数将递增，并且线程授予后，或保留的锁的所有权。