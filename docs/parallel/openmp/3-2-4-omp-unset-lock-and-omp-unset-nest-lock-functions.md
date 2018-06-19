---
title: 3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f480a75efff737356c1477593e182537ae73a8c8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690216"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数
这些函数提供了一种释放的锁的所有权。 格式如下所示：  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 其中每个函数的参数必须指向拥有的线程执行的函数初始化的锁定变量。 如果线程不拥有该锁，则该行为不确定。  
  
 简单锁，`omp_unset_lock`函数释放的锁的所有权从执行函数的线程。  
  
 Nestable 锁，`omp_unset_nest_lock`函数递减嵌套计数和版本的线程的锁的所有权从执行函数，如果在生成的计数为零。