---
title: array 类
ms.date: 11/04/2016
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: efea8dabb69a48e69d68a86110fdf9bc7664948b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127107"
---
# <a name="array-class"></a>array 类

表示用于将数据移动到快捷键的数据容器。

## <a name="syntax"></a>语法

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>参数

*value_type*<br/>
数据的元素类型。

*_Rank*<br/>
数组的秩。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[array 构造函数](#ctor)|初始化 `array` 类的新实例。|
|[~ 数组析构函数](#dtor)|销毁 `array` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[copy_to](#copy_to)|将数组的内容复制到另一个数组。|
|[data](#data)|返回指向数组原始数据的指针。|
|[get_accelerator_view](#get_accelerator_view)|返回表示分配数组的位置的[accelerator_view](accelerator-view-class.md)对象。 仅可在 CPU 上访问此属性。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|获取调用暂存构造函数来实例化 `array` 对象时作为参数传递的第二个[accelerator_view](accelerator-view-class.md)对象。|
|[get_cpu_access_type](#get_cpu_access_type)|返回数组的[access_type](concurrency-namespace-enums-amp.md#access_type) 。 只能在 CPU 上访问此方法。|
|[get_extent](#get_extent)|返回数组的[区](extent-class.md)对象。|
|[reinterpret_as](#reinterpret_as)|返回一个一维数组，该数组包含 `array` 对象中的所有元素。|
|[section](#section)|返回 `array` 对象的子节，该对象位于指定的源并且可以选择具有指定的范围。|
|[view_as](#view_as)|返回从 `array` 对象构造的[array_view](array-view-class.md)对象。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[运算符 std：： vector&lt;value_type&gt;](#operator_vec)|使用 `copy(*this, vector)` 将数组隐式转换为 std：：[vector](../../../standard-library/vector-class.md)对象。|
|[operator()](#operator_call)|返回由参数指定的元素值。|
|[operator\[\]](#operator_at)|返回指定索引处的元素。|
|[operator=](#operator_eq)|将指定 `array` 对象的内容复制到此对象中。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[rank 常量](#rank)|存储数组的秩。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|获取表示分配数组的位置的[accelerator_view](accelerator-view-class.md)对象。 仅可在 CPU 上访问此属性。|
|[associated_accelerator_view](#associated_accelerator_view)|获取调用暂存构造函数来实例化 `array` 对象时作为参数传递的第二个[accelerator_view](accelerator-view-class.md)对象。|
|[cpu_access_type](#cpu_access_type)|获取表示 CPU 如何访问数组存储的[access_type](concurrency-namespace-enums-amp.md#access_type) 。|
|[extent](#extent)|获取定义数组形状的范围。|

## <a name="remarks"></a>备注

类型 `array<T,N>` 表示位于特定位置（例如，加速器或 CPU）的密集和常规（非交错） *N*维数组。 数组中元素的数据类型为 `T`，该类型必须是与目标快捷键兼容的类型。 尽管秩、`N`（数组的秩是静态确定的，并且是类型的一部分，但数组的范围由运行时确定，并使用类 `extent<N>`表示。

虽然某些功能专门用于分级为 one、2和3的 `array` 对象，但数组可以具有任意数量的维度。 如果省略维度参数，则默认值为1。

数组数据在内存中连续排列。 不同于最小有效维度中的元素在内存中是相邻的。

数组逻辑上被视为值类型，因为当数组复制到另一个数组时，将执行深层复制。 两个数组从不指向相同的数据。

`array<T,N>` 类型用于几个方案：

- 作为可在快捷键上的计算中使用的数据容器。

- 作为容纳主机 CPU 上的内存的数据容器（可用于复制到其他数组或从其他数组复制）。

- 作为暂存对象，用作主机到设备副本中的快速中介。

## <a name="inheritance-hierarchy"></a>继承层次结构

`array`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="dtor"></a>~ array

销毁 `array` 的对象。

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a>accelerator_view

获取表示分配数组的位置的[accelerator_view](accelerator-view-class.md)对象。 仅可在 CPU 上访问此属性。

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="ctor"></a>组成

初始化[数组类](array-class.md)的新实例。 `array<T,N>`没有默认的构造函数。 所有构造函数仅在 CPU 上运行。 它们不能在 Direct3D 目标上执行。

```cpp
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

explicit array(
    int _E0) restrict(cpu);

explicit array(
    int _E0,
    int _E1) restrict(cpu);

explicit array(
    int _E0,
    int _E1,
    int _E2) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av,
    accelerator_view _Associated_Av) restrict(cpu);

array(const array& _Other) restrict(cpu);

array(array&& _Other) restrict(cpu);
```

### <a name="parameters"></a>参数

*_Associated_Av*<br/>
一个 accelerator_view，它指定数组的首选目标位置。

*_Av*<br/>
一个[accelerator_view](accelerator-view-class.md)对象，该对象指定数组的位置。

*_Cpu_access_type*<br/>
CPU 上的数组所需的[access_type](concurrency-namespace-enums-amp.md#access_type) 。 此参数的默认值为 `access_type_auto` 将 CPU `access_type` 确定为运行时。 可以使用 `get_cpu_access_type` 方法查询数组的实际 CPU `access_type`。

*_Extent*<br/>
数组的每个维度中的范围。

*_E0*<br/>
本节范围内最重要的组件。

*_E1*<br/>
本节范围内的最重要的组件。

*_E2*<br/>
本节范围内最不重要的组件。

*_InputIterator*<br/>
输入迭代器的类型。

*_Src*<br/>
要复制的对象。

*_Src_first*<br/>
源容器中的开始迭代器。

*_Src_last*<br/>
源容器中的结束迭代器。

*_Other*<br/>
其他数据源。

*_Rank*<br/>
部分的秩。

*value_type*<br/>
要复制的元素的数据类型。

## <a name="associated_accelerator_view"></a>associated_accelerator_view

获取调用暂存构造函数来实例化 `array` 对象时作为参数传递的第二个[accelerator_view](accelerator-view-class.md)对象。

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

将 `array` 的内容复制到其他 `array`。

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要复制到的[array_view](array-view-class.md)对象。

## <a name="cpu_access_type"></a>cpu_access_type

获取此数组允许的 CPU access_type。

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a>数据

返回指向 `array`的原始数据的指针。

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>返回值

指向数组的原始数据的指针。

## <a name="extent"></a>范围

获取用于定义 `array`的形状的[区](extent-class.md)对象。

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a>get_accelerator_view

返回[accelerator_view](accelerator-view-class.md)对象，该对象表示分配 `array` 对象的位置。 仅可在 CPU 上访问此属性。

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>返回值

表示分配 `array` 对象的位置的 `accelerator_view` 对象。

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

获取调用暂存构造函数来实例化 `array` 对象时作为参数传递的第二个[accelerator_view](accelerator-view-class.md)对象。

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>返回值

传递给暂存构造函数的第二个[accelerator_view](accelerator-view-class.md)对象。

## <a name="get_cpu_access_type"></a>get_cpu_access_type

返回此数组允许的 CPU access_type。

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>返回值

## <a name="get_extent"></a>get_extent

返回 `array`的[区](extent-class.md)对象。

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

`extent` 的 `array` 对象。

## <a name="operator_vec"></a>运算符 std：： vector&lt;value_type&gt;

使用 `copy(*this, vector)` 将数组隐式转换为 std：： vector 对象。

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>参数

*value_type*<br/>
向量的元素的数据类型。

### <a name="return-value"></a>返回值

`vector<T>` 类型的对象，该对象包含数组中包含的数据的副本。

## <a name="operator_call"></a>operator （）

返回由参数指定的元素值。

```cpp
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);

value_type& operator() (int _I0, int _I1) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;

value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
元素的位置。

*_I0*<br/>
本部分源的最重要的组件。

*_I1*<br/>
本部分起源的最重要的组件。

*_I2*<br/>
本部分起源的最不重要的组件。

*_I*<br/>
元素的位置。

### <a name="return-value"></a>返回值

由参数指定的元素值。

## <a name="operator_at"></a>运算符 []

返回指定索引处的元素。

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引。

*_I*<br/>
索引。

### <a name="return-value"></a>返回值

位于指定索引处的元素。

## <a name="operator_eq"></a>operator =

复制指定 `array` 对象的内容。

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从中进行复制的 `array` 对象。

*_Src*<br/>
要从中进行复制的 `array` 对象。

### <a name="return-value"></a>返回值

对此 `array` 对象的引用。

## <a name="rank"></a>级别

存储 `array`的排名。

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a>reinterpret_as

通过一维 array_view 来重新解释数组，可选择的值类型可能与源数组不同。

### <a name="syntax"></a>语法

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Value_type2*<br/>
返回的数据的数据类型。

### <a name="return-value"></a>返回值

基于数组的 array_view 或 const array_view 对象，元素类型重新解释从 T 到 ElementType，秩从 N 减少到1。

### <a name="remarks"></a>备注

有时，将多维数组视为线性的一维数组（可能与源数组的值类型不同），可以方便地查看多维数组。 您可以使用此方法来实现此目的。
**警告**使用不同值类型 Reinterpreting 数组对象是可能不安全的操作。 建议你仔细使用此功能。

以下代码是一个示例。

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>区

返回 `array` 对象的子节，该对象位于指定的源并且可以选择具有指定的范围。

```cpp
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);

array_view<value_type,1> section(
    int _I0,
    int _E0) restrict(amp,cpu);

array_view<const value_type,1> section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view<value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) restrict(amp,cpu);

array_view<const value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view<value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) restrict(amp,cpu);

array_view<const value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_E0*<br/>
本节范围内最重要的组件。

*_E1*<br/>
本节范围内的最重要的组件。

*_E2*<br/>
本节范围内最不重要的组件。

*_Ext*<br/>
指定节范围的[区](extent-class.md)对象。 原点为0。

*_Idx*<br/>
指定原点位置的[索引](index-class.md)对象。 子节是范围的其余部分。

*_I0*<br/>
本部分源的最重要的组件。

*_I1*<br/>
本部分起源的最重要的组件。

*_I2*<br/>
本部分起源的最不重要的组件。

*_Rank*<br/>
部分的秩。

*_Section_extent*<br/>
指定节范围的[区](extent-class.md)对象。

*_Section_origin*<br/>
指定原点位置的[索引](index-class.md)对象。

*value_type*<br/>
要复制的元素的数据类型。

### <a name="return-value"></a>返回值

返回 `array` 对象的子节，该对象位于指定的源并且可以选择具有指定的范围。 仅指定 `index` 对象时，子节包含关联网格中的所有元素，这些元素的索引大于 `index` 对象中元素的索引。

## <a name="view_as"></a>view_as

重新解释此数组作为不同级别的[array_view](array-view-class.md) 。

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_New_rank*<br/>
作为参数传递的 `extent` 对象的排名。

*_View_extent*<br/>
用于构造新的[array_view](array-view-class.md)对象的范围。

*value_type*<br/>
原始 `array` 对象和返回的 `array_view` 对象中的元素的数据类型。

### <a name="return-value"></a>返回值

构造的[array_view](array-view-class.md)对象。

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
