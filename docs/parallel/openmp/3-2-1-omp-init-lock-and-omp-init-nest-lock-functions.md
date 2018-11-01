---
title: 3.2.1 omp_init_lock 和 omp_init_nest_lock 函数
ms.date: 11/04/2016
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
ms.openlocfilehash: 2d15aacb5e6743d18150fb45bea85b7ca22a401f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472770"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函数

这些函数提供初始化锁的唯一方式。 每个函数初始化与参数关联的锁*锁*以便在后续调用中使用。 格式如下所示：

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初始状态处于解锁状态 （即，没有任何线程拥有该锁）。 可嵌套锁，初始嵌套计数为零。 它不符合任一这些例程使用锁的变量已初始化的调用。