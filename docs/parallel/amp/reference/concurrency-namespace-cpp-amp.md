---
title: "并发 Namespace (c + + AMP) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AMP/Concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 38c3154244b163202bcb8e271f96b393231247ca
ms.lasthandoff: 03/17/2017

---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 命名空间 (C++ AMP)
提供类和在数据并行硬件加速执行 c + + 代码的函数。 有关详细信息，请参阅[c + + AMP 概述](../cpp-amp-overview.md)  
  
## <a name="syntax"></a>语法  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>成员  
  
### <a name="namespaces"></a>命名空间  
  
|名称|描述|  
|----------|-----------------|  
|[Concurrency::direct3d 命名空间](concurrency-direct3d-namespace.md)|提供了支持 D3D 互操作性的函数。 启用无缝使用 D3D 资源 AMP 代码中的计算和在 AMP 中创建在 D3D 代码中，而无需创建多余的中间副本的资源的使用。 C + + AMP 可用于以增量方式加速 DirectX 应用程序的需要进行大量计算部分和对数据产生的 AMP 计算中使用 D3D API。|  
|[Concurrency::fast_math 命名空间](concurrency-fast-math-namespace.md)|中的函数`fast_math`命名空间不符合 C99 标准。 提供了只有单精度的每个函数的版本。 这些函数将使用 DirectX 内部函数，其速度要快于中的相应函数`precise_math`命名空间并不需要扩展的双精度支持加速器，但它们是不太准确。 有两个版本的每个函数的源代码级别与 C99 代码; 的兼容性这两个版本采用并返回单精度值。|  
|[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)|图形编程提供类型和设计的函数。|  
|[Concurrency::precise_math 命名空间](concurrency-precise-math-namespace.md)|中的函数`precise_math`命名空间是符合 C99。 每个函数的单精度和双精度版本不包括在内。 这些函数，其中包括单精度函数 — 需要扩展的双精度支持加速器。|  
  
### <a name="classes"></a>类  
  
|名称|说明|  
|----------|-----------------|  
|[accelerator 类](accelerator-class.md)|表示物理 DP 优化计算节点的抽象。|  
|[accelerator_view 类](accelerator-view-class.md)|表示在 c + + AMP 数据并行快捷键上的虚拟设备抽象。|  
|[accelerator_view_removed 类](accelerator-view-removed-class.md)|基础 DirectX 调用因 Windows 超时检测和恢复机制而失败时引发的异常。|  
|[array 类](array-class.md)|数据聚合的`accelerator_view`网格域中。 它是变量，一个用于网格域中的每个元素的集合。 每个变量可保存到一些 c + + 类型相对应的值。|  
|[array_view 类](array-view-class.md)|表示一个数组中的数据视图\<T、 N&1;>。|  
|[completion_future 类](completion-future-class.md)|表示相对应的将来对 c + + AMP 异步操作。|  
|[extent 类](extent-class.md)|表示指定 N 维空间中具有原点为 0 的边界的 N 整数值的向量。 坐标的向量中的值按照从最重要到最不重要的顺序排列。 例如，在笛卡尔 3 维空间中，扩展盘区矢量 (7,5,3) 代表在其中的 z 坐标范围从 0 到 7，y 坐标范围从 0 到 5、 和的 x 坐标值范围从 0 到 3 的空间。|  
|[index 类](index-class.md)|定义一个 N 维索引点。|  
|[invalid_compute_domain 类](invalid-compute-domain-class.md)|在运行时无法通过使用在指定的计算域启动内核时引发的异常`parallel_for_each`调用站点。|  
|[out_of_memory 类](out-of-memory-class.md)|一种方法将因系统或设备的内存不足而失败时，将引发异常。|  
|[runtime_exception 类](runtime-exception-class.md)|C + + AMP 库中的异常基类型。|  
|[tile_barrier 类](tile-barrier-class.md)|仅能由系统创建并传递到的功能类平铺`parallel_for_each`作为的一部分的 lambda`tiled_index`参数。 它提供了一种方法， `wait()`，其目的是同步线程组 (tile) 中运行的线程的执行。|  
|[tiled_extent 类](tiled-extent-class.md)|一个`tiled_extent`对象是`extent`细分为一维、 二维或三维平铺的扩展盘区空间的一到三个维度的对象。|  
|[tiled_index 类](tiled-index-class.md)|提供到索引`tiled_grid`对象。 此类的属性来访问元素相对于本地磁贴原点和相对于全局源。|  
|[uninitialized_object 类](uninitialized-object-class.md)|使用未初始化的对象时引发的异常。|  
|[unsupported_feature 类](unsupported-feature-class.md)|使用不受支持的功能时引发的异常。|  
  
