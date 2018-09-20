---
title: 3.2.3 omp_set_lock 和 omp_set_nest_lock 函数 |Microsoft Docs
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
ms.openlocfilehash: 792b95baef2821bb693d9a90fc228d2b0c508e1f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420356"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函数

每个函数将阻止执行该函数，直到指定的锁可用，然后设置该锁的线程。 如果未锁定可是简单的锁定。 如果未锁定或已归执行该函数的线程可嵌套锁可用。 格式如下所示：

```
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

为一个简单的锁定，到参数`omp_set_lock`函数必须指向初始化的锁定变量。 执行该函数的线程将授予该锁的所有权。

可嵌套锁，到参数`omp_set_nest_lock`函数必须指向初始化的锁定变量。 嵌套计数会递增，并在线程授予后，或保留该锁的所有权。