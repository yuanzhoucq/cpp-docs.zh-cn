---
title: 3.2.3 omp_set_lock 和 omp_set_nest_lock 函数
ms.date: 11/04/2016
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
ms.openlocfilehash: 8efc1f844be2d1b8cf9b15242758914edd0fca14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617654"
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