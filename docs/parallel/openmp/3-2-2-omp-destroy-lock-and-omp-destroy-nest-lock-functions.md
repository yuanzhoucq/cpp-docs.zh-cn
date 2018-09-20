---
title: 3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d334907d-94f7-4bbf-b20e-41d53484cbff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b7b762614e406e5fb4497ec901ad8f65dae15a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433863"
---
# <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函数

这些函数，请确保所指向的锁定变量*锁*未初始化。 格式如下所示：

```
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

它不符合任一这些例程使用锁的变量未初始化或已解锁的调用。