---
title: "3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dc71c6c31a1d93b6e9c9cce2cd4f7830502a1a2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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