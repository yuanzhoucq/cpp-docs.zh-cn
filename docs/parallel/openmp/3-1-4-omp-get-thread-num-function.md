---
title: 3.1.4 omp_get_thread_num 函数
ms.date: 11/04/2016
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
ms.openlocfilehash: eca8522aeab4702be390d98faaf8920f2d732244
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480920"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num 函数

`omp_get_thread_num`函数将返回线程数，其团队中执行该函数的线程。 线程数作用在于它介于 0 和**omp_get_num_threads()**-1，非独占。 团队的主线程是线程 0。

格式如下所示：

```
#include <omp.h>
int omp_get_thread_num(void);
```

如果从串行区域中，调用`omp_get_thread_num`返回 0。 如果从调用序列化嵌套并行区域内，此函数将返回 0。

## <a name="cross-references"></a>交叉引用：

- `omp_get_num_threads` 函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 页上。