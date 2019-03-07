---
title: Concurrency 命名空间 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: e0870eb046f1cec091a72d49c94a2fea41484340
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278686"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 命名空间 (C++ AMP)

提供类和数据并行硬件加速 c + + 代码执行的函数。 有关详细信息，请参阅[c + + AMP 概述](../cpp-amp-overview.md)

## <a name="syntax"></a>语法

```
namespace Concurrency;
```

## <a name="members"></a>成员

### <a name="namespaces"></a>命名空间

|名称|描述|
|----------|-----------------|
|[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)|提供支持 D3D 互操作性的函数。 启用无缝使用 D3D 资源在 AMP 代码中的计算和使用资源在 AMP 中创建在 D3D 代码中，而无需创建冗余的中间副本。 可以使用 c + + AMP 来增量加速您的 DirectX 应用程序的计算密集型部分，并使用从 AMP 计算生成的数据上的 D3D API。|
|[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)|中的函数`fast_math`命名空间不符合 C99 标准。 提供了每个函数仅单精度版本。 这些函数使用 DirectX 内部函数，其速度要快于中的相应函数`precise_math`命名空间并不需要扩展的双精度支持快捷键，但它们是不太准确。 有两个版本的每个函数与 C99 代码; 的源级别兼容性的这两个版本采用并返回单精度值。|
|[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)|为图形编程中提供类型和设计的功能。|
|[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)|中的函数`precise_math`命名空间是符合 C99。 包含每个函数的单精度和双精度版本。 这些函数，这包括单精度函数 — 需要扩展的双精度快捷键支持。|

### <a name="classes"></a>类

|名称|描述|
|----------|-----------------|
|[accelerator 类](accelerator-class.md)|表示 DP 优化的物理计算节点的抽象。|
|[accelerator_view 类](accelerator-view-class.md)|表示 c + + AMP 数据并行快捷键上的虚拟设备抽象。|
|[accelerator_view_removed 类](accelerator-view-removed-class.md)|基础 DirectX 调用因 Windows 超时检测和恢复机制而失败时引发的异常。|
|[array 类](array-class.md)|上的数据聚合`accelerator_view`网格域中。 它是变量，一个用于网格域中的每个元素的集合。 每个变量可保留为 c + + 类型相对应的值。|
|[array_view 类](array-view-class.md)|一个视图表示为数组中的数据\<T，N >。|
|[completion_future 类](completion-future-class.md)|表示相对应的将来对 c + + AMP 的异步操作。|
|[extent 类](extent-class.md)|表示指定原始为 0 的 N 维空间边界的 n 个整数值的向量。 坐标矢量中的值按从最重要到最不重要的顺序排列。 例如，在笛卡尔坐标三维空间，矢量 (7,5,3) 表示的空间中的 z 坐标介于 0 到 7，y 坐标范围从 0 到 5，和的 x 坐标介于 0 到 3。|
|[index 类](index-class.md)|定义一个 N 维的索引点。|
|[invalid_compute_domain 类](invalid-compute-domain-class.md)|当运行时不能通过使用在指定的计算域启动内核时引发的异常`parallel_for_each`调用站点。|
|[out_of_memory 类](out-of-memory-class.md)|一种方法将因系统或设备内存不足而失败时引发的异常。|
|[runtime_exception 类](runtime-exception-class.md)|C + + AMP 库中的异常基类型。|
|[tile_barrier 类](tile-barrier-class.md)|仅由系统创建并且传递到的功能类平铺`parallel_for_each`作为的一部分的 lambda`tiled_index`参数。 它提供了一种方法， `wait()`，其目的是以同步线程组 （图标） 中运行的线程的执行。|
|[tiled_extent 类](tiled-extent-class.md)|一个`tiled_extent`对象是`extent`一到三个维度的对象，该对象将区域空间细分为一维、 二维或三维磁贴。|
|[tiled_index 类](tiled-index-class.md)|提供的索引`tiled_grid`对象。 该类具有访问相对于本地平铺原点和相对于全局原点的元素的属性。|
|[uninitialized_object 类](uninitialized-object-class.md)|使用未初始化的对象时引发的异常。|
|[unsupported_feature 类](unsupported-feature-class.md)|使用不支持的功能时引发的异常。|

