---
title: 3. 运行时库函数
ms.date: 01/17/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 4e72d2d74bb26f8eeeb422881cabf92630cced43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363227"
---
# <a name="3-run-time-library-functions"></a>3.运行时库函数

本部分介绍了 OpenMP C 和C++运行时库函数。 标头 **\<omp.h >** 声明两种类型，可用于控制和查询并行执行环境，并锁定可用于同步对数据的访问的函数的几个函数。

类型`omp_lock_t`是一种对象类型能够表示锁定就可用，或一个线程拥有的锁。 这些锁嘿*简单锁*。

类型`omp_nest_lock_t`是一种对象类型能够表示任一的锁定就是可用，或这两个线程的标识拥有锁和一个*嵌套计数*（如下所述）。 这些锁嘿*可嵌套锁*。

库函数是使用"C"链接的外部函数。

本章说明分为以下主题：

- [执行环境函数](#31-execution-environment-functions)
- [Lock 函数](#32-lock-functions)
- [计时例程](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 执行环境函数

在本部分中所述的函数会影响，并监视线程、 处理器和并行环境：

- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_get_max_threads](#313-omp_get_max_threads-function)
- [omp_get_thread_num](#314-omp_get_thread_num-function)
- [omp_get_num_procs](#315-omp_get_num_procs-function)
- [omp_in_parallel](#316-omp_in_parallel-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [omp_get_dynamic](#318-omp_get_dynamic-function)
- [omp_set_nested](#319-omp_set_nested-function)
- [omp_get_nested](#3110-omp_get_nested-function)

### <a name="311-ompsetnumthreads-function"></a>3.1.1 omp_set_num_threads 函数

`omp_set_num_threads`函数设置默认线程用于更高版本中没有指定并行区域数`num_threads`子句。 格式如下所示：

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

参数的值*num_threads*必须为正整数。 其效果取决于是否启用了动态调整线程数。 获取完整的有关之间的交互的规则集`omp_set_num_threads`函数，并动态调整线程，请参阅[第 2.3 节](2-directives.md#23-parallel-construct)。

此函数将产生影响时从该程序的一部分调用上述其中`omp_in_parallel`函数将返回零。 如果从该程序的一部分调用其中`omp_in_parallel`函数将返回一个非零值，此函数的行为是未定义。

此调用的优先级高于`OMP_NUM_THREADS`环境变量。 可能由调用的线程数的默认值`omp_set_num_threads`或通过设置`OMP_NUM_THREADS`环境变量，可以显式重写的单个`parallel`指令通过指定`num_threads`子句。

#### <a name="cross-references"></a>交叉引用

- [omp_set_dynamic](#317-omp_set_dynamic-function) function
- [omp_get_dynamic](#318-omp_get_dynamic-function) function
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)环境变量
- [num_threads](2-directives.md#23-parallel-construct)子句

### <a name="312-ompgetnumthreads-function"></a>3.1.2 omp_get_num_threads 函数

`omp_get_num_threads`函数返回的线程数当前团队执行并行区域在调用它。 格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads`子句中，`omp_set_num_threads`函数，和`OMP_NUM_THREADS`环境变量控制团队中的线程数。

如果用户未显式设置的线程数，默认值是实现定义的。 此函数将绑定到最接近封闭`parallel`指令。 如果从串行一部分的程序，或从序列化的嵌套并行区域调用，此函数将返回 1。

#### <a name="cross-references"></a>交叉引用

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-ompgetmaxthreads-function"></a>3.1.3 omp_get_max_threads 函数

`omp_get_max_threads`函数返回一个整数，一定是至少与将用于形成一个组合，如果无需并行区域的线程数一样大`num_threads`子句已在该点出现在代码中。 格式如下所示：

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

以下各值表示下限`omp_get_max_threads`:

```

threads-used-for-next-team
<= omp_get_max_threads
```

请注意，是否另一并行区域使用`num_threads`子句，以请求特定数量的线程上下限的结果的, 保证`omp_get_max_threads`不长的保留。

`omp_get_max_threads`函数的返回值可用于动态分配足够的存储空间在下一并行区域格式正确的团队中的所有线程。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-ompgetthreadnum-function"></a>3.1.4 omp_get_thread_num 函数

`omp_get_thread_num`函数将返回线程数，其团队中执行该函数的线程。 线程数作用在于它介于 0 和`omp_get_num_threads()`-1，非独占。 团队的主线程是线程 0。

格式如下所示：

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

如果从串行区域中，调用`omp_get_thread_num`返回 0。 如果从调用序列化嵌套并行区域内，此函数将返回 0。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)函数

### <a name="315-ompgetnumprocs-function"></a>3.1.5 omp_get_num_procs 函数

`omp_get_num_procs`函数返回在调用该函数时可用的程序的处理器数目。 格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel 函数

`omp_in_parallel`如果并行并行区域执行的动态范围内被调用的函数将返回一个非零值; 否则，它将返回 0。 格式如下所示：

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

此函数返回一个非零值时从区域并行执行，其中包括被序列化的嵌套的区域内调用。

### <a name="317-ompsetdynamic-function"></a>3.1.7 omp_set_dynamic 函数

`omp_set_dynamic`函数启用或禁用动态调整可用的并行区域执行的线程数。 格式如下所示：

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*的计算结果为非零值，用于执行并行区域即将推出的线程数可能会自动调整由运行时环境以最佳方式使用系统资源。 因此，由用户指定的线程数是最大线程数。 团队执行并行区域中的线程数保持固定该并行区域的持续时间和报告的`omp_get_num_threads`函数。

如果*dynamic_threads*的计算结果为 0，禁用动态调整。

此函数将产生影响时从该程序的一部分调用上述其中`omp_in_parallel`函数将返回零。 如果从该程序的一部分调用其中`omp_in_parallel`函数将返回一个非零值，此函数的行为是未定义。

调用`omp_set_dynamic`优先于`OMP_DYNAMIC`环境变量。

指动态调整的线程的默认值是实现定义的。 因此，依赖于特定数量的线程的正确执行用户代码应显式禁用动态线程。 实现不一定要提供的功能可以动态调整线程数，但会要求他们提供接口以支持跨所有平台的可移植性。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 函数

`omp_get_dynamic`函数返回非零值，如果动态调整线程的已启用，否则返回 0。 格式如下所示：

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

如果实现未执行动态调整线程数，此函数始终返回 0。

#### <a name="cross-references"></a>交叉引用

- 有关的动态线程调整说明，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

### <a name="319-ompsetnested-function"></a>3.1.9 omp_set_nested 函数

`omp_set_nested`函数启用或禁用嵌套并行度。 格式如下所示：

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

如果*嵌套*计算结果为 0，嵌套并行度处于禁用状态，这是默认设置，并嵌套并行区域进行序列化和执行由当前线程。 否则为启用嵌套的并行度，并且嵌套的并行区域可以部署附加线程以形成嵌套的团队。

此函数将产生影响时从该程序的一部分调用上述其中`omp_in_parallel`函数将返回零。 如果从该程序的一部分调用其中`omp_in_parallel`函数将返回一个非零值，此函数的行为是未定义。

此调用的优先级高于`OMP_NESTED`环境变量。

启用嵌套的并行度，用来执行嵌套并行区域的线程数是实现定义的。 因此，符合 OpenMP 的实现可以序列化嵌套并行区域，即使在启用了嵌套并行度。

#### <a name="cross-references"></a>交叉引用

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested 函数

`omp_get_nested`函数返回一个非零值，如果启用了嵌套并行机制和 0，如果它处于禁用状态。 有关嵌套并行性的详细信息，请参阅[omp_set_nested](#319-omp_set_nested-function)。 格式如下所示：

```cpp
#include <omp.h>
int omp_get_nested(void);
```

如果实现不会实现嵌套并行度，则此函数始终返回 0。

## <a name="32-lock-functions"></a>3.2 锁函数

在本部分中所述的函数来操作用于同步的锁。

对于以下函数，锁定变量必须具有类型`omp_lock_t`。 此变量仅必须通过这些函数来访问。 所有锁函数都要求参数具有一个指向`omp_lock_t`类型。

- [Omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函数初始化是简单的锁定。
- [Omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函数删除是简单的锁定。
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函数等待可用是简单的锁定之前。
- [Omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函数会释放是简单的锁定。
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函数测试一个简单的锁。

对于以下函数，锁定变量必须具有类型`omp_nest_lock_t`。  此变量仅必须通过这些函数来访问。 所有可嵌套锁函数要求参数具有一个指向`omp_nest_lock_t`类型。

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函数初始化可嵌套锁。
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函数可删除可嵌套锁。
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函数等待直到可嵌套锁可用。
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函数释放可嵌套锁。
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函数测试可嵌套锁。

OpenMP 的锁函数访问它们始终读取和更新锁定变量的最新值的方式中的锁定变量。 因此，但并不需要包含显式的 OpenMP 程序`flush`指令以确保锁定变量的值在不同线程之间保持一致。 (可能需要`flush`指令以使其他变量的值保持一致。)

### <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函数

这些函数提供初始化锁的唯一方式。 每个函数初始化与参数关联的锁*锁*在即将发布的调用中使用。 格式如下所示：

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初始状态处于解锁状态 （即，没有任何线程拥有该锁）。 可嵌套锁，初始嵌套计数为零。 它不符合任一这些例程使用锁的变量已初始化的调用。

### <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函数

这些函数确保锁定变量指向*锁*未初始化。 格式如下所示：

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

这是不符合任一这些例程使用具有未初始化的锁变量调用或解锁。

### <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函数

每个函数将阻止执行该函数，直到指定的锁可用，然后设置该锁的线程。 简单的锁定就是如果它是可解除锁定。 可嵌套锁是如果它是可解除锁定或如果其属于已执行该函数的线程。 格式如下所示：

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

为一个简单的锁定，到参数`omp_set_lock`函数必须指向初始化的锁定变量。 执行该函数的线程将授予该锁的所有权。

可嵌套锁，到参数`omp_set_nest_lock`函数必须指向初始化的锁定变量。 嵌套计数会递增，并在线程授予后，或保留该锁的所有权。

### <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数

这些函数提供的释放锁的所有权的方法。 格式如下所示：

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

每个函数的参数必须指向执行函数的线程所拥有的初始化的锁定变量。 如果线程不拥有该锁，该行为不确定。

为一个简单的锁定，`omp_unset_lock`函数会释放该锁的所有权从执行该函数的线程。

可嵌套锁，`omp_unset_nest_lock`函数逐量减小嵌套计数和发布该锁的所有权从执行该函数，如果在生成的计数为零的线程。

### <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函数

这些函数尝试设置一个锁，但不会阻止线程的执行。 格式如下所示：

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

自变量必须指向初始化的锁定变量。 这些函数尝试将锁设置为相同的方式`omp_set_lock`和`omp_set_nest_lock`，只不过它们不会阻止线程的执行。

为一个简单的锁定，`omp_test_lock`函数返回非零值，如果锁已成功设置; 否则，它将返回零。

可嵌套锁，`omp_test_nest_lock`函数返回新的嵌套计数，如果锁已成功设置; 否则，它将返回零。

## <a name="33-timing-routines"></a>3.3 计时例程

在本部分中所述的函数支持可移植的时钟计时器：

- [Omp_get_wtime](#331-omp_get_wtime-function)函数将返回已用的时钟时间。
- [Omp_get_wtick](#332-omp_get_wtick-function)函数返回连续的时钟计时周期之间的秒。

### <a name="331-ompgetwtime-function"></a>3.3.1 omp_get_wtime 函数

`omp_get_wtime`函数将返回在过去某个"时间"以来的秒的已用的挂钟时间双精度浮点值。  实际"过去的时间"是任意的但它保证不会在应用程序的执行期间更改。 格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

我们已预见该函数将用于测量运行时间，如下面的示例中所示：

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

返回的时间的"每个线程时间"这意味着它们不需要是全局一致参与应用程序中的所有线程。

### <a name="332-ompgetwtick-function"></a>3.3.2 omp_get_wtick 函数

`omp_get_wtick`函数将返回连续的时钟计时周期之间等待的秒数双精度浮点值。 格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
