---
title: 3.1.9 omp_set_nested 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 68e5898b8b57814a152ca2ce9ced84a9df8190cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414532"
---
# <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested 函数

**Omp_set_nested**函数启用或禁用嵌套并行度。 格式如下所示：

```
#include <omp.h>
void omp_set_nested(int nested);
```

如果*嵌套*计算结果为 0，嵌套并行度处于禁用状态，这是默认设置，并嵌套并行区域进行序列化和执行由当前线程。 如果*嵌套*的计算结果为非零值，启用了嵌套并行度，并将其嵌套的并行区域可能部署以形成嵌套的团队的其他线程。

此函数将产生影响时从该程序的一部分调用上述其中**omp_in_parallel**函数将返回零。 如果它从该程序的一部分调用其中**omp_in_parallel**函数将返回一个非零值，此函数的行为是未定义。

此调用的优先级高于**OMP_NESTED**环境变量。

启用嵌套的并行度，用来执行嵌套并行区域的线程数是实现定义的。 因此，符合 OpenMP 的实现可以序列化嵌套并行区域，即使在启用了嵌套并行度。

## <a name="cross-references"></a>交叉引用：

- **OMP_NESTED**环境变量，请参阅[部分 4.4](../../parallel/openmp/4-4-omp-nested.md) 49 页上。

- **omp_in_parallel**函数中，请参阅[部分 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)第 38 页上。