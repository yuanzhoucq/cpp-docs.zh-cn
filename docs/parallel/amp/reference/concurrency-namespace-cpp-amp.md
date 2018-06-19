---
title: 并发 Namespace (c + + AMP) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP/Concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 127c1b63693b128e9cdf23813bbfe8e0ec251f9d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693372"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 命名空间 (C++ AMP)
提供的类和在数据并行硬件加速执行的 c + + 代码的函数。 有关详细信息，请参阅[c + + AMP 概述](../cpp-amp-overview.md)  
  
## <a name="syntax"></a>语法  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>成员  
  
### <a name="namespaces"></a>命名空间  
  
|名称|描述|  
|----------|-----------------|  
|[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)|提供了支持 D3D 互操作性的函数。 启用 AMP 代码中的计算 D3D 资源的无缝利用和在 AMP 中创建在 D3D 代码中，而无需创建冗余中间副本的资源的使用。 可以使用 c + + AMP 以增量方式加速 DirectX 应用程序的需要进行大量计算的部分而对从 AMP 计算生成数据使用 D3D API。|  
|[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)|函数中`fast_math`命名空间不符合 C99 标准。 提供了只有单精度的每个函数的版本。 这些函数将使用 DirectX 内部函数，其速度要快于中的相应函数`precise_math`命名空间和不需要扩展的双精度支持加速器，但它们是不太准确。 有两个版本的每个函数以便与 C99 代码; 的源级别兼容这两个版本采用并返回单精度值。|  
|[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)|图形编程提供类型和函数所设计的。|  
|[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)|函数中`precise_math`命名空间是符合 C99。 每个函数的单精度和双精度版本是包含。 这些函数-这包括单精度函数-需要扩展的双精度支持加速器上。|  
  
### <a name="classes"></a>类  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator 类](accelerator-class.md)|表示物理 DP 优化计算节点的抽象。|  
|[accelerator_view 类](accelerator-view-class.md)|表示 c + + AMP 数据并行加速器上的虚拟设备抽象。|  
|[accelerator_view_removed 类](accelerator-view-removed-class.md)|基础 DirectX 调用因 Windows 超时检测和恢复机制而失败时引发的异常。|  
|[array 类](array-class.md)|数据聚合上`accelerator_view`网格域中。 它是变量，一个用于在网格域中的每个元素的集合。 每个变量包含一个值，对应于某些 c + + 类型。|  
|[array_view 类](array-view-class.md)|一个视图表示为数组中的数据\<T、 N >。|  
|[completion_future 类](completion-future-class.md)|表示相对应的将来对 c + + AMP 异步操作。|  
|[extent 类](extent-class.md)|表示一个 N 整数值，指定具有 0 起始 N 维空间的边界的向量。 坐标向量中的值进行排序从最高有效，到最不重要。 例如，在笛卡尔 3 维空间中，扩展盘区向量 (7,5,3) 表示的空间中的 z 坐标值范围从 0 到 7，y 坐标的范围介于 0 到 5，和的 x 坐标值范围从 0 到 3。|  
|[index 类](index-class.md)|定义一个 N 维索引点。|  
|[invalid_compute_domain 类](invalid-compute-domain-class.md)|当运行时无法通过使用在指定的计算域启动内核时引发的异常`parallel_for_each`调用站点。|  
|[out_of_memory 类](out-of-memory-class.md)|一种方法将因系统或设备内存不足而失败时引发的异常。|  
|[runtime_exception 类](runtime-exception-class.md)|C + + AMP 库中的异常基类型。|  
|[tile_barrier 类](tile-barrier-class.md)|功能类是仅能由系统创建并传递给平铺`parallel_for_each`作为的一部分的 lambda`tiled_index`参数。 它提供了一个方法， `wait()`，其目的是以同步线程组 (tile) 中运行的线程的执行。|  
|[tiled_extent 类](tiled-extent-class.md)|A`tiled_extent`对象是`extent`细分为一维、 二维或三维磁贴扩展盘区空间的一到三个维度的对象。|  
|[tiled_index 类](tiled-index-class.md)|提供的索引`tiled_grid`对象。 此类具有访问元素相对于本地的磁贴源和相对于全局源的属性。|  
|[uninitialized_object 类](uninitialized-object-class.md)|使用未初始化的对象时引发的异常。|  
|[unsupported_feature 类](unsupported-feature-class.md)|使用不支持的功能时引发的异常。|  
  
