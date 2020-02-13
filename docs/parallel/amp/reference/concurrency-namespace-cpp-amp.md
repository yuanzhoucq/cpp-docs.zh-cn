---
title: Concurrency 命名空间 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 34c3c10fa6bec2737ba78a71c282f90f284a28c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139370"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 命名空间 (C++ AMP)

提供在数据并行硬件上加速C++代码执行的类和函数。 有关详细信息，请参阅[ C++ AMP 概述](../cpp-amp-overview.md)

## <a name="syntax"></a>语法

```cpp
namespace Concurrency;
```

## <a name="members"></a>Members

### <a name="namespaces"></a>命名空间

|名称|说明|
|----------|-----------------|
|[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)|提供支持 D3D 互操作性的函数。 允许无缝使用 D3D 资源来计算 AMP 代码和在 D3D 代码中创建的资源，而无需创建冗余的中间副本。 你可以使用C++ amp 增量加速 DirectX 应用程序的计算密集型部分，并在从 AMP 计算生成的数据上使用 D3D API。|
|[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)|`fast_math` 命名空间中的函数不符合 C99。 仅提供每个函数的单精度版本。 这些函数使用 DirectX 内部函数，该函数比 `precise_math` 命名空间中的对应函数快，并且不需要对加速器进行扩展的双精度支持，但它们不太准确。 每个函数的两个版本都适用于与 C99 代码进行源级别的兼容性。这两个版本都采用并返回单精度值。|
|[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)|提供专为图形编程设计的类型和函数。|
|[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)|`precise_math` 命名空间中的函数符合 C99。 每个函数的单精度和双精度版本都包括在内。 这些函数（包括单精度函数）需要对加速器进行扩展的双精度支持。|

### <a name="classes"></a>类

|名称|说明|
|----------|-----------------|
|[accelerator 类](accelerator-class.md)|表示物理 DP 优化计算节点的抽象。|
|[accelerator_view 类](accelerator-view-class.md)|表示C++ AMP 数据并行加速器上的虚拟设备抽象。|
|[accelerator_view_removed 类](accelerator-view-removed-class.md)|基础 DirectX 调用因 Windows 超时检测和恢复机制而失败时引发的异常。|
|[array 类](array-class.md)|网格域中 `accelerator_view` 的数据聚合。 它是变量集合，每个元素对应于网格域中的一个元素。 每个变量都包含对应于某种C++类型的值。|
|[array_view 类](array-view-class.md)|表示\<T，N > 的数组中数据的视图。|
|[completion_future 类](completion-future-class.md)|表示与C++ AMP 异步操作对应的将来。|
|[extent 类](extent-class.md)|表示 N 个整数值的向量，这些整数值指定具有0源的 N 维空间的界限。 坐标矢量中的值按从最重要到最不重要的顺序排列。 例如，在笛卡尔三维空间中，区向量（7，5，3）表示一个空间，其中 z 坐标范围介于0到7之间，y 坐标范围为0到5，x 坐标范围介于0到3之间。|
|[index 类](index-class.md)|定义一个 N 维索引点。|
|[invalid_compute_domain 类](invalid-compute-domain-class.md)|当运行时无法通过使用在 `parallel_for_each` 调用站点指定的计算域启动内核时引发的异常。|
|[out_of_memory 类](out-of-memory-class.md)|当某个方法因缺少系统或设备内存而失败时引发的异常。|
|[runtime_exception 类](runtime-exception-class.md)|C++ AMP 库中的异常的基类型。|
|[tile_barrier 类](tile-barrier-class.md)|仅可由系统创建并作为 `tiled_index` 参数的一部分传递给平铺 `parallel_for_each` lambda 的功能类。 它提供一种 `wait()`方法，其目的是同步线程组（磁贴）中运行的线程的执行。|
|[tiled_extent 类](tiled-extent-class.md)|`tiled_extent` 对象是一到三个维度的 `extent` 对象，它将范围空间细分一维、二维或三维平铺。|
|[tiled_index 类](tiled-index-class.md)|为 `tiled_grid` 对象提供索引。 此类具有一些属性，可访问相对于本地平铺原点和相对于全局原点的元素。|
|[uninitialized_object 类](uninitialized-object-class.md)|当使用未初始化的对象时引发的异常。|
|[unsupported_feature 类](unsupported-feature-class.md)|当使用不受支持的功能时引发的异常。|

