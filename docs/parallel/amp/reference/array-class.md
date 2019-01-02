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
ms.openlocfilehash: 93ef654bb71a342a6215ce5cd60786f36cadedf7
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657547"
---
# <a name="array-class"></a>array 类

表示用于将数据移动到加速器的数据容器。

## <a name="syntax"></a>语法

```
template <typename value_type, int _Rank>
friend class array;
```

#### <a name="parameters"></a>参数

*value_type*<br/>
数据元素类型。

*_Rank*<br/>
数组的秩。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[数组构造函数](#ctor)|初始化 `array` 类的新实例。|
|[~ array 析构函数](#dtor)|销毁`array`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[copy_to](#copy_to)|将数组的内容复制到另一个数组。|
|[data](#data)|返回指向数组的原始数据的指针。|
|[get_accelerator_view](#get_accelerator_view)|返回[accelerator_view](accelerator-view-class.md)对象，表示分配数组的位置。 可以仅在 CPU 上访问此属性。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。|
|[get_cpu_access_type](#get_cpu_access_type)|返回[access_type](concurrency-namespace-enums-amp.md#access_type)的数组。 可以仅在 CPU 上访问此方法。|
|[get_extent](#get_extent)|返回[程度](extent-class.md)数组的对象。|
|[reinterpret_as](#reinterpret_as)|返回包含中的所有元素的一维数组`array`对象。|
|[section](#section)|返回的一个子节`array`对象，它指定的原点上并且 （可选） 的具有指定的范围。|
|[view_as](#view_as)|返回[array_view](array-view-class.md)对象，它从构造`array`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator std::vector&lt;value_type&gt;](#operator_vec)|使用`copy(*this, vector)`隐式将数组转换为 std::[向量](../../../standard-library/vector-class.md)对象。|
|[operator()](#operator_call)|返回由参数指定的元素值。|
|[operator\[\]](#operator_at)|返回位于指定索引处的元素。|
|[operator=](#operator_eq)|将指定的内容复制`array`到此对象。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[rank 常量](#rank)|存储数组的秩。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|获取[accelerator_view](accelerator-view-class.md)对象，表示分配数组的位置。 可以仅在 CPU 上访问此属性。|
|[associated_accelerator_view](#associated_accelerator_view)|获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。|
|[cpu_access_type](#cpu_access_type)|获取[access_type](concurrency-namespace-enums-amp.md#access_type)表示 CPU 如何访问数组的存储。|
|[extent](#extent)|获取定义数组形状的范围。|

## <a name="remarks"></a>备注

类型`array<T,N>`表示密集型和常规 （不带锯齿的） *N*-维数组，它位于特定位置，例如快捷键或 CPU。 数组中元素的数据类型是`T`，它必须是与目标快捷键兼容的类型。 尽管秩`N`，(的数组以静态方式确定，并且是该类型的一部分，数组的范围由运行时确定，并且通过使用类来表示`extent<N>`。

数组有任意数量的维度，但某些功能专用于`array`具有级别为 1，2 和 3 的对象。 如果省略维度参数，则默认值为 1。

数组数据是连续排列在内存中。 不同的最低有效位维中的其中一个元素是在内存中相邻的。

数组是逻辑上被视为值类型，因为数组复制到另一个数组，会执行深层复制。 两个数组决不指向相同的数据。

`array<T,N>`在多种方案中使用类型：

- 作为可用在加速器上的计算中的数据容器。

- 作为用于保存主机 CPU 上的内存 （这可用于向 / 从其他数组复制） 的数据容器。

- 作为暂存对象来充当快速中介中主机到设备的复制。

## <a name="inheritance-hierarchy"></a>继承层次结构

`array`

## <a name="requirements"></a>要求

**标头：** amp.h

**Namespace:** 并发

##  <a name="dtor"></a> ~ 数组

销毁`array`对象。

```
~array() restrict(cpu);
```

##  <a name="accelerator_view"></a> accelerator_view

获取[accelerator_view](accelerator-view-class.md)对象，表示分配数组的位置。 可以仅在 CPU 上访问此属性。

```
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

##  <a name="ctor"></a> 数组

初始化的新实例[array 类](array-class.md)。 没有默认构造函数为`array<T,N>`。 所有构造函数只能在 CPU 上运行。 它们不能在 Direct3D 目标上执行。

```
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
指定数组首选的目标位置的 accelerator_view。

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md)对象，它指定数组的位置。

*_Cpu_access_type*<br/>
所需[access_type](concurrency-namespace-enums-amp.md#access_type)在 CPU 上数组。 此参数具有默认值为`access_type_auto`让 CPU`access_type`确定运行时。 实际 CPU`access_type`的数组可以使用查询`get_cpu_access_type`方法。

*_Extent*<br/>
数组的每个维度中的范围。

*_E0*<br/>
本部分的范围的最高有效组件。

*_E1*<br/>
本部分的范围的下一步-到-最高有效组件。

*_E2*<br/>
本部分的范围的最低有效组件。

*_InputIterator*<br/>
输入迭代器的类型。

*_Src*<br/>
若要要复制的对象。

*_Src_first*<br/>
进入源容器开始迭代器。

*_Src_last*<br/>
进入源容器结束迭代器。

*_Other*<br/>
其他数据源。

*_Rank*<br/>
区域的等级。

*value_type*<br/>
复制的元素数据类型。

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

将复制的内容`array`到另一个`array`。

```
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>参数

*_Dest*<br/>
[Array_view](array-view-class.md)要复制到对象。

##  <a name="cpu_access_type"></a> cpu_access_type

获取此数组允许的 CPU 访问类型。

```
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

##  <a name="data"></a> 数据

返回一个指针指向原始数据的`array`。

```
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>返回值

指向数组的原始数据的指针。

##  <a name="extent"></a> 范围

获取[程度](extent-class.md)对象，该定义的形状对象`array`。

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_accelerator_view"></a> get_accelerator_view

返回[accelerator_view](accelerator-view-class.md)对象表示的位置，其中`array`分配对象。 可以仅在 CPU 上访问此属性。

```
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>返回值

`accelerator_view`对象表示的位置，其中`array`分配对象。

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

获取第二个[accelerator_view](accelerator-view-class.md)暂存构造函数调用来实例化时作为参数传递的对象`array`对象。

```
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>返回值

第二个[accelerator_view](accelerator-view-class.md)对象传递给暂存构造函数。

##  <a name="get_cpu_access_type"></a> get_cpu_access_type

返回此数组允许的 CPU 访问类型。

```
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>返回值

##  <a name="get_extent"></a> get_extent

返回[程度](extent-class.md)对象的`array`。

```
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>返回值

`extent`对象的`array`。

##  <a name="operator_vec"></a> 运算符 std:: vector&lt;value_type&gt;

使用`copy(*this, vector)`将隐式转换为 std:: vector 对象的数组。

```
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>参数

*value_type*<br/>
向量的元素数据类型。

### <a name="return-value"></a>返回值

类型的对象`vector<T>`，其中包含数组中包含的数据的副本。

##  <a name="operator_call"></a> operator （)

返回由参数指定的元素值。

```
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
本节原点的最高有效组件。

*_I1*<br/>
本节原点的下一步-到-最高有效组件。

*_I2*<br/>
本节原点的最低有效组件。

*_I*<br/>
元素的位置。

### <a name="return-value"></a>返回值

由参数指定的元素值。

##  <a name="operator_at"></a> operator]

返回位于指定索引处的元素。

```
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

##  <a name="operator_eq"></a> 运算符 =

将指定的内容复制`array`对象。

```
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
`array`要从复制对象。

*_Src*<br/>
`array`要从复制对象。

### <a name="return-value"></a>返回值

对此引用`array`对象。

##  <a name="rank"></a> 排名

将存储的秩`array`。

```
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a> reinterpret_as

重新解释通过一维 array_view，其可能具有和值类型不同于源数组的数组。

### <a name="syntax"></a>语法

```
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Value_type2*<br/>
返回的数据的数据类型。

### <a name="return-value"></a>返回值

Array_view 或基于数组，与重新解释从 T 到 ElementType 和排名从 N 减少到 1 的元素类型的常量 array_view 对象。

### <a name="remarks"></a>备注

有时，可以方便地查看多维数组，如同它是线性、 一维数组，这可能可以使值类型不同于源数组。 可以使用此方法来实现此目的。
**警告：** 通过使用不同的值类型重复定义数组对象是一个潜在的不安全的操作。 我们建议谨慎使用此功能。

下面的代码提供了一个示例。

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> 部分

返回的一个子节`array`对象，它指定的原点上并且 （可选） 的具有指定的范围。

```
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
本部分的范围的最高有效组件。

*_E1*<br/>
本部分的范围的下一步-到-最高有效组件。

*_E2*<br/>
本部分的范围的最低有效组件。

*_Ext*<br/>
[程度](extent-class.md)指定区域范围的对象。 原始是 0。

*上 _Idx*<br/>
[索引](index-class.md)对象，它指定原点的位置。 子节是范围的其余部分。

*_I0*<br/>
本节原点的最高有效组件。

*_I1*<br/>
本节原点的下一步-到-最高有效组件。

*_I2*<br/>
本节原点的最低有效组件。

*_Rank*<br/>
区域的等级。

*_Section_extent*<br/>
[程度](extent-class.md)指定区域范围的对象。

*_Section_origin*<br/>
[索引](index-class.md)对象，它指定原点的位置。

*value_type*<br/>
复制的元素数据类型。

### <a name="return-value"></a>返回值

返回的一个子节`array`对象，它指定的原点上并且 （可选） 的具有指定的范围。 当仅`index`指定对象时，小节包含关联网格中的所有元素的索引中的元素的索引大于`index`对象。

##  <a name="view_as"></a> view_as

重新解释为此数组[array_view](array-view-class.md)一个不同的级别。

```
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_New_rank*<br/>
秩`extent`对象作为参数传递。

*_View_extent*<br/>
用于构造新的范围[array_view](array-view-class.md)对象。

*value_type*<br/>
在这两个原始元素的数据类型`array`对象和返回`array_view`对象。

### <a name="return-value"></a>返回值

[Array_view](array-view-class.md)构造对象。

## <a name="see-also"></a>请参阅

[并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)
