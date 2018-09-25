---
title: 3.1.1 omp_set_num_threads 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85f7ff733583e531b449caf2039817b71165da52
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426791"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads 函数

`omp_set_num_threads`函数设置默认线程要用于后续并行区域未指定的数`num_threads`子句。 格式如下所示：

```
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

参数的值*num_threads*必须为正整数。 其效果取决于是否启用了动态调整线程数。 获取完整的有关之间的交互的规则集`omp_set_num_threads`函数和动态调整线程，在第 8 页上看到 2.3 节。

此函数将产生影响时从该程序的一部分调用上述其中`omp_in_parallel`函数将返回零。 如果它从该程序的一部分调用其中`omp_in_parallel`函数将返回一个非零值，此函数的行为是未定义。

此调用的优先级高于`OMP_NUM_THREADS`环境变量。 可能由调用的线程数的默认值`omp_set_num_threads`或通过设置`OMP_NUM_THREADS`环境变量，可以显式重写的单个**并行**通过指定指令`num_threads`子句。

## <a name="cross-references"></a>交叉引用：

- `omp_set_dynamic` 函数中，请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上。

- `omp_get_dynamic` 函数中，请参阅[部分 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) 40 页上。

- `OMP_NUM_THREADS` 环境变量，请参阅[4.2 节](../../parallel/openmp/4-2-omp-num-threads.md)48，页和第 8 页第 2.3 节。

- `num_threads` 子句中，请参阅[2.3 节](../../parallel/openmp/2-3-parallel-construct.md)第 8 页