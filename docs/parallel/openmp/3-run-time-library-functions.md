---
title: 3. 运行时库函数
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 767c006b0a2d81af4d1f8f2e23f84d7847326f31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370274"
---
# <a name="3-run-time-library-functions"></a>3. 运行时库功能

本节介绍 OpenMP C 和C++运行时库函数。 标头**\<omp.h>** 声明两种类型，多个函数可用于控制和查询并行执行环境，以及锁定可用于同步访问数据的函数。

类型`omp_lock_t`是一种对象类型，能够表示锁可用或线程拥有锁。 这些锁被称为*简单的锁*。

类型`omp_nest_lock_t`是一种对象类型，能够表示锁可用，或者同时表示拥有锁的线程的标识和*嵌套计数*（如下所述）。 这些锁称为*可嵌套锁*。

库函数是具有"C"链接的外部函数。

本章中的描述分为以下主题：

- [执行环境函数](#31-execution-environment-functions)
- [锁定功能](#32-lock-functions)
- [计时例程](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 执行环境函数

本节中描述的函数影响和监视线程、处理器和并行环境：

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

### <a name="311-omp_set_num_threads-function"></a><a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads功能

函数`omp_set_num_threads`设置默认的线程数，用于未指定`num_threads`子句的更高版本的并行区域。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

参数*num_threads*的值必须为正整数。 其效果取决于是否启用了线程数的动态调整。 有关`omp_set_num_threads`函数与线程动态调整之间的交互的一套全面规则，请参阅[第 2.3 节](2-directives.md#23-parallel-construct)。

当从程序返回零的部分调用时，`omp_in_parallel`此功能具有上述效果。 如果从程序的一部分调用函数`omp_in_parallel`返回非零值，则此函数的行为未定义。

此调用优先于`OMP_NUM_THREADS`环境变量。 可以通过调用`omp_set_num_threads`或设置`OMP_NUM_THREADS`环境变量在单个`parallel`指令上显式覆盖线程数的默认值，该值可以通过指定`num_threads`子句来显式覆盖。

有关详细信息，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉引用

- [omp_set_dynamic](#317-omp_set_dynamic-function)功能
- [omp_get_dynamic](#318-omp_get_dynamic-function)功能
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)环境变量
- [num_threads](2-directives.md#23-parallel-construct)条款

### <a name="312-omp_get_num_threads-function"></a><a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads功能

函数`omp_get_num_threads`返回团队中当前执行调用它的并行区域的线程数。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

子`num_threads`句、`omp_set_num_threads`函数`OMP_NUM_THREADS`和环境变量控制团队中的线程数。

如果用户尚未显式设置线程数，则默认值为实现定义。 此函数绑定到最近的封闭`parallel`指令。 如果从程序的串行部分或序列化的嵌套并行区域调用，则此函数返回 1。

有关详细信息，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉引用

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [并行](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a><a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads功能

函数`omp_get_max_threads`返回一个整数，该整数保证至少与用于组建团队的线程数一样大，如果代码中此时可以看到没有子句的`num_threads`并行区域。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

下面表示对 的值的下`omp_get_max_threads`限：

> *线程使用为下一个团队* <= `omp_get_max_threads`

请注意，如果另一个并行区域`num_threads`使用 子句请求特定数量的线程，则下限上的保证`omp_get_max_threads`不再保留。

函数`omp_get_max_threads`的返回值可用于动态分配在下一个并行区域形成的团队中的所有线程的足够存储。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a><a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num功能

函数`omp_get_thread_num`返回执行其函数的线程的线程编号（在其团队中）。 线程数介于 0 和`omp_get_num_threads()`-1 之间，包括。 团队的主线程是线程 0。

其格式如下所示：

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

如果从串行区域调用，`omp_get_thread_num`则返回 0。 如果从序列化的嵌套并行区域内调用，则此函数返回 0。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)功能

### <a name="315-omp_get_num_procs-function"></a><a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs功能

函数`omp_get_num_procs`返回调用函数时程序可用的处理器数。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a><a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel功能

`omp_in_parallel`如果函数在并行区域的动态范围内调用，则返回非零值;否则，它返回 0。 其格式如下所示：

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

当从并行执行的区域内调用时，此函数返回非零值，包括序列化的嵌套区域。

### <a name="317-omp_set_dynamic-function"></a><a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic功能

该`omp_set_dynamic`函数启用或禁用可用于执行并行区域的线程数的动态调整。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*计算为非零值，则运行时环境可能会自动调整用于执行即将到来的并行区域的线程数，以最佳使用系统资源。 因此，用户指定的线程数是最大线程计数。 执行并行区域的团队中的线程数在该并行区域的持续时间内保持不变，`omp_get_num_threads`并由函数报告。

如果*dynamic_threads*计算为 0，则禁用动态调整。

当从程序返回零的部分调用时，`omp_in_parallel`此功能具有上述效果。 如果从程序的一部分调用函数`omp_in_parallel`返回非零值，则此函数的行为未定义。

对 的`omp_set_dynamic`调用优先于`OMP_DYNAMIC`环境变量。

线程动态调整的默认值是实现定义的。 因此，依赖于特定数量的线程进行正确执行的用户代码应显式禁用动态线程。 实现不需要提供动态调整线程数的能力，但它们需要提供接口来支持跨所有平台的可移植性。

#### <a name="microsoft-specific"></a>Microsoft 专用

目前的支持`omp_get_dynamic`如下`omp_set_dynamic`：

要`omp_set_dynamic`的输入参数不会影响线程策略，也不会更改线程数。 `omp_get_num_threads`始终返回用户定义的编号（如果已设置）或默认线程号。 在当前 Microsoft 实现中`omp_set_dynamic(0)`，关闭动态线程，以便现有线程集可以重新用于以下并行区域。 `omp_set_dynamic(1)`通过放弃现有线程集并为即将到来的并行区域创建新集来打开动态线程。 新集中的线程数与旧集相同，并且基于 的`omp_get_num_threads`返回值 。 因此，为了获得最佳性能，请使用`omp_set_dynamic(0)`重用现有线程。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a><a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic功能

如果`omp_get_dynamic`启用了线程的动态调整，则函数返回非零值，否则返回 0。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

如果实现不实现线程数的动态调整，则此函数始终返回 0。 有关详细信息，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉引用

- 有关动态线程调整的说明，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

### <a name="319-omp_set_nested-function"></a><a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested功能

该`omp_set_nested`函数启用或禁用嵌套并行性。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

如果*嵌套*计算为 0，则禁用嵌套并行性（这是默认值），嵌套并行区域由当前线程序列化并执行。 否则，将启用嵌套并行性，嵌套的并行区域可能会部署其他线程以形成嵌套团队。

当从程序返回零的部分调用时，`omp_in_parallel`此功能具有上述效果。 如果从程序的一部分调用函数`omp_in_parallel`返回非零值，则此函数的行为未定义。

此调用优先于`OMP_NESTED`环境变量。

启用嵌套并行性后，用于执行嵌套并行区域的线程数将定义实现。 因此，即使启用嵌套并行性，也允许符合 OpenMP 的实现序列化嵌套并行区域。

#### <a name="cross-references"></a>交叉引用

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a><a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested功能

如果`omp_get_nested`启用嵌套并行性，则函数返回非零值;如果禁用，则返回 0。 有关嵌套并行性的详细信息，请参阅[omp_set_nested](#319-omp_set_nested-function)。 其格式如下所示：

```cpp
#include <omp.h>
int omp_get_nested(void);
```

如果实现不实现嵌套并行性，则此函数始终返回 0。

## <a name="32-lock-functions"></a>3.2 锁定功能

本节中描述的函数操作用于同步的锁。

对于以下函数，锁变量必须具有 类型`omp_lock_t`。 只能通过这些函数访问此变量。 所有锁函数都需要具有指向`omp_lock_t`类型的指针的参数。

- [omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函数初始化一个简单的锁。
- [omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函数删除一个简单的锁。
- [omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函数等待，直到一个简单的锁可用。
- [omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函数释放一个简单的锁。
- [omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函数测试一个简单的锁。

对于以下函数，锁变量必须具有 类型`omp_nest_lock_t`。  只能通过这些函数访问此变量。 所有可嵌套锁函数都需要具有指向`omp_nest_lock_t`类型的指针的参数。

- [omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函数初始化可嵌套锁。
- [omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函数删除可嵌套锁。
- [omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函数等待，直到可嵌套锁可用。
- [omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函数释放可嵌套锁。
- [omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函数测试可嵌套锁。

OpenMP 锁函数访问锁变量的方式始终读取和更新锁变量的最新版本。 因此，OpenMP 程序不需要包含显式`flush`指令，以确保锁变量的值在不同的线程之间一致。 （可能需要指令`flush`来使其他变量的值保持一致。

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a><a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock和omp_init_nest_lock功能

这些函数提供了初始化锁的唯一方法。 每个函数初始化与参数*锁*关联的锁，以便在即将到来的调用中使用。 其格式如下所示：

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初始状态解锁（即，没有线程拥有锁）。 对于可嵌套锁，初始嵌套计数为零。 使用已初始化的锁变量调用这些例程中的任何一个都不符合要求。

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a><a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock和omp_destroy_nest_lock功能

这些函数可确保未初始化指向锁定变量*锁*。 其格式如下所示：

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

使用未初始化或解锁的锁变量调用这些例程中的任何一个是不合规的。

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a><a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock和omp_set_nest_lock功能

这些函数中的每一个都会阻止执行函数的线程，直到指定的锁可用，然后设置锁。 如果未锁定，则提供简单的锁。 如果可嵌套锁已解锁，或者该锁已归执行该函数的线程所有，则该锁可用。 其格式如下所示：

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

对于简单锁，函数的`omp_set_lock`参数必须指向初始化锁变量。 锁的所有权授予执行函数的线程。

对于可嵌套锁，函数的`omp_set_nest_lock`参数必须指向初始化锁变量。 嵌套计数递增，线程被授予或保留锁的所有权。

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a><a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock和omp_unset_nest_lock功能

这些函数提供了释放锁所有权的方法。 其格式如下所示：

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

每个函数的参数必须指向执行函数的线程拥有的初始化锁变量。 如果线程不拥有该锁，则该行为未定义。

对于简单锁，`omp_unset_lock`函数释放从锁的所有权中执行函数的线程。

对于可嵌套锁，`omp_unset_nest_lock`函数将释放嵌套计数，并在生成的计数为零时释放从锁的所有权执行函数的线程。

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a><a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock和omp_test_nest_lock功能

这些函数尝试设置锁，但不阻止线程的执行。 其格式如下所示：

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

参数必须指向初始化锁变量。 这些函数尝试以 与`omp_set_lock``omp_set_nest_lock`和 相同的方式设置锁，只不过它们不会阻止线程的执行。

对于简单锁，如果成功`omp_test_lock`设置锁，函数将返回非零值;对于简单锁，函数将返回非零值。否则，它将返回零。

对于可嵌套锁，如果成功`omp_test_nest_lock`设置锁，函数将返回新的嵌套计数;否则，它将返回零。

## <a name="33-timing-routines"></a>3.3 计时例程

本节中描述的功能支持便携式挂钟计时器：

- [omp_get_wtime](#331-omp_get_wtime-function)函数返回已经过的挂钟时间。
- [omp_get_wtick](#332-omp_get_wtick-function)函数在连续时钟刻度之间返回秒。

### <a name="331-omp_get_wtime-function"></a><a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime功能

该`omp_get_wtime`函数返回一个双精度浮点值，该值等于经过的挂钟时间（以秒为单位），因为"过去的某个时间"。  实际的"过去时间"是任意的，但保证在应用程序执行期间不会更改。 其格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

预计该函数将用于测量已用时间，如以下示例所示：

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

返回的时间是"每个线程时间"，这意味着它们不需要在参与应用程序的所有线程之间全局一致。

### <a name="332-omp_get_wtick-function"></a><a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick功能

函数`omp_get_wtick`返回一个双精度浮点值，等于连续时钟刻度之间的秒数。 其格式如下所示：

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
