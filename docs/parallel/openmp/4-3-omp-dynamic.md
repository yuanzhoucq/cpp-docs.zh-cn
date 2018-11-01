---
title: 4.3 OMP_DYNAMIC
ms.date: 11/04/2016
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
ms.openlocfilehash: 0ea6784159a11fc194d0c1cd16d2316a80b9cd37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488554"
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

**OMP_DYNAMIC**环境变量启用或禁用动态调整可用的并行区域执行的线程数，除非显式启用或禁用通过调用动态调整**omp_set_dynamic**库例程。 其值必须是 **，则返回 TRUE**或**FALSE**。

如果设置为 **，则返回 TRUE**，可能由运行时环境来充分地利用系统资源调整用于执行并行区域的线程数。  如果设置为**FALSE**，禁用动态调整。 默认条件是实现定义的。

示例:

```
setenv OMP_DYNAMIC TRUE
```

## <a name="cross-references"></a>交叉引用：

- 并行区域的详细信息，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页。

- **omp_set_dynamic**函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。