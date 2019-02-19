---
title: 4. 环境变量
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 966e4466f10c93fc12faf33d28e03b39489423fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987051"
---
# <a name="4-environment-variables"></a>4.环境变量

本章节介绍了 OpenMP C 和 c + + API 环境变量 （或类似的特定于平台的机制），以控制并行代码的执行。  环境变量的名称必须为大写。 分配给它们的值是不区分大小写，并可能有前导和尾随空格。  程序启动后的值对的修改将被忽略。

环境变量如下所示：

- [OMP_SCHEDULE](#41-omp_schedule)设置运行时计划类型和块区大小。
- [OMP_NUM_THREADS](#42-omp_num_threads)设置要在执行期间使用的线程数。
- [OMP_DYNAMIC](#43-omp_dynamic)启用或禁用动态调整的线程数。
- [OMP_NESTED](#44-omp_nested)启用或禁用嵌套并行度。

这一章中的示例仅演示如何可能在 Unix C shell (csh) 环境中设置这些变量。 在 Korn shell 和 DOS 环境中，操作如下：

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` 仅适用于`for`并`parallel for`具有计划类型的指令`runtime`。 可以在运行时设置此类循环的计划类型和块区大小。 设置此环境变量，为任何已识别的计划类型和一个可选*使用 chunk_size*。

有关`for`并`parallel for`而不具有计划类型的指令`runtime`，`OMP_SCHEDULE`将被忽略。 此环境变量的默认值是实现定义的。 如果可选*使用 chunk_size*值必须为正数的设置。 如果*使用 chunk_size*未设置，假设的值为 1，除非该计划是`static`。 有关`static`计划，默认块区大小设置为循环迭代空间除以应用于循环的线程数。

示例:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>交叉引用

- [有关](2-directives.md#241-for-construct)指令
- [有关并行](2-directives.md#251-parallel-for-construct)指令

## <a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

`OMP_NUM_THREADS`环境变量设置线程在执行期间使用的默认值数。 `OMP_NUM_THREADS` 如果通过调用显式更改该数字，则忽略`omp_set_num_threads`库例程。 如果没有显式还忽略`num_threads`上的子句`parallel`指令。

值`OMP_NUM_THREADS`环境变量必须为正整数。 其效果取决于是否启用了动态调整线程数。 获取完整的有关之间的交互的规则集`OMP_NUM_THREADS`环境变量和动态调整线程，请参阅[第 2.3 节](2-directives.md#23-parallel-construct)。

要使用的线程数是实现定义如果：

- `OMP_NUM_THREADS`未指定环境变量，
- 指定的值不是一个正整数，或
- 值大于最大的系统可以支持的线程数。

示例:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>交叉引用

- [num_threads](2-directives.md#23-parallel-construct)子句
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)函数
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) function

## <a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

`OMP_DYNAMIC`环境变量启用或禁用动态调整的可用于并行区域执行的线程数。 `OMP_DYNAMIC` 动态调整是显式启用或禁用通过调用时，将忽略`omp_set_dynamic`库例程。 其值必须是`TRUE`或`FALSE`。

如果`OMP_DYNAMIC`设置为`TRUE`，可能由运行时环境以最佳方式使用系统资源调整用于执行并行区域的线程数。  如果`OMP_DYNAMIC`设置为`FALSE`，禁用动态调整。 默认条件是实现定义的。

示例:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>交叉引用

- [并行区域](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) function

## <a name="44-omp_nested"></a>4.4 OMP_NESTED

`OMP_NESTED`环境变量启用或禁用嵌套并行度，除非启用或禁用通过调用嵌套并行度`omp_set_nested`库例程。 如果`OMP_NESTED`设置为`TRUE`，启用了嵌套并行机制。 如果`OMP_NESTED`设置为`FALSE`、 嵌套禁用并行度。 默认值为 `FALSE`。

示例:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>交叉引用

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) function
