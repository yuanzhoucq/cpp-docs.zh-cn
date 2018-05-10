---
title: 3.2.5 omp_test_lock 和 omp_test_nest_lock 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5023f0b089d76e92be886f4917905f57dda7a018
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函数
这些函数尝试设置锁定而不是会阻止线程的执行。 格式如下所示：  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 自变量必须指向一个初始化的锁定变量。 这些函数尝试中与相同的方式将锁`omp_set_lock`和`omp_set_nest_lock`，只不过它们不会阻止线程的执行。  
  
 简单锁，`omp_test_lock`如果成功地设置锁，函数将返回一个非零值; 否则，它将返回零。  
  
 Nestable 锁，`omp_test_nest_lock`函数返回新的嵌套计数，如果已成功设置锁; 否则，它将返回零。