### <a name="enumerations"></a>枚举  
  
|名称|描述|  
|----------|-----------------|  
|[access_type 枚举](concurrency-namespace-enums-amp.md#access_type)|指定的数据访问类型。|  
|[queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)|指定在快捷键受支持的排队模式。|  
  
### <a name="operators"></a>运算符  
  
|运算符|描述|  
|--------------|-----------------|  
|[运算符 = = 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|确定指定的数据结构是否相等。|  
|[运算符 ！ = 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_neq)|确定指定的数据结构是否不相等。|  
|[operator + 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_add)|计算指定的参数的 component-wise 和。|  
|[operator-运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator-)|计算指定的自变量之间的 component-wise 差。|  
|[运算符 * 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_star)|计算指定的参数的 component-wise 积。|  
|[operator / 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_div)|计算指定的参数的 component-wise 商。|  
|[operator %运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_mod)|计算由第二个指定的自变量的第一个指定参数的模数。|  
  
### <a name="functions"></a>函数  
  
|名称|描述|  
|----------|-----------------|  
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|完成所有的内存访问之后，才能将磁贴中的所有线程的阻止执行。|  
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|取消初始化 c + + AMP 运行时。|  
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|已重载。 如果存储在指定位置的值比较的第一个指定值相等，则第二个指定的值存储在原子操作与相同的位置。|  
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|已重载。 设置存储在为指定的值作为一个原子操作的指定位置的值。|  
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|已重载。 设置存储在指定位置到该值与指定的值的总和作为一个原子操作的值。|  
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|已重载。 设置存储在指定位置到的按位值`and`该值与指定的值作为一个原子操作。|  
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|已重载。 递减的值存储在指定的位置，并将结果存储在相同的位置作为一个原子操作。|  
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|已重载。 递增存储的指定位置的值并将结果存储在相同的位置作为一个原子操作。|  
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|已重载。 设置存储在指定位置到较大的值的该值和作为一个原子操作的指定的值。|  
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|已重载。 设置存储在指定位置到较小的值的该值和作为一个原子操作的指定的值。|  
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|已重载。 设置存储在指定位置到的按位值`or`该值与指定的值作为一个原子操作。|  
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|已重载。 设置存储到差异该值与指定的值作为一个原子操作的指定位置的值。|  
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|已重载。 设置存储在指定位置到的按位值`xor`该值与指定的值作为一个原子操作。|  
|[copy](concurrency-namespace-functions-amp.md#copy)|将 c + + AMP 对象复制。 满足所有同步的数据传输要求。 代码的加速器上运行代码时，无法将复制数据。 此函数的常规形式是`copy(src, dest)`。|  
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|将 c + + AMP 对象复制并返回[completion_future](completion-future-class.md) ，可以等待。 在加速器上运行代码时，无法将复制数据。 此函数的常规形式是`copy(src, dest)`。|  
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|中止具有的函数的执行`restrict(amp)`限制子句。|  
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|打印到 Visual Studio 的格式化的字符串**输出**窗口并引发[runtime_exception](runtime-exception-class.md)具有相同的格式的异常的字符串。|  
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|打印到 Visual Studio 的格式化的字符串**输出**窗口。 从具有的函数调用`restrict(amp)`限制子句。|  
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|将磁贴，直到所有全局内存访问中的所有线程的阻止执行已完成。|  
|[parallel_for_each 函数 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|在计算域内运行了一个函数。|  
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|将阻止执行之前将磁贴中的所有线程`tile_static`内存访问已完成。|  
  
## <a name="constants"></a>常量  
  
|名称|描述|  
|----------|-----------------|  
|[HLSL_MAX_NUM_BUFFERS 常量](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|最大允许的 DirectX 的缓冲区数。|  
|[MODULENAME_MAX_LENGTH 常量](concurrency-namespace-constants-amp.md#modulename_max_length)|将存储的模块名称的最大长度。 此值必须在编译器和运行时上相同。|  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
## <a name="see-also"></a>请参阅  
 [参考 (C++ AMP)](reference-cpp-amp.md)