### <a name="enumerations"></a>枚举

|名称|说明|
|----------|-----------------|
|[access_type 枚举](concurrency-namespace-enums-amp.md#access_type)|指定数据访问类型。|
|[queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)|指定加速器支持的排队模式。|

### <a name="operators"></a>运算符

|运算符|说明|
|--------------|-----------------|
|[operator = = 运算符（C++ AMP）](concurrency-namespace-operators-amp.md#operator_eq_eq)|确定指定的数据结构是否相等。|
|[operator！ = 运算符（C++ AMP）](concurrency-namespace-operators-amp.md#operator_neq)|确定指定的数据结构是否不相等。|
|[operator + 运算符（C++ AMP）](concurrency-namespace-operators-amp.md#operator_add)|计算指定参数的按组件的和。|
|[operator-运算符（C++ AMP）](concurrency-namespace-operators-amp.md#operator-)|计算指定参数之间的以组件为的差。|
|[operator * 运算符（C++ AMP）](concurrency-namespace-operators-amp.md#operator_star)|计算指定参数的按组件的积。|
|[operator/运算符（C++ AMP）](concurrency-namespace-operators-amp.md#operator_div)|计算指定参数的按分量的商。|
|[operator% 运算符（C++ AMP）](concurrency-namespace-operators-amp.md#operator_mod)|按指定的第二个参数计算第一个指定参数的模数。|

### <a name="functions"></a>函数

|名称|说明|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|阻止在磁贴中所有线程的执行，直到所有内存访问都完成。|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|取消C++ AMP 运行时。|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|已重载。 如果存储在指定位置的值与第一个指定的值相等，则第二个指定的值将存储在与原子操作相同的位置中。|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|已重载。 以原子操作的形式，将指定位置处存储的值设置为指定值。|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|已重载。 以原子操作的形式，将指定位置处存储的值设置为此值和指定值的总和。|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|已重载。 将指定位置处存储的值设置为该值的按位 `and`，并将指定的值设置为原子操作。|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|已重载。 减少存储在指定位置的值，并将结果存储在与原子操作相同的位置中。|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|已重载。 递增存储在指定位置的值，并将结果存储在与原子操作相同的位置中。|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|已重载。 以原子操作的形式，将指定位置处存储的值设置为此值和指定值中的较大值。|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|已重载。 以原子操作的形式，将指定位置处存储的值设置为此值和指定值中的较小值。|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|已重载。 将指定位置处存储的值设置为该值的按位 `or`，并将指定的值设置为原子操作。|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|已重载。 以原子操作的形式，将指定位置处存储的值设置为此值和指定值的差。|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|已重载。 将指定位置处存储的值设置为该值的按位 `xor`，并将指定的值设置为原子操作。|
|[copy](concurrency-namespace-functions-amp.md#copy)|复制C++ AMP 对象。 满足所有同步数据传输要求。 当代码正在加速器上运行代码时，无法复制数据。 此函数的常规形式是 `copy(src, dest)`。|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|复制C++ AMP 对象并返回可等待的[completion_future](completion-future-class.md) 。 在加速器上运行代码时，无法复制数据。 此函数的常规形式是 `copy(src, dest)`。|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|中止具有 `restrict(amp)` 限制子句的函数的执行。|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|打印格式化的字符串到 Visual Studio "**输出**" 窗口，并引发具有相同格式设置字符串的[runtime_exception](runtime-exception-class.md)异常。|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|打印格式化的字符串到 Visual Studio "**输出**" 窗口。 它从具有 `restrict(amp)` 限制子句的函数中调用。|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|阻止在磁贴中所有线程的执行，直到所有全局内存访问都完成。|
|[parallel_for_each 函数（C++ AMP）](concurrency-namespace-functions-amp.md#parallel_for_each)|跨计算域运行函数。|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|阻止执行磁贴中所有线程的执行，直到 `tile_static` 内存访问完成。|

## <a name="constants"></a>常量

|名称|说明|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS 常量](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|DirectX 允许的最大缓冲区数。|
|[MODULENAME_MAX_LENGTH 常量](concurrency-namespace-constants-amp.md#modulename_max_length)|存储模块名称的最大长度。 此值在编译器和运行时上必须相同。|

## <a name="requirements"></a>要求

**标头：** amp.h

## <a name="see-also"></a>另请参阅

[参考 (C++ AMP)](reference-cpp-amp.md)
