---
title: 3.2.5 omp_test_lock 和 omp_test_nest_lock 函数
ms.date: 11/04/2016
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
ms.openlocfilehash: e8e03699f807f23f139075560592d8846467f2c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512744"
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