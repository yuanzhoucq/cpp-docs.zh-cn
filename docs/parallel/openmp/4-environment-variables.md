---
title: 4. 环境变量
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: e93c59654c17ed6dbfb7483ac2dce716ce24b52a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370263"
---
# <a name="4-environment-variables"></a>4. 环境变量

本章介绍 OpenMP C 和C++控制并行代码执行的 API 环境变量（或类似特定于平台的机制）。  环境变量的名称必须为大写。 分配给它们的值不区分大小写，并且可能具有前导空格和尾随空格。  程序启动后对值的修改将被忽略。

环境变量如下所示：

- [OMP_SCHEDULE](#41-omp_schedule)设置运行时计划类型和区块大小。
- [OMP_NUM_THREADS](#42-omp_num_threads)设置执行期间要使用的线程数。
- [OMP_DYNAMIC](#43-omp_dynamic)启用或禁用线程数的动态调整。
- [OMP_NESTED](#44-omp_nested)启用或禁用嵌套并行性。

本章中的示例仅演示如何在 Unix C 外壳 （csh） 环境中设置这些变量。 在 Korn 外壳和 DOS 环境中，操作类似：

csh：  
`setenv OMP_SCHEDULE "dynamic"`

ksh：  
`export OMP_SCHEDULE="dynamic"`

Dos：  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE`仅适用于 具有`for`计划`parallel for`类型的`runtime`和 指令。 可在运行时设置所有此类循环的计划类型和区块大小。 将此环境变量设置为任何已识别的计划类型和可选*chunk_size。*

将`for`忽略`parallel for`具有 计划类型而不是`runtime`的`OMP_SCHEDULE`和 指令。 此环境变量的默认值是实现定义。 如果设置了可选*chunk_size，* 则该值必须为正。 如果未设置*chunk_size，* 则假定值为 1，但计划为`static`时除外。 对于`static`计划，默认区块大小设置为循环迭代空间除以应用于循环的线程数。

示例：

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>交叉引用

- [用于](2-directives.md#241-for-construct)指令
- [指令的并行](2-directives.md#251-parallel-for-construct)

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

环境`OMP_NUM_THREADS`变量设置执行期间要使用的默认线程数。 `OMP_NUM_THREADS`如果通过调用库例程显式更改该号码，`omp_set_num_threads`则忽略该编号。 如果指令上有显式`num_threads`子句，`parallel`也会忽略它。

`OMP_NUM_THREADS`环境变量的值必须为正整数。 其效果取决于是否启用了线程数的动态调整。 有关`OMP_NUM_THREADS`环境变量和线程动态调整之间交互的一套全面规则，请参阅[第 2.3 节](2-directives.md#23-parallel-construct)。

在以下情况下，要使用的线程数是实现定义的：

- 未`OMP_NUM_THREADS`指定环境变量，
- 指定的值不是正整数，或
- 该值大于系统可以支持的最大线程数。

示例：

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>交叉引用

- [num_threads](2-directives.md#23-parallel-construct)条款
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)功能
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)功能

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

环境`OMP_DYNAMIC`变量启用或禁用可用于执行并行区域的线程数的动态调整。 `OMP_DYNAMIC`当通过调用库例程显式启用或禁用动态调整时，`omp_set_dynamic`将忽略。 其值必须为`TRUE``FALSE`或 。

如果`OMP_DYNAMIC`设置为`TRUE`，则用于执行并行区域的线程数可能由运行时环境调整，以最佳使用系统资源。  如果`OMP_DYNAMIC`设置为`FALSE`，则禁用动态调整。 默认条件为实现定义。

示例：

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>交叉引用

- [平行区域](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)功能

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a>4.4 OMP_NESTED

除非`OMP_NESTED`通过调用`omp_set_nested`库例程启用或禁用嵌套并行性，否则环境变量将启用或禁用嵌套并行性。 如果`OMP_NESTED`设置为`TRUE`，则启用嵌套并行性。 如果`OMP_NESTED`设置为`FALSE`，则嵌套并行性将禁用。 默认值为 `FALSE`。

示例：

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>交叉引用

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)功能
