---
title: 4. 环境变量
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882845"
---
# <a name="4-environment-variables"></a>4. 环境变量

本章介绍了控制并行代码执行C++的 OpenMP C 和 API 环境变量（或类似于平台的机制）。  环境变量的名称必须为大写。 赋予它们的值不区分大小写，并且可能具有前导空格和尾随空格。  在程序启动后对值所做的修改将被忽略。

环境变量如下所示：

- [OMP_SCHEDULE](#41-omp_schedule)设置运行时计划类型和块区大小。
- [OMP_NUM_THREADS](#42-omp_num_threads)设置执行期间要使用的线程数。
- [OMP_DYNAMIC](#43-omp_dynamic)允许或禁止动态调整线程数。
- [OMP_NESTED](#44-omp_nested)启用或禁用嵌套并行度。

本章中的示例仅演示如何在 Unix C shell （csh）环境中设置这些变量。 在 Korn shell 和 DOS 环境中，操作类似于：

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh  
`export OMP_SCHEDULE="dynamic"`

造成  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` 仅适用于计划类型 `runtime`的 `for` 和 `parallel for` 指令。 所有此类循环的计划类型和块区大小都可以在运行时设置。 将此环境变量设置为任何已识别的计划类型和可选*chunk_size*。

对于其计划类型不是 `runtime`的 `for` 和 `parallel for` 指令，`OMP_SCHEDULE` 将被忽略。 此环境变量的默认值是实现定义的。 如果设置了可选的*chunk_size* ，则该值必须为正数。 如果未设置*chunk_size* ，则将假定值为1，除非 `static`计划。 对于 `static` 计划，默认块区大小设置为循环迭代空间除以应用于循环的线程数。

示例：

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>交叉引用

- [for](2-directives.md#241-for-construct)指令
- [对指令并行](2-directives.md#251-parallel-for-construct)

## <a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS` 环境变量设置要在执行过程中使用的默认线程数。 如果通过调用 `omp_set_num_threads` 库例程来显式更改该数字，则将忽略 `OMP_NUM_THREADS`。 如果 `parallel` 指令上存在显式 `num_threads` 子句，则此方法也将被忽略。

`OMP_NUM_THREADS` 环境变量的值必须是一个正整数。 其效果取决于是否启用了动态调整线程数。 有关 `OMP_NUM_THREADS` 环境变量与线程动态调整之间的交互的综合规则集，请参阅[2.3 节](2-directives.md#23-parallel-construct)。

要使用的线程数为实现定义的值（如果：

- 未指定 `OMP_NUM_THREADS` 环境变量，
- 指定的值不是正整数，或
- 值大于系统可以支持的最大线程数。

示例：

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>交叉引用

- [num_threads](2-directives.md#23-parallel-construct)子句
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)函数
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)函数

## <a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC` 环境变量启用或禁用对并行区域执行可用线程数的动态调整。 当通过调用 `omp_set_dynamic` 库例程显式启用或禁用动态调整时，将忽略 `OMP_DYNAMIC`。 其值必须 `TRUE` 或 `FALSE`。

如果 `OMP_DYNAMIC` 设置为 `TRUE`，运行时环境可能会调整用于执行并行区域的线程的数量，以最好地使用系统资源。  如果 `OMP_DYNAMIC` 设置为 `FALSE`，则禁用动态调整。 默认条件是实现定义的。

示例：

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>交叉引用

- [并行区域](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)函数

## <a name="44-omp_nested"></a>4.4 OMP_NESTED

`OMP_NESTED` 环境变量启用或禁用嵌套并行性，除非通过调用 `omp_set_nested` 库例程启用或禁用嵌套并行度。 如果 `OMP_NESTED` 设置为 `TRUE`，则会启用嵌套并行度。 如果 `OMP_NESTED` 设置为 `FALSE`，则将禁用嵌套并行度。 默认值为 `FALSE`。

示例：

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>交叉引用

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)函数
