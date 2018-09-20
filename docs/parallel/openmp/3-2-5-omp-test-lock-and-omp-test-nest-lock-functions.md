---
title: 3.2.5 omp_test_lock 和 omp_test_nest_lock 函数 |Microsoft Docs
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
ms.openlocfilehash: 5349134bf92f407d4b65df9b92e3eebe87c097c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426141"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函数

这些函数尝试设置一个锁，但不是会阻止线程的执行。 格式如下所示：

```
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

自变量必须指向初始化的锁定变量。 这些函数尝试将锁设置为相同的方式`omp_set_lock`和`omp_set_nest_lock`，只不过它们不会阻止线程的执行。

为一个简单的锁定，`omp_test_lock`函数返回非零值，如果锁已成功设置; 否则，它将返回零。

可嵌套锁，`omp_test_nest_lock`函数返回新的嵌套计数，如果锁已成功设置; 否则，它将返回零。