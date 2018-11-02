---
title: 3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数
ms.date: 11/04/2016
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
ms.openlocfilehash: b0764e3590f8edb3a3e783d9b5493a64be154401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607855"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数

这些函数提供的释放锁的所有权的方法。 格式如下所示：

```
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

每个函数的参数必须指向执行函数的线程所拥有的初始化的锁定变量。 如果该线程不拥有该锁，该行为不确定。

为一个简单的锁定，`omp_unset_lock`函数会释放该锁的所有权从执行该函数的线程。

可嵌套锁，`omp_unset_nest_lock`函数逐量减小嵌套计数和发布该锁的所有权从执行该函数，如果在生成的计数为零的线程。