### <a name="enumerations"></a>枚举  
  
|名称|说明|  
|----------|-----------------|  
|[access_type 枚举](concurrency-namespace-enums-amp.md#access_type)|指定数据访问类型。|  
|[queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)|指定在快捷键支持的排队模式。|  
  
### <a name="operators"></a>运算符  
  
|运算符|描述|  
|--------------|-----------------|  
|[运算符 = = 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|确定指定的数据结构是否相等。|  
|[运算符 ！ = 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_neq)|确定指定的数据结构是否不相等。|  
|[operator + 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_add)|计算指定的参数的 component-wise 和。|  
|[operator-运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator-)|计算指定的参数之间的 component-wise 差异。|  
|[运算符 * 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_star)|计算指定的参数的 component-wise 积。|  
|[运算符 / 运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_div)|计算指定的参数的 component-wise 商。|  
|[operator %运算符 (c + + AMP)](concurrency-namespace-operators-amp.md#operator_mod)|计算的第二个指定的参数的第一个指定参数的模数。|  
  
### <a name="functions"></a>函数  
  
|名称|描述|  
|----------|-----------------|  
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|块中的图块，直到完成所有的内存访问的所有线程执行。|  
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|取消初始化 c + + AMP 运行时。|  
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|已重载。 如果存储在指定位置的值比较的第一个指定值相等，则第二个指定的值存储在同一位置作为一个原子操作。|  
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|已重载。 设置存储在为指定的值作为一个原子操作的指定位置处的值。|  
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|已重载。 设置存储在该值与指定的值的总和作为一个原子操作的指定位置处的值。|  
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|已重载。 设置存储在指定的位置为按位值`and`该值与指定的值作为一个原子操作。|  
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|已重载。 递减的值存储在指定的位置，并将结果存储在同一位置作为一个原子操作。|  
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|已重载。 递增存储的指定位置的值并将结果存储在同一位置作为一个原子操作。|  
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|已重载。 设置存储在指定的位置为较大值以及该值作为一个原子操作的指定的值。|  
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|已重载。 设置存储在指定位置到较小的值以及该值作为一个原子操作的指定的值。|  
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|已重载。 设置存储在指定的位置为按位值`or`该值与指定的值作为一个原子操作。|  
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|已重载。 设置存储到差异该值与指定的值作为一个原子操作的指定位置的值。|  
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|已重载。 设置存储在指定的位置为按位值`xor`该值与指定的值作为一个原子操作。|  
|[copy](concurrency-namespace-functions-amp.md#copy)|将 c + + AMP 对象复制。 满足所有同步数据传输要求。 当代码在快捷键上运行代码时，无法复制数据。 此函数的常规形式`copy(src, dest)`。|  
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|复制 c + + AMP 对象并返回[completion_future](completion-future-class.md) ，可以等待。 在快捷键上运行代码时，无法复制数据。 此函数的常规形式`copy(src, dest)`。|  
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|中止具有的函数的执行`restrict(amp)`限制子句。|  
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|打印到 Visual Studio 的格式化的字符串**输出**窗口，并引发[runtime_exception](runtime-exception-class.md)异常有相同的格式字符串。|  
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|打印到 Visual Studio 的格式化的字符串**输出**窗口。 从具有的函数调用`restrict(amp)`限制子句。|  
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|直到所有全局内存存取平铺中的所有线程的阻止执行已完成。|  
|[parallel_for_each 函数 (c + + AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|在计算域内运行了一个函数。|  
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|阻止，直到 tile 中的所有线程的执行`tile_static`内存访问已完成。|  
  
## <a name="constants"></a>常量  
  
|名称|描述|  
|----------|-----------------|  
|[HLSL_MAX_NUM_BUFFERS 常量](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|允许的 DirectX 的缓冲区的最大数目。|  
|[MODULENAME_MAX_LENGTH 常量](concurrency-namespace-constants-amp.md#modulename_max_length)|将存储模块名称的最大长度。 此值必须在编译器和运行时上相同。|  
  
## <a name="requirements"></a>要求  
 **标头：** amp.h  
  
## <a name="see-also"></a>另请参阅  
 [参考 (C++ AMP)](reference-cpp-amp.md)