### <a name="enumerations"></a>枚举

|name|描述|
|----------|-----------------|
|[access_type 枚举](concurrency-namespace-enums-amp.md#access_type)|指定的数据访问类型。|
|[queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)|指定在快捷键支持的排队模式。|

### <a name="operators"></a>运算符

|运算符|描述|
|--------------|-----------------|
|[operator== Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|确定指定的数据结构是否相等。|
|[operator!= Operator (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|确定指定的数据结构是否不相等。|
|[operator + 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_add)|计算指定的参数的按分量逐位的总和。|
|[operator-运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator-)|计算指定参数间的按分量逐位差异。|
|[运算符 * 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_star)|计算指定的参数的乘积。|
|[运算符 / 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_div)|计算指定的参数的按分量逐位的商。|
|[operator %运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_mod)|计算第二个指定参数的第一个指定参数的模数。|

### <a name="functions"></a>函数

|名称|描述|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|阻止直到所有内存访问都完成的磁贴中的所有线程的执行。|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|取消初始化 c + + AMP 运行时。|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|已重载。 如果指定位置处存储的值进行比较的第一个指定值相等，则第二个指定的值存储在与原子操作相同的位置。|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|已重载。 设置为指定的值作为一个原子操作指定的位置处存储的值。|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|已重载。 设置值和指定的值的总和为原子操作的形式指定位置处存储的值。|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|已重载。 设置值的按位指定位置处存储`and`值和指定的值作为一个原子操作。|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|已重载。 递减值存储在指定位置，并将结果存储在作为一个原子操作相同的位置。|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|已重载。 递增指定位置处存储的值并将结果存储在作为一个原子操作相同的位置。|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|已重载。 设置存储在指定位置到较大的值的值和指定的值作为一个原子操作。|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|已重载。 设置为小于指定的位置处存储的值的值和指定的值作为一个原子操作。|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|已重载。 设置值的按位指定位置处存储`or`值和指定的值作为一个原子操作。|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|已重载。 设置值和指定的值的原子操作的形式的差异将指定位置处存储的值。|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|已重载。 设置值的按位指定位置处存储`xor`值和指定的值作为一个原子操作。|
|[copy](concurrency-namespace-functions-amp.md#copy)|复制 c + + AMP 对象。 满足所有同步数据传输要求。 代码在加速器上运行代码时，无法复制数据。 此函数的一般形式为`copy(src, dest)`。|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|复制 c + + AMP 对象并返回[completion_future](completion-future-class.md)的可等待。 当在加速器上运行代码时，无法复制数据。 此函数的一般形式为`copy(src, dest)`。|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|中止具有的函数的执行`restrict(amp)`限制子句。|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|打印格式化的字符串到 Visual Studio**输出**窗口并引发[runtime_exception](runtime-exception-class.md)异常有相同的格式设置字符串。|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|打印格式化的字符串到 Visual Studio**输出**窗口。 从具有的函数调用`restrict(amp)`限制子句。|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|阻止执行，直到所有全局内存访问的磁贴中的所有线程的已完成。|
|[parallel_for_each 函数 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|计算域之间运行函数。|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|阻止执行，直到平铺中的所有线程的`tile_static`内存访问都完成。|

## <a name="constants"></a>常量

|名称|描述|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS 常量](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|最大允许的 DirectX 的缓冲区数。|
|[MODULENAME_MAX_LENGTH 常量](concurrency-namespace-constants-amp.md#modulename_max_length)|存储模块名称的最大长度。 此值必须是编译器和运行时上相同。|

## <a name="requirements"></a>要求

**标头：** amp.h

## <a name="see-also"></a>请参阅

[参考 (C++ AMP)](reference-cpp-amp.md)
