---
title: 3. 运行时库函数
ms.date: 05/13/2019
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: 553c9ff2ceff02dc7b72e9f11899dac9d1f0f612
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857952"
---
# <a name="3-run-time-library-functions"></a>3. 运行时库函数

本部分介绍 OpenMP C 和C++运行时库函数。 标头 **\<omp >** 声明两个类型、可用于控制和查询并行执行环境的多个函数以及可用于同步对数据的访问的锁函数。

类型 `omp_lock_t` 是一种对象类型，该对象类型能够表示锁可用，或者线程拥有锁。 这些锁称为*简单锁*。

类型 `omp_nest_lock_t` 是一种对象类型，该对象类型能够表示锁可用，或者同时拥有该锁的线程的标识和*嵌套计数*（如下所述）。 这些锁嘿*可嵌套锁*。

库函数是带有 "C" 链接的外部函数。

本章中的说明分为以下主题：

- [执行环境函数](#31-execution-environment-functions)
- [锁定函数](#32-lock-functions)
- [计时例程](#33-timing-routines)

## <a name="31-execution-environment-functions"></a>3.1 执行环境函数

本部分中所述的函数影响和监视线程、处理器和并行环境：

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

### <a name="311-omp_set_num_threads-function"></a>3.1.1 omp_set_num_threads 函数

`omp_set_num_threads` 函数将设置用于后面的并行区域的默认线程数，这些线程不指定 `num_threads` 子句。 格式如下：

```cpp
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

参数*num_threads*的值必须是一个正整数。 其效果取决于是否启用了动态调整线程数。 有关 `omp_set_num_threads` 函数与线程动态调整之间的交互的综合规则集，请参阅[2.3 节](2-directives.md#23-parallel-construct)。

此函数包含上述效果，从 `omp_in_parallel` 函数返回零的程序的某个部分调用。 如果在 `omp_in_parallel` 函数返回非零值的程序的一部分中调用该函数，则此函数的行为是不确定的。

此调用优先于 `OMP_NUM_THREADS` 环境变量。 可以通过调用 `omp_set_num_threads` 或设置 `OMP_NUM_THREADS` 环境变量来在单个 `parallel` 指令上显式重写的线程数的默认值，可以通过指定 `num_threads` 子句来显式重写。

有关详细信息，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉引用

- [omp_set_dynamic](#317-omp_set_dynamic-function)函数
- [omp_get_dynamic](#318-omp_get_dynamic-function)函数
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)环境变量
- [num_threads](2-directives.md#23-parallel-construct)子句

### <a name="312-omp_get_num_threads-function"></a>3.1.2 omp_get_num_threads 函数

`omp_get_num_threads` 函数返回团队中当前正在执行其调用的并行区域的线程数。 格式如下：

```cpp
#include <omp.h>
int omp_get_num_threads(void);
```

`num_threads` 子句、`omp_set_num_threads` 函数和 `OMP_NUM_THREADS` 环境变量控制团队中的线程数。

如果用户尚未显式设置线程数，则默认值为实现定义的。 此函数绑定到最近的封闭 `parallel` 指令。 如果是从程序的序列部分或从序列化的嵌套并行区域调用的，则此函数返回1。

有关详细信息，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉引用

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [num_threads](2-directives.md#23-parallel-construct)
- [parallel](2-directives.md#23-parallel-construct)

### <a name="313-omp_get_max_threads-function"></a>3.1.3 omp_get_max_threads 函数

`omp_get_max_threads` 函数返回一个整数，该整数保证至少当在代码中没有出现 `num_threads` 子句的并行区域时，该整数才能用于构成团队的线程的数目。 格式如下：

```cpp
#include <omp.h>
int omp_get_max_threads(void);
```

下面表示 `omp_get_max_threads`的值的下限：

```

threads-used-for-next-team
<= omp_get_max_threads
```

请注意，如果另一个并行区域使用 `num_threads` 子句来请求特定数量的线程，则保证 `omp_get_max_threads` 的结果的下限不长。

`omp_get_max_threads` 函数的返回值可用于为在下一个并行区域中形成的团队中的所有线程动态分配足够的存储空间。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [omp_set_num_threads](#311-omp_set_num_threads-function)
- [omp_set_dynamic](#317-omp_set_dynamic-function)
- [num_threads](2-directives.md#23-parallel-construct)

### <a name="314-omp_get_thread_num-function"></a>3.1.4 omp_get_thread_num 函数

`omp_get_thread_num` 函数返回执行函数的线程在其团队中的线程数。 线程编号介于0和 `omp_get_num_threads()`-1 （含）之间。 团队的主线程为线程0。

格式如下：

```cpp
#include <omp.h>
int omp_get_thread_num(void);
```

如果从串行区域调用，`omp_get_thread_num` 将返回0。 如果从序列化的嵌套并行区域内调用，则此函数返回0。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)函数

### <a name="315-omp_get_num_procs-function"></a>3.1.5 omp_get_num_procs 函数

`omp_get_num_procs` 函数将返回调用函数时程序可用的处理器数。 格式如下：

```cpp
#include <omp.h>
int omp_get_num_procs(void);
```

### <a name="316-omp_in_parallel-function"></a>3.1.6 omp_in_parallel 函数

如果在并行执行的并行区域的动态范围内调用，则 `omp_in_parallel` 函数将返回非零值;否则，返回0。 格式如下：

```cpp
#include <omp.h>
int omp_in_parallel(void);
```

从并行执行的区域内调用时，此函数将返回一个非零值，包括已序列化的嵌套区域。

### <a name="317-omp_set_dynamic-function"></a>3.1.7 omp_set_dynamic 函数

`omp_set_dynamic` 函数可启用或禁用对可执行并行区域的线程数进行动态调整。 格式如下：

```cpp
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

如果*dynamic_threads*的计算结果为非零值，则运行时环境可能会自动调整用于执行即将开始的并行区域的线程数，以最好地使用系统资源。 因此，用户指定的线程数是最大线程数。 执行并行区域的团队中的线程数在该并行区域的持续时间内保持固定，并由 `omp_get_num_threads` 函数进行报告。

如果*dynamic_threads*的计算结果为0，则禁用动态调整。

此函数包含上述效果，从 `omp_in_parallel` 函数返回零的程序的某个部分调用。 如果在 `omp_in_parallel` 函数返回非零值的程序的一部分中调用该函数，则此函数的行为是不确定的。

对 `omp_set_dynamic` 的调用优先于 `OMP_DYNAMIC` 环境变量。

线程的动态调整的默认值是实现定义的。 因此，依赖于特定数量的线程进行正确执行的用户代码应显式禁用动态线程。 实现不需要提供动态调整线程数的能力，但需要提供接口以支持所有平台上的可移植性。

#### <a name="microsoft-specific"></a>Microsoft 专用

`omp_get_dynamic` 和 `omp_set_dynamic` 的当前支持如下所示： 

`omp_set_dynamic` 的输入参数不会影响线程策略，也不会更改线程的数目。 `omp_get_num_threads` 总是返回用户定义的编号（如果已设置）或默认线程号。 在当前的 Microsoft 实现中，`omp_set_dynamic(0)` 关闭动态线程，以便可以为以下并行区域重用现有的线程集。 `omp_set_dynamic(1)` 通过丢弃现有的一组线程并为即将推出的并行区域创建新集来打开动态线程处理。 新集合中的线程数与旧集相同，并且基于 `omp_get_num_threads`的返回值。 因此，为了获得最佳性能，请使用 `omp_set_dynamic(0)` 重新使用现有线程。

#### <a name="cross-references"></a>交叉引用

- [omp_get_num_threads](#312-omp_get_num_threads-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="318-omp_get_dynamic-function"></a>3.1.8 omp_get_dynamic 函数

如果启用线程的动态调整，则 `omp_get_dynamic` 函数返回一个非零值，否则返回0。 格式如下：

```cpp
#include <omp.h>
int omp_get_dynamic(void);
```

如果实现未实现线程数的动态调整，则此函数始终返回0。 有关详细信息，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

#### <a name="cross-references"></a>交叉引用

- 有关动态线程调整的说明，请参阅[omp_set_dynamic](#317-omp_set_dynamic-function)。

### <a name="319-omp_set_nested-function"></a>3.1.9 omp_set_nested 函数

`omp_set_nested` 函数启用或禁用嵌套并行度。 格式如下：

```cpp
#include <omp.h>
void omp_set_nested(int nested);
```

如果*嵌套*的计算结果为0，则会禁用嵌套并行，这是默认值，嵌套的并行区域由当前线程进行序列化和执行。 否则，会启用嵌套并行，而嵌套的并行区域可能会部署其他线程来形成嵌套团队。

此函数包含上述效果，从 `omp_in_parallel` 函数返回零的程序的某个部分调用。 如果在 `omp_in_parallel` 函数返回非零值的程序的一部分中调用该函数，则此函数的行为是不确定的。

此调用优先于 `OMP_NESTED` 环境变量。

当启用嵌套并行时，用于执行嵌套并行区域的线程的数目是实现定义的。 因此，即使在启用了嵌套并行机制的情况下，也允许 OpenMP 兼容的实现序列化嵌套的并行区域。

#### <a name="cross-references"></a>交叉引用

- [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_in_parallel](#316-omp_in_parallel-function)

### <a name="3110-omp_get_nested-function"></a>3.1.10 omp_get_nested 函数

如果启用嵌套并行，则 `omp_get_nested` 函数将返回非零值; 如果已禁用，则返回0。 有关嵌套并行的详细信息，请参阅[omp_set_nested](#319-omp_set_nested-function)。 格式如下：

```cpp
#include <omp.h>
int omp_get_nested(void);
```

如果实现未实现嵌套并行，则此函数始终返回0。

## <a name="32-lock-functions"></a>3.2 锁函数

本部分中所述的函数操作用于同步的锁。

对于以下函数，lock 变量必须具有类型 `omp_lock_t`。 仅可通过这些函数访问此变量。 所有锁函数都需要一个具有指向 `omp_lock_t` 类型的指针的参数。

- [Omp_init_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函数初始化简单锁。
- [Omp_destroy_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函数删除一个简单的锁。
- [Omp_set_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函数将一直等待，直到有一个简单的锁可用。
- [Omp_unset_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函数将释放一个简单的锁。
- [Omp_test_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函数测试简单锁。

对于以下函数，lock 变量必须具有类型 `omp_nest_lock_t`。  仅可通过这些函数访问此变量。 所有 a.17 锁函数都需要一个具有指向 `omp_nest_lock_t` 类型的指针的参数。

- [Omp_init_nest_lock](#321-omp_init_lock-and-omp_init_nest_lock-functions)函数初始化 a.17 锁。
- [Omp_destroy_nest_lock](#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)函数删除 a.17 锁。
- [Omp_set_nest_lock](#323-omp_set_lock-and-omp_set_nest_lock-functions)函数将等待 a.17 锁可用。
- [Omp_unset_nest_lock](#324-omp_unset_lock-and-omp_unset_nest_lock-functions)函数将释放一个 a.17 锁。
- [Omp_test_nest_lock](#325-omp_test_lock-and-omp_test_nest_lock-functions)函数测试 a.17 锁。

OpenMP 锁函数以这种方式访问锁变量，以使其始终读取和更新锁变量的最新值。 因此，OpenMP 程序不需要包括显式 `flush` 指令，以确保锁变量的值在不同线程之间保持一致。 （可能需要 `flush` 指令，使其他变量的值保持一致。）

### <a name="321-omp_init_lock-and-omp_init_nest_lock-functions"></a>3.2.1 omp_init_lock 和 omp_init_nest_lock 函数

这些函数提供初始化锁的唯一方法。 每个函数都初始化与参数*锁*关联的锁，以便在即将进行的调用中使用。 格式如下：

```cpp
#include <omp.h>
void omp_init_lock(omp_lock_t *lock);
void omp_init_nest_lock(omp_nest_lock_t *lock);
```

初始状态为 "未锁定" （即，没有线程拥有该锁）。 对于 a.17 锁，初始嵌套计数为零。 使用已初始化的锁变量调用其中一个例程是不相容的。

### <a name="322-omp_destroy_lock-and-omp_destroy_nest_lock-functions"></a>3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函数

这些函数可确保指向锁定变量*锁*的未初始化。 格式如下：

```cpp
#include <omp.h>
void omp_destroy_lock(omp_lock_t *lock);
void omp_destroy_nest_lock(omp_nest_lock_t *lock);
```

使用未初始化或未锁定的锁定变量调用其中一个例程是不相容的。

### <a name="323-omp_set_lock-and-omp_set_nest_lock-functions"></a>3.2.3 omp_set_lock 和 omp_set_nest_lock 函数

其中每个函数都会阻止执行函数的线程，直到指定的锁可用，然后设置锁。 如果解除锁定，则可以使用简单锁。 如果 a.17 锁已解锁，或者它已由执行函数的线程所有，则可以使用该锁。 格式如下：

```cpp
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

对于简单锁，`omp_set_lock` 函数的参数必须指向已初始化的锁变量。 锁定的所有权将授予执行函数的线程。

对于 a.17 锁，`omp_set_nest_lock` 函数的参数必须指向已初始化的锁变量。 嵌套计数递增，线程被授予或保留锁的所有权。

### <a name="324-omp_unset_lock-and-omp_unset_nest_lock-functions"></a>3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函数

这些函数提供释放锁定所有权的方式。 格式如下：

```cpp
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

其中每个函数的参数都必须指向执行函数的线程所拥有的已初始化锁变量。 如果线程未拥有该锁，则行为是不确定的。

对于简单的锁，`omp_unset_lock` 函数将从锁的所有权中释放执行函数的线程。

对于 a.17 锁，`omp_unset_nest_lock` 函数将减小嵌套计数，并在生成的计数为零时释放执行函数的线程。

### <a name="325-omp_test_lock-and-omp_test_nest_lock-functions"></a>3.2.5 omp_test_lock 和 omp_test_nest_lock 函数

这些函数尝试设置锁，但不阻止执行线程。 格式如下：

```cpp
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

自变量必须指向已初始化的锁定变量。 这些函数尝试以与 `omp_set_lock` 和 `omp_set_nest_lock`相同的方式设置锁，只不过它们不会阻止执行线程。

对于简单锁，如果成功设置了锁，则 `omp_test_lock` 函数返回一个非零值;否则，它返回零。

对于 a.17 锁，如果成功设置了锁，则 `omp_test_nest_lock` 函数将返回新的嵌套计数;否则，它返回零。

## <a name="33-timing-routines"></a>3.3 计时例程

本节中所述的函数支持可移植的墙壁时钟定时器：

- [Omp_get_wtime](#331-omp_get_wtime-function)函数将返回已用的时钟时间。
- [Omp_get_wtick](#332-omp_get_wtick-function)函数返回连续时钟计时周期之间的秒数。

### <a name="331-omp_get_wtime-function"></a>3.3.1 omp_get_wtime 函数

`omp_get_wtime` 函数返回的双精度浮点值等于已用的时钟时间（以秒为单位），因为某些 "过去时间"。  实际的 "过去时间" 是任意的，但在应用程序执行过程中一定不会更改。 格式如下：

```cpp
#include <omp.h>
double omp_get_wtime(void);
```

预计该函数将用于测量过去的时间，如以下示例中所示：

```cpp
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

返回的时间是 "每个线程的时间"，这意味着它们在所有参与应用程序的线程之间不需要全局一致。

### <a name="332-omp_get_wtick-function"></a>3.3.2 omp_get_wtick 函数

`omp_get_wtick` 函数返回一个双精度浮点值，该值等于连续时钟周期之间的秒数。 格式如下：

```cpp
#include <omp.h>
double omp_get_wtick(void);
```
