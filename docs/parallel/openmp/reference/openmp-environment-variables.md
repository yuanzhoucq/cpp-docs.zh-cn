---
title: OpenMP 环境变量
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: bee9b0fbdf147ee962ff92d0b3b9ff57d4209f84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363875"
---
# <a name="openmp-environment-variables"></a>OpenMP 环境变量

提供指向 OpenMP API 中使用的环境变量的链接。

OpenMP 标准的可视化C++实现包括以下环境变量。 这些环境变量在程序启动时读取，并在运行时忽略对其值的修改（例如，使用[_putenv，_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)）。

|环境变量|说明|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|在`for`或`parallel for`指令中指定[计划子句](openmp-clauses.md#schedule)时`schedule(runtime)`修改其行为。|
|[OMP_NUM_THREADS](#omp-num-threads)|设置并行区域中的最大线程数，除非被[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)覆盖。|
|[OMP_DYNAMIC](#omp-dynamic)|指定 OpenMP 运行时是否可以调整并行区域中的线程数。|
|[OMP_NESTED](#omp-nested)|指定是否启用嵌套并行性，除非启用嵌套并行性或使用 禁用`omp_set_nested`|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a>OMP_DYNAMIC

指定 OpenMP 运行时是否可以调整并行区域中的线程数。

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>备注

`OMP_DYNAMIC`环境变量可以由[omp_set_dynamic](openmp-functions.md#omp-set-dynamic)函数覆盖。

OpenMP 标准的视觉C++实现的默认值为`OMP_DYNAMIC=FALSE`。

有关详细信息，请参阅[4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

### <a name="example"></a>示例

以下命令将`OMP_DYNAMIC`环境变量设置为 TRUE：

```cmd
set OMP_DYNAMIC=TRUE
```

以下命令显示环境变量的`OMP_DYNAMIC`当前设置：

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a>OMP_NESTED

指定是否启用嵌套并行性，除非启用嵌套并行性或使用 禁用`omp_set_nested`

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>备注

环境`OMP_NESTED`变量可以由[omp_set_nested](openmp-functions.md#omp-set-nested)函数覆盖。

OpenMP 标准的视觉C++实现的默认值为`OMP_DYNAMIC=FALSE`。

有关详细信息，请参阅[4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。

### <a name="example"></a>示例

以下命令将`OMP_NESTED`环境变量设置为 TRUE：

```cmd
set OMP_NESTED=TRUE
```

以下命令显示环境变量的`OMP_NESTED`当前设置：

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a>OMP_NUM_THREADS

设置并行区域中的最大线程数，除非被[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)覆盖。

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>参数

*num*<br/>
并行区域中所需的最大线程数，在 Visual C++实现中最多 64 个线程。

### <a name="remarks"></a>备注

`OMP_NUM_THREADS`环境变量可以由[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)函数或[num_threads](openmp-clauses.md#num-threads)覆盖。

OpenMP 标准的`num`可视化C++实现的默认值是虚拟处理器的数量，包括超线程 CPU。

有关详细信息，请参阅[4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。

### <a name="example"></a>示例

以下命令将`OMP_NUM_THREADS`环境变量设置为`16`：

```cmd
set OMP_NUM_THREADS=16
```

以下命令显示环境变量的`OMP_NUM_THREADS`当前设置：

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a>OMP_SCHEDULE

在`for`或`parallel for`指令中指定[计划子句](openmp-clauses.md#schedule)时`schedule(runtime)`修改其行为。

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>参数

*大小*<br/>
（可选）指定迭代的大小。 *大小*必须为正整数。 默认值为`1`，除非*类型*为静态。 *当类型*为`runtime`时无效。

*type*<br/>
计划类型`dynamic`，或 、、`guided``runtime`或`static`。

### <a name="remarks"></a>备注

OpenMP 标准的视觉C++实现的默认值为`OMP_SCHEDULE=static,0`。

有关详细信息，请参阅[4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。

### <a name="example"></a>示例

以下命令设置`OMP_SCHEDULE`环境变量：

```cmd
set OMP_SCHEDULE="guided,2"
```

以下命令显示环境变量的`OMP_SCHEDULE`当前设置：

```cmd
set OMP_SCHEDULE
```
