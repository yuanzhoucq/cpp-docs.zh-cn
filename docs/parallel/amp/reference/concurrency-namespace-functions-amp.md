---
title: 并发命名空间函数 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: 7baae51480c273ca023856253af7963ac83d7c92
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284835"
---
# <a name="concurrency-namespace-functions-amp"></a>并发命名空间函数 (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange 函数 (c + + AMP)](#atomic_exchange)|[atomic_fetch_add 函数 (c + + AMP)](#atomic_fetch_add)|[atomic_fetch_and 函数 (c + + AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or 函数 (c + + AMP)](#atomic_fetch_or)|[atomic_fetch_sub 函数 (c + + AMP)](#atomic_fetch_sub)|
|[atomic_fetch_xor 函数 (c + + AMP)](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each 函数 (c + + AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

##  <a name="all_memory_fence"></a>  all_memory_fence

阻止直到所有内存访问都完成的磁贴中的所有线程的执行。 这可确保所有内存访问对于线程平铺中的其他线程是可见的并按程序顺序执行。

```
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
一个 `tile_barrier` 对象。

##  <a name="amp_uninitialize"></a>  amp_uninitialize

取消初始化 c + + AMP 运行时。 它是合法的应用程序生命周期内多次调用此函数。 调用任何调用此函数的 c + + AMP API 后，将重新初始化 c + + AMP 运行时。 请注意，它是非法中对此函数的调用中使用 c + + AMP 对象这样做将导致未定义的行为。 此外，同时调用此函数和任何其他 AMP Api 是非法的并会导致未定义的行为。

```
void __cdecl amp_uninitialize();
```

##  <a name="atomic_compare_exchange"></a>  atomic_compare_exchange

以原子方式比较存储在内存位置的值中指定的第二个指定的参数值相等的第一个参数，如果值是相同的位于内存位置的值更改为第三个指定参数。

```
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,
    _Inout_ int* _Expected_value,
    int value
    ) restrict(amp)

inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,
    _Inout_ unsigned int* _Expected_value,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
读取从要进行比较的值的哪一个位置，并向其新值，如果有的话，是要存储。

*_Expected_value*<br/>
从中读取要进行比较的第二个值的位置。

*值*<br/>
要存储到指定的内存位置的值`_Dest`如果`_Dest`等同于`_Expected_value`。

### <a name="return-value"></a>返回值

**true**如果操作成功; 否则为**false**。

##  <a name="atomic_exchange"></a>  atomic_exchange 函数 (c + + AMP)

像原子运算那样设置目标位置的值。

```
inline int atomic_exchange(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)

inline float atomic_exchange(
    _Inout_ float* _Dest,
    float value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
指向目标位置的指针。

*值*<br/>
新值。

### <a name="return-value"></a>返回值

目标位置的初始值。

##  <a name="atomic_fetch_add"></a>  atomic_fetch_add 函数 (c + + AMP)

以原子方式将值添加到的内存位置的值。

```
inline int atomic_fetch_add(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
指向该内存位置的指针。

*值*<br/>
要添加的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

##  <a name="atomic_fetch_and"></a>  atomic_fetch_and 函数 (c + + AMP)

以原子方式执行值和一个内存位置的值的按位 AND 运算。

```
inline int atomic_fetch_and(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
指向该内存位置的指针。

*值*<br/>
要使用按位 AND 计算中的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

##  <a name="atomic_fetch_dec"></a>  atomic_fetch_dec

以原子方式递减的值存储在指定的内存位置。

```
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要递减的值的内存中的位置。

### <a name="return-value"></a>返回值

存储在内存位置的原始值。

##  <a name="atomic_fetch_inc"></a>  atomic_fetch_inc

以原子方式递增存储在指定的内存位置的值。

```
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要递增的值的内存中的位置。

### <a name="return-value"></a>返回值

存储在内存位置的原始值。

##  <a name="atomic_fetch_max"></a>  atomic_fetch_max

以原子方式计算存储在第一个参数，第二个参数中指定的值中指定的内存位置的值之间的最大值，并将其存储在同一个内存位置。

```
inline int atomic_fetch_max(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
读取从要进行比较的值的哪一个位置，并且两个值的最大已存储。

*值*<br/>
要与位于指定位置处的值进行比较的值。

### <a name="return-value"></a>返回值

存储在指定的位置的原始值。

##  <a name="atomic_fetch_min"></a>  atomic_fetch_min

以原子方式计算存储在第一个参数，第二个参数中指定的值中指定的内存位置的值之间的最小值，并将其存储在同一个内存位置。

```
inline int atomic_fetch_min(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
读取从要进行比较的值的哪一个位置，以及两个值的最小值是要存储。

*值*<br/>
要与位于指定位置处的值进行比较的值。

### <a name="return-value"></a>返回值

存储在指定的位置的原始值。

##  <a name="atomic_fetch_or"></a>  atomic_fetch_or 函数 (c + + AMP)

通过一个值和一个内存位置的值在原子级别执行按位或运算。

```
inline int atomic_fetch_or(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
指向该内存位置的指针。

*值*<br/>
用于执行按位或计算的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

##  <a name="atomic_fetch_sub"></a>  atomic_fetch_sub 函数 (c + + AMP)

以原子方式从减去的值的内存位置。

```
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
指向目标位置的指针。

*值*<br/>
要减去的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

##  <a name="atomic_fetch_xor"></a>  atomic_fetch_xor 函数 (c + + AMP)

以原子方式为 peforms 值和内存位置的按位 XOR 运算。

```
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>参数

*_Dest*<br/>
指向该内存位置的指针。

*值*<br/>
要使用 XOR 计算中的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

##  <a name="copy"></a>  copy

复制 c + + AMP 对象。 满足所有同步数据传输要求。 当在加速器上运行代码时，不能将数据复制。 此函数的一般形式为`copy(src, dest)`。

```
template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
   OutputIterator _DestIter);

template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要将复制到的对象。

*_DestIter*<br/>
指向目标处的开始位置的输出迭代器。

*InputIterator*<br/>
输入迭代器的类型。

*OutputIterator*<br/>
输出迭代器的类型。

*_Rank*<br/>
要从复制的对象或要将复制到的对象的秩。

*_Src*<br/>
若要要复制的对象。

*_SrcFirst*<br/>
进入源容器开始迭代器。

*_SrcLast*<br/>
进入源容器结束迭代器。

*value_type*<br/>
复制的元素数据类型。

##  <a name="copy_async"></a>  copy_async

复制 c + + AMP 对象并返回[completion_future](completion-future-class.md)可等待的对象。 当在加速器上运行代码时，不能将数据复制。  此函数的一般形式为`copy(src, dest)`。

```
template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要将复制到的对象。

*_DestIter*<br/>
指向目标处的开始位置的输出迭代器。

*InputIterator*<br/>
输入迭代器的类型。

*OutputIterator*<br/>
输出迭代器的类型。

*_Rank*<br/>
要从复制的对象或要将复制到的对象的秩。

*_Src*<br/>
若要要复制的对象。

*_SrcFirst*<br/>
进入源容器开始迭代器。

*_SrcLast*<br/>
进入源容器结束迭代器。

*value_type*<br/>
复制的元素数据类型。

### <a name="return-value"></a>返回值

一个`future<void>`的可等待。

##  <a name="direct3d_abort"></a>  direct3d_abort

用 `restrict(amp)` 限制子句中止函数的执行。 当 AMP 运行时检测该调用时，将引发[runtime_exception](runtime-exception-class.md)异常并显示错误消息"参考光栅器：命中着色器中止指令"。

```
void direct3d_abort() restrict(amp);
```

##  <a name="direct3d_errorf"></a>  direct3d_errorf

打印格式化的字符串到 Visual Studio 输出窗口。 从与函数调用`restrict(amp)`限制子句。 当 AMP 运行时检测该调用时，将引发[runtime_exception](runtime-exception-class.md)使用相同的格式设置字符串的异常。

```
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

##  <a name="direct3d_printf"></a>  direct3d_printf

打印格式化的字符串到 Visual Studio 输出窗口。 从与函数调用`restrict(amp)`限制子句。

```
void direct3d_printf(
    const char *,
...) restrict(amp);
```

##  <a name="global_memory_fence"></a>  global_memory_fence

阻止执行，直到所有全局内存访问的磁贴中的所有线程的已完成。 这可确保全局内存访问对于线程平铺中的其他线程是可见的并按程序顺序执行。

```
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
Tile_barrier 对象

##  <a name="parallel_for_each"></a>  parallel_for_each 函数 (c + + AMP)

计算域之间运行函数。 有关详细信息，请参阅[c + + AMP 概述](../../../parallel/amp/cpp-amp-overview.md)。

```
template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
   const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);
```

### <a name="parameters"></a>参数

*_Accl_view*<br/>
`accelerator_view`对象运行的并行计算。

*_Compute_domain*<br/>
`extent`对象，其中包含计算的数据。

*_Dim0*<br/>
维度的`tiled_extent`对象。

*_Dim1*<br/>
维度的`tiled_extent`对象。

*_Dim2*<br/>
维度的`tiled_extent`对象。

*_Kernel*<br/>
使用类型的自变量的 lambda 或函数对象"索引\<_Rank >"，并执行并行计算。

*_Kernel_type*<br/>
Lambda 或仿函数。

*_Rank*<br/>
范围的等级。

##  <a name="tile_static_memory_fence"></a>  tile_static_memory_fence

阻止平铺中的所有线程的执行，直至将所有未完成`tile_static`内存访问都完成。 这可确保`tile_static`内存访问是线程平铺中的其他线程可见并访问按程序顺序执行。

```
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
Tile_barrier 对象。

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
