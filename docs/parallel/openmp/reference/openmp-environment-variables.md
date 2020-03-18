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
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424127"
---
# <a name="openmp-environment-variables"></a>OpenMP 环境变量

提供 OpenMP API 中使用的环境变量的链接。

OpenMP 标准C++的可视化实现包括以下环境变量。 这些环境变量将在程序启动时读取，在运行时将忽略对其值的修改（例如，使用[_putenv，_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)）。

|环境变量|说明|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|当在 `for` 或 `parallel for` 指令中指定 `schedule(runtime)` 时，修改[schedule](openmp-clauses.md#schedule)子句的行为。|
|[OMP_NUM_THREADS](#omp-num-threads)|设置并行区域中的最大线程数，除非由[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)重写。|
|[OMP_DYNAMIC](#omp-dynamic)|指定 OpenMP 运行时是否可以调整并行区域中的线程数。|
|[OMP_NESTED](#omp-nested)|指定是否启用嵌套并行，除非启用或禁用了嵌套并行 `omp_set_nested`。|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

指定 OpenMP 运行时是否可以调整并行区域中的线程数。

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>备注

[Omp_set_dynamic](openmp-functions.md#omp-set-dynamic)函数可以重写 `OMP_DYNAMIC` 环境变量。

OpenMP 标准的可视化C++实现中的默认值为 `OMP_DYNAMIC=FALSE`。

有关详细信息，请参阅[4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

### <a name="example"></a>示例

以下命令将 `OMP_DYNAMIC` 环境变量设置为 TRUE：

```cmd
set OMP_DYNAMIC=TRUE
```

以下命令显示 `OMP_DYNAMIC` 环境变量的当前设置：

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

指定是否启用嵌套并行，除非启用或禁用了嵌套并行 `omp_set_nested`。

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>备注

[Omp_set_nested](openmp-functions.md#omp-set-nested)函数可以重写 `OMP_NESTED` 环境变量。

OpenMP 标准的可视化C++实现中的默认值为 `OMP_DYNAMIC=FALSE`。

有关详细信息，请参阅[4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。

### <a name="example"></a>示例

以下命令将 `OMP_NESTED` 环境变量设置为 TRUE：

```cmd
set OMP_NESTED=TRUE
```

以下命令显示 `OMP_NESTED` 环境变量的当前设置：

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

设置并行区域中的最大线程数，除非由[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)或[num_threads](openmp-clauses.md#num-threads)重写。

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>parameters

*num*<br/>
并行区域中所需的最大线程数，在可视化C++实现中最大为64。

### <a name="remarks"></a>备注

`OMP_NUM_THREADS` 环境变量可由[omp_set_num_threads](openmp-functions.md#omp-set-num-threads)函数或[num_threads](openmp-clauses.md#num-threads)重写。

OpenMP 标准的可视化C++实现中 `num` 的默认值是虚拟处理器的数量，包括超线程 cpu。

有关详细信息，请参阅[4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。

### <a name="example"></a>示例

以下命令将 `OMP_NUM_THREADS` 环境变量设置为 `16`：

```cmd
set OMP_NUM_THREADS=16
```

以下命令显示 `OMP_NUM_THREADS` 环境变量的当前设置：

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

当在 `for` 或 `parallel for` 指令中指定 `schedule(runtime)` 时，修改[schedule](openmp-clauses.md#schedule)子句的行为。

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>parameters

size<br/>
可有可无指定迭代的大小。 *大小*必须为正整数。 默认值为 `1`，除非*类型*为 static。 当*类型*为 `runtime`时无效。

type<br/>
计划的类型，`dynamic`、`guided`、`runtime`或 `static`。

### <a name="remarks"></a>备注

OpenMP 标准的可视化C++实现中的默认值为 `OMP_SCHEDULE=static,0`。

有关详细信息，请参阅[4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。

### <a name="example"></a>示例

以下命令设置 `OMP_SCHEDULE` 环境变量：

```cmd
set OMP_SCHEDULE="guided,2"
```

以下命令显示 `OMP_SCHEDULE` 环境变量的当前设置：

```cmd
set OMP_SCHEDULE
```
