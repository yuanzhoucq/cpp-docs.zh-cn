---
title: 3.1.2 omp_get_num_threads 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 512c09b0cf71a7fd9c7438b6f9cceb9f16126718
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424972"
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads 函数

**Omp_get_num_threads**函数返回的线程数当前团队执行并行区域在调用它。 格式如下所示：

```
#include <omp.h>
int omp_get_num_threads(void);
```

**Num_threads**子句**omp_set_num_threads**函数，并且**OMP_NUM_THREADS**环境变量控制团队中的线程数。

如果线程数具有未显式设置用户，默认值是实现定义的。 此函数将绑定到最接近封闭**并行**指令。 如果从串行一部分的程序，或从序列化的嵌套并行区域调用，此函数将返回 1。

## <a name="cross-references"></a>交叉引用：

- **OMP_NUM_THREADS**环境变量，请参阅[4.2 节](../../parallel/openmp/4-2-omp-num-threads.md)第 48 页。

- **num_threads**子句，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页。

- **并行**构造，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页。