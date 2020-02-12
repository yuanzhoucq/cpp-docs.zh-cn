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
ms.openlocfilehash: 90a23ce111f7307610de3f0ad4bcec05d8de27df
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126888"
---
# <a name="concurrency-namespace-functions-amp"></a>并发命名空间函数 (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange 函数（C++ AMP）](#atomic_exchange)|[atomic_fetch_add 函数（C++ AMP）](#atomic_fetch_add)|[atomic_fetch_and 函数（C++ AMP）](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or 函数（C++ AMP）](#atomic_fetch_or)|[atomic_fetch_sub 函数（C++ AMP）](#atomic_fetch_sub)|
|[atomic_fetch_xor 函数（C++ AMP）](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each 函数（C++ AMP）](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a>all_memory_fence

阻止在磁贴中所有线程的执行，直到所有内存访问都完成。 这可确保所有内存访问对于线程平铺中的其他线程都可见，并按程序顺序执行。

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
一个 `tile_barrier` 对象。

## <a name="amp_uninitialize"></a>amp_uninitialize

取消C++ AMP 运行时。 在应用程序生存期内多次调用此函数是合法的。 调用此C++函数后调用任何 amp API 将重新初始化C++ amp 运行时。 请注意，对此函数的C++调用使用 AMP 对象是非法的，这样做将导致未定义的行为。 同时，同时调用此函数和任何其他 AMP Api 是非法的，并会导致未定义的行为。

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a>atomic_compare_exchange

以原子方式比较第一个参数中指定的内存位置上存储的值是否与第二个指定参数的值相等，如果值相同，则将内存位置的值更改为第三个指定参数的值。

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
从中进行比较的值的读取位置，若要存储新值（如果有），则为。

*_Expected_value*<br/>
要从其进行比较的第二个值的读取位置。

*value*<br/>
要存储到中指定的内存位置的值（如果 `_Dest` 等于 `_Expected_value`，则 `_Dest`。

### <a name="return-value"></a>返回值

如果操作成功，则为**true** ;否则**为 false**。

## <a name="atomic_exchange"></a>atomic_exchange 函数（C++ AMP）

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

## <a name="atomic_fetch_add"></a>atomic_fetch_add 函数（C++ AMP）

以原子方式将一个值添加到内存位置的值。

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

## <a name="atomic_fetch_and"></a>atomic_fetch_and 函数（C++ AMP）

以原子方式对值和内存位置的值执行 "位与" 运算。

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
要在按位 "与" 运算中使用的值。

### <a name="return-value"></a>返回值

内存位置的初始值。

## <a name="atomic_fetch_dec"></a>atomic_fetch_dec

以原子方式递减存储在指定内存位置的值。

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要递减的值在内存中的位置。

### <a name="return-value"></a>返回值

存储在内存位置的原始值。

## <a name="atomic_fetch_inc"></a>atomic_fetch_inc

以原子方式递增存储在指定内存位置的值。

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要递增的值在内存中的位置。

### <a name="return-value"></a>返回值

存储在内存位置的原始值。

## <a name="atomic_fetch_max"></a>atomic_fetch_max

以原子方式计算存储在第一个参数中指定的内存位置的值与第二个参数中指定的值之间的最大值，并将其存储在相同的内存位置。

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
从中进行比较的值的读取位置，最多可存储两个值中的最大值。

*value*<br/>
要与指定位置的值进行比较的值。

### <a name="return-value"></a>返回值

存储在指定位置位置的原始值。

## <a name="atomic_fetch_min"></a>atomic_fetch_min

以原子方式计算存储在第一个参数中指定的内存位置的值与第二个参数中指定的值之间的最小值，并将其存储在相同的内存位置。

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
要从中进行比较的值的读取位置，最小值为存储的两个值。

*value*<br/>
要与指定位置的值进行比较的值。

### <a name="return-value"></a>返回值

存储在指定位置位置的原始值。

## <a name="atomic_fetch_or"></a>atomic_fetch_or 函数（C++ AMP）

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

## <a name="atomic_fetch_sub"></a>atomic_fetch_sub 函数（C++ AMP）

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

## <a name="atomic_fetch_xor"></a>atomic_fetch_xor 函数（C++ AMP）

以原子方式执行值和内存位置的按位 XOR 运算。

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

## <a name="copy"></a>  copy

复制C++ AMP 对象。 满足所有同步数据传输要求。 在加速器上运行代码时，不能复制数据。 此函数的常规形式是 `copy(src, dest)`。

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
指向目标位置处的起始位置的输出迭代器。

*InputIterator*<br/>
输入迭代器的类型。

*OutputIterator*<br/>
输出迭代器的类型。

*_Rank*<br/>
要从其复制的对象或要复制到的对象的级别。

*_Src*<br/>
要复制的对象。

*_SrcFirst*<br/>
源容器中的开始迭代器。

*_SrcLast*<br/>
源容器中的结束迭代器。

*value_type*<br/>
要复制的元素的数据类型。

## <a name="copy_async"></a>copy_async

复制C++ AMP 对象并返回可等待的[completion_future](completion-future-class.md)对象。 在加速器上运行代码时，不能复制数据。  此函数的常规形式是 `copy(src, dest)`。

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
指向目标位置处的起始位置的输出迭代器。

*InputIterator*<br/>
输入迭代器的类型。

*OutputIterator*<br/>
输出迭代器的类型。

*_Rank*<br/>
要从其复制的对象或要复制到的对象的级别。

*_Src*<br/>
要复制的对象。

*_SrcFirst*<br/>
源容器中的开始迭代器。

*_SrcLast*<br/>
源容器中的结束迭代器。

*value_type*<br/>
要复制的元素的数据类型。

### <a name="return-value"></a>返回值

可以等待的 `future<void>`。

## <a name="direct3d_abort"></a>direct3d_abort

用 `restrict(amp)` 限制子句中止函数的执行。 当 AMP 运行时检测该调用时，将引发 [runtime_exception](runtime-exception-class.md) 异常并显示错误消息“参考光栅器: 命中着色器中止指令”。

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a>direct3d_errorf

打印格式化的字符串到 Visual Studio "输出" 窗口。 它通过 `restrict(amp)` 限制子句的函数进行调用。 当 AMP 运行时检测到调用时，它将使用相同的格式设置字符串引发[runtime_exception](runtime-exception-class.md)异常。

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a>direct3d_printf

打印格式化的字符串到 Visual Studio "输出" 窗口。 它通过 `restrict(amp)` 限制子句的函数进行调用。

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a>global_memory_fence

阻止在磁贴中所有线程的执行，直到所有全局内存访问都完成。 这可确保全局内存访问对于线程平铺中的其他线程可见，并按程序顺序执行。

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
一个 tile_barrier 对象

## <a name="parallel_for_each"></a>parallel_for_each 函数（C++ AMP）

跨计算域运行函数。 有关详细信息，请参阅[ C++ AMP 概述](../../../parallel/amp/cpp-amp-overview.md)。

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
要对其运行并行计算的 `accelerator_view` 对象。

*_Compute_domain*<br/>
包含计算数据的 `extent` 对象。

*_Dim0*<br/>
`tiled_extent` 对象的维度。

*_Dim1*<br/>
`tiled_extent` 对象的维度。

*_Dim2*<br/>
`tiled_extent` 对象的维度。

*_Kernel*<br/>
一个 lambda 或函数对象，它采用类型为 "index\<_Rank >" 的自变量，并执行并行计算。

*_Kernel_type*<br/>
Lambda 或函子。

*_Rank*<br/>
范围的秩。

## <a name="tile_static_memory_fence"></a>tile_static_memory_fence

阻止在磁贴中所有线程的执行，直到完成所有未完成的 `tile_static` 内存访问。 这可确保 `tile_static` 内存访问对线程平铺中的其他线程可见，并按程序顺序执行访问。

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>参数

*_Barrier*<br/>
一个 tile_barrier 对象。

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
