---
title: 3.1.8 omp_get_dynamic 函数
ms.date: 11/04/2016
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
ms.openlocfilehash: d9476894e5aff4cc7bb9c67fbbeb14d185b65f5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566421"
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 函数

**Omp_get_dynamic**函数返回非零值，如果动态调整线程的已启用，否则返回 0。 格式如下所示：

```
#include <omp.h>
int omp_get_dynamic(void);
```

如果实现未实现动态调整线程数，此函数始终返回 0。

## <a name="cross-references"></a>交叉引用：

- 有关的动态线程调整说明，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。