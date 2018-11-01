---
title: E. 实现定义的行为在 OpenMP C/c + +
ms.date: 11/04/2016
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 704062f36102a06e6e7b8cf015f6330f925a6bba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619344"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. 实现定义的行为在 OpenMP C/c + +

本附录总结了被描述为"实现定义"此 API 中的行为。  每个行为是交叉引用回为其主规范中的说明。

## <a name="remarks"></a>备注

实现所需定义并记录在这些情况下，其行为，但此列表可能不完整。

- **线程数：** 如果遇到并行区域则禁用动态调整线程数，而为并行区域请求的线程数超过了运行时系统可以提供的行为数量该程序是实现定义的 （请参阅第 9 页）。

   在 Visual c + +，对于非嵌套并行区域中，64 个线程 （最大值） 将提供。

- **处理器数：** 实际上在任何给定时间托管线程的物理处理器的数目是实现定义的 （请参阅第 10 页）。

   在 Visual c + +，此数字不是常量，并由操作系统控制。

- **创建的线程的团队：** 执行嵌套并行区域在团队中的线程数是实现定义。 (请参见页 10）。

   Visual c + +，这是由操作系统决定。

- **schedule （runtime):** 有关计划推迟到运行时的决定。 可以通过设置在运行时选择的计划类型和区块大小`OMP_SCHEDULE`环境变量。 如果未设置此环境变量，生成的计划是实现定义的 （请参阅第 13 页）。

   在 Visual c + +，计划类型是`static`与没有块区大小。

- **默认计划：** 缺少 schedule 子句的情况下，默认计划是实现定义的 （请参阅第 13 页）。

   在 Visual c + +，默认计划类型是`static`与没有块区大小。

- **ATOMIC:** 它是实现定义的实现是否替换所有`atomic`指令与**关键**具有相同的唯一名称 （请参阅第 20 页） 的指令。

   在 Visual c + +，如果通过修改数据[原子](../../parallel/openmp/reference/atomic.md)不在自然对齐或如果它为 1 或 2 个字节长时间的所有原子操作，满足该属性将使用一个关键部分。 否则，将不使用临界区。

- **omp_get_num_threads:** 如果线程数具有未显式设置用户，默认值是实现定义的 (请参阅页 9，并[部分 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)第 37 页上)。

   Visual c + + 中的默认线程数等于处理器数。

- **omp_set_dynamic:** 是实现定义的动态线程调整的默认值 (请参阅[部分 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)第 39 页上)。

   在 Visual c + +，默认值是`FALSE`。

- **omp_set_nested:** 时启用了嵌套并行机制，用于执行嵌套并行区域的线程数是实现定义的 (请参阅[部分 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 40 页上)。

   在 Visual c + +，由操作系统确定的线程数。

- `OMP_SCHEDULE` 环境变量： 此环境变量的默认值是实现定义的 (请参阅[第 4.1 节](../../parallel/openmp/4-1-omp-schedule.md)第 48 页)。

   在 Visual c + +，计划类型是`static`与没有块区大小。

- `OMP_NUM_THREADS` 环境变量： 如果没有值指定为`OMP_NUM_THREADS`环境变量，或如果指定的值不是一个正整数，或如果值大于最大的系统可以支持的线程数，是要使用的线程数实现定义 (请参阅[4.2 节](../../parallel/openmp/4-2-omp-num-threads.md)第 48 页)。

   在 Visual c + +，如果未指定值为零或更低，线程数等于处理器数。  如果值大于 64，线程数为 64。

- `OMP_DYNAMIC` 环境变量： 是实现定义的默认值 (请参阅[4.3 节](../../parallel/openmp/4-3-omp-dynamic.md)页 49 上)。

   在 Visual c + +，默认值是`FALSE`。