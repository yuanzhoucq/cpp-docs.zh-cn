---
title: E. OpenMP C/C++ 中实现定义的行为
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: e866eee9c6d85e93388f9f1d086badf948e2600e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215041"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. OpenMP C/C++ 中实现定义的行为

本附录汇总了在此 API 中描述为 "实现定义的" 的行为。  在主规范中，每个行为均交叉引用到其说明。

## <a name="remarks"></a>备注

在这些情况下，实现需要定义并记录其行为，但此列表可能不完整。

- **线程数：** 如果在对线程数进行动态调整时遇到并行区域，并且并行区域请求的线程数大于运行时系统可以提供的数目，则该程序的行为是实现定义的（请参阅第9页）。

   在视觉C++对象中，对于非嵌套并行区域，将提供64线程（最大值）。

- **处理器数量：** 在任意给定时间，实际承载线程的物理处理器的数量是实现定义的（请参阅第10页）。

   在视觉C++对象中，此数字不是常量，由操作系统控制。

- **创建线程团队：** 执行嵌套并行区域的团队中的线程数是实现定义的（请参阅第10页）。

   在视觉C++对象中，此数字由操作系统确定。

- **计划（运行时）：** 有关计划的决策将推迟到运行时。 可以通过设置 `OMP_SCHEDULE` 环境变量在运行时选择计划类型和块区大小。 如果未设置此环境变量，则生成的计划是实现定义的（请参阅第13页）。

   在视觉C++对象中，计划类型为 `static`，无区块大小。

- **默认计划：** 如果缺少 schedule 子句，则默认计划为实现定义（请参阅第13页）。

   在视觉C++对象中，默认计划类型为 `static`，无区块大小。

- **原子：** 它的实现定义了实现是否将所有 `atomic` 指令替换为具有相同唯一名称的 `critical` 指令（请参阅第20页）。

   在视觉C++对象中，如果[原子](reference/openmp-directives.md#atomic)修改的数据不是自然对齐，或者它的长度为1或2个字节，则满足该属性的所有原子操作都将使用一个关键部分。 否则，不会使用临界区。

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function)：** 如果用户尚未显式设置线程数，则默认值为实现定义（请参阅第9页）。

   在视觉C++对象中，线程的默认数目等于处理器数。

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)：** 动态线程调整的默认值是实现定义的。

   在视觉C++对象中，默认值为 `FALSE`。

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)：** 当启用嵌套并行时，用于执行嵌套并行区域的线程的数目是实现定义的。

   在视觉C++对象中，线程数由操作系统决定。

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)环境变量：此环境变量的默认值是实现定义的。

   在视觉C++对象中，计划类型为 `static`，无区块大小。

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)环境变量：如果未指定 `OMP_NUM_THREADS` 环境变量的值，或者指定的值不是正整数，或者值大于系统可以支持的最大线程数，则使用的线程数是实现定义的。

   在视觉C++对象中，如果指定的值为零或更小，则线程数等于处理器数。  如果值大于64，则线程数为64。

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)环境变量：默认值是实现定义的。

   在视觉C++对象中，默认值为 `FALSE`。
