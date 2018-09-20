---
title: 3.2.1 omp_init_lock 和 omp_init_nest_lock 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4303eb3ccfcb1c449022a4be32f94b9f91e6e80c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386998"
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函数

这些函数提供初始化锁的唯一方式。 每个函数初始化与参数关联的锁*锁*以便在后续调用中使用。 格式如下所示：

```
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初始状态处于解锁状态 （即，没有任何线程拥有该锁）。 可嵌套锁，初始嵌套计数为零。 它不符合任一这些例程使用锁的变量已初始化的调用。