---
title: 3.1.7 omp_set_dynamic 函数
ms.date: 11/04/2016
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
ms.openlocfilehash: 641b2ecfdb19aec9387aa299d22a041f25b22929
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492932"
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic 函数

**Omp_set_dynamic**函数启用或禁用动态调整可用的并行区域执行的线程数。 格式如下所示：

```
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*的计算结果为非零值，用于执行后续并行区域的线程数可能会自动调整由运行时环境来充分地利用系统资源。 因此，由用户指定的线程数是最大线程数。 团队执行并行区域中的线程数持续时间内该并行区域中保持不变，并通过报告**omp_get_num_threads**函数。

如果*dynamic_threads*的计算结果为 0，禁用动态调整。

此函数将产生影响时从该程序的一部分调用上述其中**omp_in_parallel**函数将返回零。 如果它从该程序的一部分调用其中**omp_in_parallel**函数将返回一个非零值，此函数的行为是未定义。

调用**omp_set_dynamic**优先于**OMP_DYNAMIC**环境变量。

指动态调整的线程的默认值是实现定义的。 因此，依赖于特定数量的线程的正确执行用户代码应显式禁用动态线程。 实现不需要提供的功能可以动态调整线程数，但需要它们来提供接口，以支持跨所有平台的可移植性。

## <a name="cross-references"></a>交叉引用：

- **omp_get_num_threads**函数中，请参阅[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 页上。

- **OMP_DYNAMIC**环境变量，请参阅[4.3 节](../../parallel/openmp/4-3-omp-dynamic.md)49 页上。

- **omp_in_parallel**函数中，请参阅[部分 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)第 38 页上。