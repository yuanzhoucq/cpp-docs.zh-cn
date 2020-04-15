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
ms.openlocfilehash: 1187b745a6d8c903c22958185be8d98a6e3d0204
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376350"
---
# <a name="concurrency-namespace-functions-amp"></a>并发命名空间函数 (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange 函数 (C++ AMP)](#atomic_exchange)|[atomic_fetch_add 函数 (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and 函数 (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or 函数 (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub功能（C++安培）](#atomic_fetch_sub)|
|[atomic_fetch_xor 函数 (C++ AMP)](#atomic_fetch_xor)|[复制](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each 函数 (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a><a name="all_memory_fence"></a>all_memory_fence

阻止执行磁贴中的所有线程，直到完成所有内存访问。 这可确保线程磁贴中的其他线程对所有内存访问都可见，并且按程序顺序执行。

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
`tile_barrier` 对象。

## <a name="amp_uninitialize"></a><a name="amp_uninitialize"></a>amp_uninitialize

取消初始化C++ AMP 运行时。 在应用程序生存期内多次调用此函数是合法的。 调用此函数后调用任何C++ AMP API 将重新初始化 C++ AMP 运行时。 请注意，跨调用此函数C++ AMP 对象是非法的，这样做将导致未定义的行为。 此外，同时调用此函数和任何其他 AMP API 是非法的，将导致未定义的行为。

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a><a name="atomic_compare_exchange"></a>atomic_compare_exchange

原子方式将存储在第一个参数中指定的内存位置的值与第二个指定参数的值进行比较，如果值相同，则内存位置的值将更改为第三个指定参数的值。

```cpp
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
读取要比较的一个值的位置，以及要存储新值（如果有）的位置。

*_Expected_value*<br/>
读取要比较的第二个值的位置。

*value*<br/>
要存储到 的内存位置 的值，`_Dest`如果`_Dest`等于 。 `_Expected_value`

### <a name="return-value"></a>返回值

如果操作成功，**为 true;** 否则，**假**。

## <a name="atomic_exchange-function-c-amp"></a><a name="atomic_exchange"></a>atomic_exchange功能（C++安培）

像原子运算那样设置目标位置的值。

```cpp
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

*value*<br/>
新值。

### <a name="return-value"></a>返回值

目标位置的初始值。

## <a name="atomic_fetch_add-function-c-amp"></a><a name="atomic_fetch_add"></a>atomic_fetch_add功能（C++安培）

以原子方式向内存位置的值添加值。

```cpp
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

*value*<br/>
要添加的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

## <a name="atomic_fetch_and-function-c-amp"></a><a name="atomic_fetch_and"></a>atomic_fetch_and功能（C++安培）

原子上执行值和内存位置的值的位和操作。

```cpp
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

*value*<br/>
要在位和计算中使用的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

## <a name="atomic_fetch_dec"></a><a name="atomic_fetch_dec"></a>atomic_fetch_dec

从原子上递减存储在指定内存位置的值。

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要递减的值的内存中的位置。

### <a name="return-value"></a>返回值

存储在内存位置的原始值。

## <a name="atomic_fetch_inc"></a><a name="atomic_fetch_inc"></a>atomic_fetch_inc

以原子方式增加存储在指定内存位置的值。

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要递增的值的内存中的位置。

### <a name="return-value"></a>返回值

存储在内存位置的原始值。

## <a name="atomic_fetch_max"></a><a name="atomic_fetch_max"></a>atomic_fetch_max

原子计算存储在第一个参数中指定的内存位置的值和第二个参数中指定的值之间的最大值，并将其存储在相同的内存位置。

```cpp
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
读取要比较的一个值的位置，以及将两个值的最大值存储到的位置。

*value*<br/>
要与指定位置的值进行比较的值。

### <a name="return-value"></a>返回值

存储在指定位置的原始值。

## <a name="atomic_fetch_min"></a><a name="atomic_fetch_min"></a>atomic_fetch_min

以原子方式计算存储在第一个参数中指定的内存位置的值和第二个参数中指定的值之间的最小值，并将其存储在相同的内存位置。

```cpp
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
读取要比较的一个值的位置，以及要存储两个值的最小值的位置。

*value*<br/>
要与指定位置的值进行比较的值。

### <a name="return-value"></a>返回值

存储在指定位置的原始值。

## <a name="atomic_fetch_or-function-c-amp"></a><a name="atomic_fetch_or"></a>atomic_fetch_or功能（C++安培）

通过一个值和一个内存位置的值在原子级别执行按位或运算。

```cpp
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

*value*<br/>
用于执行按位或计算的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

## <a name="atomic_fetch_sub-function-c-amp"></a><a name="atomic_fetch_sub"></a>atomic_fetch_sub功能（C++安培）

从内存位置以原子方式减去值。

```cpp
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

*value*<br/>
要减去的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

## <a name="atomic_fetch_xor-function-c-amp"></a><a name="atomic_fetch_xor"></a>atomic_fetch_xor功能（C++安培）

原子上执行值和内存位置的位 XOR 操作。

```cpp
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

*value*<br/>
要在 XOR 计算中使用的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

## <a name="copy"></a><a name="copy"></a>复制

复制C++ AMP 对象。 满足所有同步数据传输要求。 在加速器上运行代码时，无法复制数据。 此函数的一般形式是`copy(src, dest)`。

```cpp
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
要复制到的对象。

*_DestIter*<br/>
到目标处开始位置的输出迭代器。

*输入迭代器*<br/>
输入迭代器的类型。

*输出迭代器*<br/>
输出迭代器的类型。

*_Rank*<br/>
要复制的对象的排名或要复制到的对象。

*_Src*<br/>
以反对复制。

*_SrcFirst*<br/>
到源容器的开始迭代器。

*_SrcLast*<br/>
到源容器的结束迭代器。

*value_type*<br/>
复制的元素的数据类型。

## <a name="copy_async"></a><a name="copy_async"></a>copy_async

复制C++ AMP 对象并返回可以等待[的对象completion_future。](completion-future-class.md) 在加速器上运行代码时，无法复制数据。  此函数的一般形式是`copy(src, dest)`。

```cpp
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
要复制到的对象。

*_DestIter*<br/>
到目标处开始位置的输出迭代器。

*输入迭代器*<br/>
输入迭代器的类型。

*输出迭代器*<br/>
输出迭代器的类型。

*_Rank*<br/>
要复制的对象的排名或要复制到的对象。

*_Src*<br/>
以反对复制。

*_SrcFirst*<br/>
到源容器的开始迭代器。

*_SrcLast*<br/>
到源容器的结束迭代器。

*value_type*<br/>
复制的元素的数据类型。

### <a name="return-value"></a>返回值

`future<void>`可以等待的。

## <a name="direct3d_abort"></a><a name="direct3d_abort"></a>direct3d_abort

用 `restrict(amp)` 限制子句中止函数的执行。 当 AMP 运行时检测该调用时，将引发 [runtime_exception](runtime-exception-class.md) 异常并显示错误消息“参考光栅器: 命中着色器中止指令”。

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a><a name="direct3d_errorf"></a>direct3d_errorf

将格式化的字符串打印到可视化工作室输出窗口。 它从具有限制子句的`restrict(amp)`函数调用。 当 AMP 运行时检测到调用时，它会引发具有相同格式字符串[runtime_exception](runtime-exception-class.md)异常。

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a><a name="direct3d_printf"></a>direct3d_printf

将格式化的字符串打印到可视化工作室输出窗口。 它从具有限制子句的`restrict(amp)`函数调用。

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a><a name="global_memory_fence"></a>global_memory_fence

阻止执行磁贴中的所有线程，直到完成所有全局内存访问。 这可确保全局内存访问对线程磁贴中的其他线程可见，并且按程序顺序执行。

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
tile_barrier对象

## <a name="parallel_for_each-function-c-amp"></a><a name="parallel_for_each"></a>parallel_for_each功能（C++安培）

跨计算域运行函数。 有关详细信息，请参阅[C++ AMP 概述](../../../parallel/amp/cpp-amp-overview.md)。

```cpp
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
要`accelerator_view`运行并行计算的对象。

*_Compute_domain*<br/>
包含`extent`计算数据的对象。

*_Dim0*<br/>
`tiled_extent`对象的维度。

*_Dim1*<br/>
`tiled_extent`对象的维度。

*_Dim2*<br/>
`tiled_extent`对象的维度。

*_Kernel*<br/>
采用类型为"索引\<_Rank>"并执行并行计算的参数的 lambda 或函数对象。

*_Kernel_type*<br/>
羊羔或娱乐。

*_Rank*<br/>
范围的等级。

## <a name="tile_static_memory_fence"></a><a name="tile_static_memory_fence"></a>tile_static_memory_fence

阻止执行磁贴中的所有线程，直到完成所有未完成的`tile_static`内存访问。 这可确保`tile_static`内存访问对线程磁贴中的其他线程可见，并且按程序顺序执行访问。

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
tile_barrier对象。

## <a name="see-also"></a>另请参阅

[Concurrency 命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
