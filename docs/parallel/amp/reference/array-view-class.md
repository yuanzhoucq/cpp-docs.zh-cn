---
title: array_view 类
ms.date: 11/04/2016
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: 2aef75eedcde2a2064fe12815d9afd21fee2c293
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127132"
---
# <a name="array_view-class"></a>array_view 类

表示包含在另一个容器中的数据的 N 维视图。

## <a name="syntax"></a>语法

```cpp
template <
    typename value_type,
    int _Rank = 1
>
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;

template <
    typename value_type,
    int _Rank
>
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;
```

### <a name="parameters"></a>参数

*value_type*<br/>
`array_view` 对象中元素的数据类型。

*_Rank*<br/>
`array_view` 对象的秩。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[array_view 构造函数](#ctor)|初始化 `array_view` 类的新实例。 `array<T,N>`没有默认的构造函数。 所有构造函数仅在 CPU 上运行，并且不能在 Direct3D 目标上执行。|
|[~ array_view 析构函数](#ctor)|销毁 `array_view` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[copy_to](#copy_to)|通过调用 `copy(*this, dest)`将 `array_view` 对象的内容复制到指定的目标。|
|[data](#data)|返回指向 `array_view`的原始数据的指针。|
|[discard_data](#discard_data)|丢弃此视图的当前数据。|
|[get_extent](#get_extent)|返回 array_view 对象的 extent 对象。|
|[get_ref](#get_ref)|返回对已编制索引的元素的引用。|
|[get_source_accelerator_view](#get_source_accelerator_view)|返回 `array_view` 的数据源所在的[accelerator_view](accelerator-view-class.md) 。|
|[刷新](#refresh)|通知 `array_view` 对象其绑定内存已在 `array_view` 接口外部进行了修改。 对此方法的调用将呈现过时的所有缓存信息。|
|[reinterpret_as](#reinterpret_as)|返回一个一维数组，该数组包含 `array_view` 对象中的所有元素。|
|[section](#section)|返回 `array_view` 对象的子节，该对象位于指定的源并且可以选择具有指定的范围。|
|[synchronize](#synchronize)|将对 `array_view` 对象所做的任何修改同步回其源数据。|
|[synchronize_async](#synchronize_async)|将对 `array_view` 对象所做的任何修改异步同步回其源数据。|
|[synchronize_to](#synchronize_to)|将对 `array_view` 对象所做的任何修改同步到指定的[accelerator_view](accelerator-view-class.md)。|
|[synchronize_to_async](#synchronize_to_async)|将对 `array_view` 对象所做的任何修改异步同步到指定的[accelerator_view](accelerator-view-class.md)。|
|[view_as](#view_as)|使用此 `array_view` 对象的数据生成不同级别的 `array_view` 对象。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator()](#operator_call)|返回由参数指定的元素的值。|
|[operator\[\]](#operator_at)|返回由参数指定的元素。|
|[operator=](#operator_eq)|将指定 `array_view` 对象的内容复制到此对象中。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[rank 常量](#rank)|存储 `array_view` 对象的排名。|

### <a name="data-members"></a>数据成员

|名称|说明|
|----------|-----------------|
|[extent](#extent)|获取定义 `extent` 对象形状的 `array_view` 对象。|
|[source_accelerator_view](#source_accelerator_view)|获取 `array_view` 的数据源所在的[accelerator_view](accelerator-view-class.md)|
|[value_type](#value_type)|`array_view` 和绑定数组的值类型。|

## <a name="remarks"></a>备注

`array_view` 类表示数据中的一个视图，该视图包含在[数组](array-class.md)对象或 `array` 对象的子节中。

可以访问源数据所在的 `array_view` 对象（本地）或其他加速器或一致性域（远程）。 远程访问该对象时，将根据需要复制和缓存视图。 除了自动缓存的效果，`array_view` 对象的性能配置文件类似于 `array` 对象的性能配置文件。 通过视图访问数据时，性能会下降。

有三种远程使用方案：

- 系统内存指针的视图通过对加速器的[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)调用传递，并在快捷键上访问。

- 位于快捷键上的数组的视图通过对其他快捷键的 `parallel_for_each` 调用传递，并在其中进行访问。

- 在 CPU 上访问位于快捷键上的数组的视图。

在上述任何一种情况下，被引用的视图将由运行时复制到远程位置，并在被调用 `array_view` 对象修改后复制回本地位置。 运行时可能会优化将更改复制回的过程，可能只复制更改的元素，或者可能复制更改的部分。 不保证在一个数据源上重叠 `array_view` 对象在远程位置维护引用完整性。

您必须将任何多线程访问同步到相同的数据源。

运行时对 `array_view` 对象中的数据进行缓存做出以下保证：

- 按照程序顺序，对 `array` 对象和它上的 `array_view` 对象进行的所有同步访问都遵循在关系之前进行的一系列操作。

- 对单个 `array` 对象上同一加速器上的重叠 `array_view` 对象的所有完全同步访问都通过 `array` 对象化名为别名。 它们会引发 total 服从程序顺序。 没有缓存。 如果 `array_view` 对象在不同的快捷键上执行，则访问顺序是不确定的，这会造成争用情况。

使用系统内存中的指针创建 `array_view` 对象时，必须通过 `array_view` 指针仅更改 `array_view` 对象的视图。 或者，必须对附加到系统指针的某个 `array_view` 对象调用 `refresh()` （如果直接更改基础本机内存，而不是通过 `array_view` 对象）。

任一操作都会通知 `array_view` 对象基础本机内存已更改，并且位于加速器上的任何副本都已过时。 如果遵循这些准则，则基于指针的视图与为数据并行数组的视图提供的视图相同。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>要求

**标头：** amp.h

**命名空间：** 并发

## <a name="dtor"></a>~ array_view

销毁 `array_view` 的对象。

```cpp
~array_view()restrict(amp,cpu);
```

## <a name="ctor"></a>array_view

初始化 `array_view` 类的新实例。

```cpp
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view& _Other)restrict(amp,cpu);

explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    _Container& _Src) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    int _E0,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _Container& _Src);

explicit array_view(
    int _E0,
    _In_ value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    _In_ value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _In_ value_type* _Src)restrict(amp,cpu);

array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const _Container& _Src) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    const _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    int _E0,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    int _E2,
    const _Container& _Src);

array_view(
    int _E0,
    const value_type* _Src)restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    const value_type* _Src) restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    int _E2,
    const value_type* _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Arr_type*<br/>
提供数据的 C 样式数组的元素类型。

*_Container*<br/>
一个模板参数，必须指定支持 `data()` 和 `size()` 成员的线性容器。

*_E0*<br/>
本节范围内最重要的组件。

*_E1*<br/>
本节范围内的最重要的组件。

*_E2*<br/>
本节范围内最不重要的组件。

*_Extent*<br/>
此 `array_view`的每个维度中的范围。

*_Other*<br/>
一个类型为的对象，从该对象初始化新的 `array_view``array_view<T,N>`。

*_Size*<br/>
提供数据的 C 样式数组的大小。

*_Src*<br/>
指向将复制到新数组中的源数据的指针。

## <a name="copy_to"></a>copy_to

通过调用 `copy(*this, dest)`将 `array_view` 对象的内容复制到指定的目标对象。

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要复制到的对象。

## <a name="data"></a>数据

返回指向 `array_view`的原始数据的指针。

```cpp
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>返回值

指向 `array_view` 原始数据的指针。

## <a name="discard_data"></a>discard_data

丢弃此视图的当前数据。 这是运行时的优化提示，用于避免将视图的当前内容复制到访问目标 `accelerator_view` 目标，如果不需要现有内容，则建议使用此方法。 在 restrict （amp）上下文中使用时，此方法为无操作

```cpp
void discard_data() const restrict(cpu);
```

## <a name="extent"></a>范围

获取定义 `extent` 对象形状的 `array_view` 对象。

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_extent"></a>get_extent

返回 `array_view` 对象的[区](extent-class.md)对象。

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>返回值

`extent` 对象的  `array_view` 对象。

## <a name="get_ref"></a>get_ref

获取对 _Index 索引的元素的引用。 与用于访问 CPU 上的 array_view 的其他索引运算符不同，此方法不会将此 array_view 的内容隐式同步到 CPU。 访问远程位置上的 array_view 或执行涉及此 array_view 的复制操作后，用户将负责在调用此方法之前将 array_view 显式同步到 CPU。 否则，会导致未定义的行为。

```cpp
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引。

### <a name="return-value"></a>返回值

对索引的元素的引用 _Index

## <a name="get_source_accelerator_view"></a>get_source_accelerator_view

返回 array_view 的数据源所在的 accelerator_view。 如果 array_view 没有数据源，此 API 将引发 runtime_exception

```cpp
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>返回值

## <a name="operator_call"></a>operator （）

返回由参数指定的元素的值。

```cpp
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
元素的位置。

*_I0*<br/>
第一个维中的索引。

*_I1*<br/>
第二个维中的索引。

*_I2*<br/>
第三个维中的索引。

*_I*<br/>
元素的位置。

### <a name="return-value"></a>返回值

由参数指定的元素的值。

## <a name="operator_at"></a>运算符 []

返回由参数指定的元素。

```cpp
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引。

*_I*<br/>
索引。

### <a name="return-value"></a>返回值

索引处的元素的值，或投影到最高有效维度的 `array_view`。

## <a name="operator_eq"></a>operator =

将指定 `array_view` 对象的内容复制到此对象。

```cpp
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从中进行复制的 `array_view` 对象。

### <a name="return-value"></a>返回值

对此 `array_view` 对象的引用。

## <a name="rank"></a>级别

存储 `array_view` 对象的排名。

```cpp
static const int rank = _Rank;
```

## <a name="refresh"></a>刷新

通知 `array_view` 对象其绑定内存已在 `array_view` 接口外部进行了修改。 对此方法的调用将呈现过时的所有缓存信息。

```cpp
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a>reinterpret_as

通过一维 array_view 重新解释 array_view，作为选项的值类型可以与源 array_view 不同。

### <a name="syntax"></a>语法

```cpp
template <
    typename _Value_type2
>
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);

template <
    typename _Value_type2
>
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Value_type2*<br/>
新 `array_view` 对象的数据类型。

### <a name="return-value"></a>返回值

基于此 `array_view`的 `array_view` 对象或常量 `array_view` 对象，元素类型从 `T` 转换为 `_Value_type2`，而秩从*N*减为1。

### <a name="remarks"></a>备注

有时将多维数组视为线性、一维数组是一种很方便的方法，这种数组的值类型可能与源数组不同。 您可以使用此方法在 `array_view` 上实现此目的。

**警告**使用不同值类型 Reinterpreting array_view 对象是可能不安全的操作。 应谨慎使用此功能。

以下是一个示例：

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>区

返回 `array_view` 对象的子节，该对象位于指定的源并且可以选择具有指定的范围。

```cpp
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view section(
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

### <a name="return-value"></a>返回值

位于指定源的 `array_view` 对象的子节，还可以选择具有指定范围。 仅指定 `index` 对象时，子节包含关联区中的所有元素，这些元素的索引大于 `index` 对象中元素的索引。

## <a name="source_accelerator_view"></a>source_accelerator_view

获取与此 array_view 关联的源 accelerator_view。

```cpp
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

## <a name="synchronize"></a>同步

将对 `array_view` 对象所做的任何修改同步回其源数据。

```cpp
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>参数

*_Access_type*<br/>
目标[accelerator_view](accelerator-view-class.md)上的预期[access_type](concurrency-namespace-enums-amp.md#access_type) 。 此参数的默认值为 `access_type_read`。

## <a name="synchronize_async"></a>synchronize_async

将对 `array_view` 对象所做的任何修改异步同步回其源数据。

```cpp
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>参数

*_Access_type*<br/>
目标[accelerator_view](accelerator-view-class.md)上的预期[access_type](concurrency-namespace-enums-amp.md#access_type) 。 此参数的默认值为 `access_type_read`。

### <a name="return-value"></a>返回值

未来等待操作完成的时间。

## <a name="synchronize_to"></a>synchronize_to

将对此 array_view 所做的任何修改同步到指定的 accelerator_view。

```cpp
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>参数

*_Accl_view*<br/>
要同步到的目标 accelerator_view。

*_Access_type*<br/>
目标 accelerator_view 上的所需 access_type。 此参数的默认值为 access_type_read。

## <a name="synchronize_to_async"></a>synchronize_to_async

将对此 array_view 所做的任何修改异步同步到指定的 accelerator_view。

```cpp
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>参数

*_Accl_view*<br/>
要同步到的目标 accelerator_view。

*_Access_type*<br/>
目标 accelerator_view 上的所需 access_type。 此参数的默认值为 access_type_read。

### <a name="return-value"></a>返回值

未来等待操作完成的时间。

## <a name="value_type"></a>value_type

Array_view 和绑定数组的值类型。

```cpp
typedef typenamevalue_type value_type;
```

## <a name="view_as"></a>view_as

将此 `array_view` 为不同级别的 `array_view` 重新解释。

```cpp
template <
    int _New_rank
>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

template <
    int _New_rank
>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_New_rank*<br/>
新 `array_view` 对象的排名。

*_View_extent*<br/>
整形 `extent`。

*value_type*<br/>
原始[数组](array-class.md)对象和返回 `array_view` 对象中元素的数据类型。

### <a name="return-value"></a>返回值

构造的 `array_view` 对象。

## <a name="see-also"></a>另请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
