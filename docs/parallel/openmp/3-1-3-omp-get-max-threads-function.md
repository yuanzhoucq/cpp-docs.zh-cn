---
title: 3.1.3 omp_get_max_threads 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c439dc0203fa3435c62e9669da40b5b092556492
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400817"
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads 函数

**Omp_get_max_threads**函数返回一个整数，保证在至少与将用于形成一个组合，如果无需并行区域的线程数一样大**num_threads**子句已在该点遇到在代码中。 格式如下所示：

```
#include <omp.h>
int omp_get_max_threads(void);
```

以下各值表示下限**omp_get_max_threads**:

```

threads-used-for-next-team
<= omp_get_max_threads

```

请注意，如果使用后续的并行区域**num_threads**子句，以请求特定数量的线程上下限的结果的, 保证**omp_get_max_threads**不长的保留。

**Omp_get_max_threads**函数的返回值可用于动态分配足够的存储空间在后续的并行区域格式正确的团队中的所有线程。

## <a name="cross-references"></a>交叉引用：

- **omp_get_num_threads**函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 页上。

- **omp_set_num_threads**函数中，请参阅[部分 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)第 36 页上。

- **omp_set_dynamic**函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。

- **num_threads**子句，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页。