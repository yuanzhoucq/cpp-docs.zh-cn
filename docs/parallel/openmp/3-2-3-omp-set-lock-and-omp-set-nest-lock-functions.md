---
title: 3.2.3 omp_set_lock 和 omp_set_nest_lock 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba24e923051eb887db2a81c1d9765d31a4ef7b24
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689709"
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