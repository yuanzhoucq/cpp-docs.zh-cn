---
title: OpenMP 环境变量 |Microsoft Docs
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 395494431c3942832a64cf64c9c150f643389062
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990225"
---
# <a name="openmp-environment-variables"></a>OpenMP 环境变量

提供指向 OpenMP API 中使用的环境变量。

OpenMP 标准的 Visual c + + 实现包括以下环境变量。 在程序启动时读取这些环境变量和它们的值对的修改将忽略在运行时 (例如，使用[_putenv、 _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md))。

环境变量                | 描述
----------------------------------- | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[OMP_DYNAMIC](#omp-dynamic)         | 指定 OpenMP 运行时是否可以调整并行区域中的线程数。
[OMP_NESTED](#omp-nested)           | 指定是否已启用嵌套的并行度，除非启用或禁用与嵌套并行度`omp_set_nested`。
[OMP_NUM_THREADS](#omp-num-threads) | 并行区域中设置的最大线程数，除非被重写[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num_threads](openmp-clauses.md#num-threads)。
[OMP_SCHEDULE](#omp-schedule)       | 修改的行为[计划](openmp-clauses.md#schedule)子句时`schedule(runtime)`中指定`for`或`parallel for`指令。

## <a name="omp-dynamic"></a>OMP_DYNAMIC

指定 OpenMP 运行时是否可以调整并行区域中的线程数。

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>备注

`OMP_DYNAMIC`环境变量可以通过重写[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)函数。

OpenMP 标准的 Visual c + + 实现中的默认值是`OMP_DYNAMIC=FALSE`。

有关详细信息，请参阅[4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md)。

### <a name="example"></a>示例

下面的命令集`OMP_DYNAMIC`为 TRUE 的环境变量：

```
set OMP_DYNAMIC=TRUE
```

下面的命令显示的当前设置`OMP_DYNAMIC`环境变量：

```
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

指定是否已启用嵌套的并行度，除非启用或禁用与嵌套并行度`omp_set_nested`。

```
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>备注

`OMP_NESTED`环境变量可以通过重写[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)函数。

OpenMP 标准的 Visual c + + 实现中的默认值是`OMP_DYNAMIC=FALSE`。

有关详细信息，请参阅[4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md)。

### <a name="example"></a>示例

下面的命令集`OMP_NESTED`为 TRUE 的环境变量：

```
set OMP_NESTED=TRUE
```

下面的命令显示的当前设置`OMP_NESTED`环境变量：

```
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

并行区域中设置的最大线程数，除非被重写[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num_threads](openmp-clauses.md#num-threads)。

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>参数

*num*<br/>
最大并行区域，最多为 64 在 Visual c + + 实现中所需的线程数。

### <a name="remarks"></a>备注

`OMP_NUM_THREADS`环境变量可以通过重写[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函数或通过[num_threads](openmp-clauses.md#num-threads)。

默认值`num`Visual c + + 中实现的 OpenMP 标准是虚拟处理器，包括超线程 Cpu 的数量。

有关详细信息，请参阅[4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。

### <a name="example"></a>示例

下面的命令集`OMP_NUM_THREADS`为 16 的环境变量：

```
set OMP_NUM_THREADS=16
```

下面的命令显示的当前设置`OMP_NUM_THREADS`环境变量：

```
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

修改的行为[计划](openmp-clauses.md#schedule)子句时`schedule(runtime)`中指定`for`或`parallel for`指令。

```
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>参数

*size*<br/>
（可选）指定的迭代的大小。 `size` 必须为正整数。 默认值为 1，除非当`type`是静态的。 时未有效`type`是`runtime`。

*type*<br/>
计划的类型：

- `dynamic`
- `guided`
- `runtime`
- `static`

### <a name="remarks"></a>备注

OpenMP 标准的 Visual c + + 实现中的默认值是`OMP_SCHEDULE=static,0`。

有关详细信息，请参阅[4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md)。

### <a name="example"></a>示例

下面的命令集`OMP_SCHEDULE`环境变量：

```
set OMP_SCHEDULE="guided,2"
```

下面的命令显示的当前设置`OMP_SCHEDULE`环境变量：

```
set OMP_SCHEDULE
```
