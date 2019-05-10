---
title: E. OpenMP C 中实现定义的行为 /C++
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 3d8e9493cad1fce02e5d482cd5e612afb44bb37b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362748"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. OpenMP C 中实现定义的行为 /C++

本附录总结了被描述为"实现定义"此 API 中的行为。  每个行为是交叉引用回为其主规范中的说明。

## <a name="remarks"></a>备注

实现所需定义并记录在这些情况下，其行为，但此列表可能不完整。

- **线程数：** 如果禁用动态调整线程数，并为并行区域请求的线程数不只是运行时系统可以提供的号时遇到并行区域，则该程序的行为是实现定义的 （请参阅第 9 页）。

   视觉对象中C++，对于非嵌套并行区域中，将提供 64 个线程 （最大）。

- **处理器数：** 在任何给定时间实际托管线程的物理处理器的数目是实现定义的 （请参阅第 10 页）。

   视觉对象中C++，此数字不是常量，并由操作系统控制。

- **创建的线程的团队：** 执行嵌套并行区域在团队中的线程数是实现定义的 （请参阅第 10 页）。

   视觉对象中C++，此数量由操作系统。

- **schedule （runtime):** 有关计划的决定推迟到运行时。 可以通过设置在运行时选择的计划类型和区块大小`OMP_SCHEDULE`环境变量。 如果未设置此环境变量，生成的计划是实现定义的 （请参阅第 13 页）。

   视觉对象中C++，计划类型是`static`与没有块区大小。

- **默认计划：** 在没有 schedule 子句的情况下，默认计划是实现定义的 （请参阅第 13 页）。

   视觉对象中C++，默认计划类型是`static`与没有块区大小。

- **原子：** 它是实现定义的实现是否替换所有`atomic`指令与`critical`具有相同的唯一名称 （请参阅第 20 页） 的指令。

   视觉对象中C++，如果通过修改数据[原子](reference/openmp-directives.md#atomic)不在自然对齐，或如果它是一个或两个字节长时间，满足该属性的所有原子操作将使用一个关键部分。 否则，不会使用关键部分。

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** 如果用户未显式设置的线程数，默认值是实现定义的 （请参阅第 9 页）。

   视觉对象中C++，默认线程数等于处理器数。

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** 动态线程调整的默认值是实现定义的。

   视觉对象中C++，默认值是`FALSE`。

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** 启用嵌套的并行度，用来执行嵌套并行区域的线程数是实现定义的。

   视觉对象中C++，由操作系统确定的线程数。

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)环境变量：此环境变量的默认值是实现定义的。

   视觉对象中C++，计划类型是`static`与没有块区大小。

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)环境变量：如果未指定值为`OMP_NUM_THREADS`环境变量，或如果指定的值不是一个正整数，或值大于最大的系统可以支持的线程数，如果要使用的线程数是实现定义的。

   视觉对象中C++，如果指定的值为零或更低，线程数等于处理器数。  如果值大于 64，线程数为 64。

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)环境变量：默认值是实现定义的。

   视觉对象中C++，默认值是`FALSE`。