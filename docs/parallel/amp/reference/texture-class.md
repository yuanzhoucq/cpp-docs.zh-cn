---
title: texture 类
ms.date: 11/04/2016
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: cfcb65fa23fe4593e7dcf11da3b5da4b1785ce71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351529"
---
# <a name="texture-class"></a>texture 类

纹理是上的数据聚合`accelerator_view`在范围域中。 它是变量，一个用于在范围域中的每个元素的集合。 每个变量包含一个值，对应于C++基元类型 ( `unsigned int`， `int`， `float`， `double`)、 标量类型 ( `norm`，或者`unorm`)，或短矢量类型。

## <a name="syntax"></a>语法

```
template <typename value_type,  int _Rank>
class texture;
```

#### <a name="parameters"></a>参数

*value_type*<br/>
纹理中元素的类型。

*_Rank*<br/>
纹理的等级。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`scalar_type`|标量类型。|
|`value_type`|值类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[纹理构造函数](#ctor)|初始化 `texture` 类的新实例。|
|[~ texture 析构函数](#ctor)|销毁`texture`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[copy_to](#copy_to)|副本`texture`对象到目标，通过执行深层复制。|
|[data](#data)|返回 CPU 指针到该纹理的原始数据。|
|[get](#get)|返回指定索引处的元素的值。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|返回[accelerator_view](accelerator-view-class.md)该纹理要复制到的首选的目标。|
|[get_depth_pitch](#get_depth_pitch)|返回在 3D 暂存纹理在 CPU 上的每个深度切片之间的字节数。|
|[get_row_pitch](#get_row_pitch)|返回在 2D 或 CPU 上 3D 暂存纹理中每行之间的字节数。|
|[set](#set)|设置指定索引处的元素的值。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator()](#operator_call)|返回由参数指定的元素值。|
|[operator\[\]](#operator_at)|返回位于指定索引处的元素。|
|[operator=](#operator_eq)|复制指定[纹理](texture-class.md)到此对象。|

### <a name="public-constants"></a>公共常量

|名称|描述|
|----------|-----------------|
|[rank 常量](#rank)|获取的排名`texture`对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|获取[accelerator_view](accelerator-view-class.md)该纹理要复制到的首选的目标。|
|[depth_pitch](#depth_pitch)|获取在 CPU 上 3D 暂存纹理中每个深度切片之间的字节数。|
|[row_pitch](#row_pitch)|获取 2D 或 3D 中每行之间的字节数的临时在 CPU 上的纹理。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Texture_base`

`texture`

## <a name="requirements"></a>要求

**标头：** amp_graphics.h

**命名空间：** Concurrency:: graphics

##  <a name="dtor"></a> ~texture

销毁`texture`对象。

```
~texture() restrict(cpu);
```

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

获取[accelerator_view](accelerator-view-class.md)该纹理要复制到的首选的目标。

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

副本`texture`对象到目标，通过执行深层复制。

```
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要将复制到的对象。

*_Rank*<br/>
纹理的等级。

*value_type*<br/>
纹理中元素的类型。

##  <a name="data"></a> data

返回 CPU 指针到该纹理的原始数据。

```
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>返回值

指向纹理的原始数据的指针。

##  <a name="depth_pitch"></a> depth_pitch

获取在 CPU 上 3D 暂存纹理中每个深度切片之间的字节数。

```
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

##  <a name="get"></a> 获取

返回指定索引处的元素的值。

```
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
元素的索引。

### <a name="return-value"></a>返回值

位于指定索引处的元素的值。

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

返回该纹理要复制到目标的 accelerator_view。

```
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>返回值

[Accelerator_view](accelerator-view-class.md)该纹理要复制到的首选的目标。

##  <a name="get_depth_pitch"></a> get_depth_pitch

返回在 3D 暂存纹理在 CPU 上的每个深度切片之间的字节数。

```
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>返回值

在 3D 暂存纹理在 CPU 上的每个深度切片之间的字节数。

##  <a name="get_row_pitch"></a> get_row_pitch

二维暂存纹理中每行之间或三维暂存纹理中深度切片每行之间，则返回字节的数。

```
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>返回值

二维暂存纹理中每行之间或三维暂存纹理中深度切片每行之间的字节数。

##  <a name="operator_call"></a> operator()

返回由参数指定的元素值。

```
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引。

*_I0*<br/>
索引的最高有效组件。

*_I1*<br/>
索引的下一步-到-最高有效组件。

*_I2*<br/>
索引的最低有效组件。

*_Rank*<br/>
索引的秩。

### <a name="return-value"></a>返回值

由参数指定的元素值。

##  <a name="operator_at"></a> operator[]

返回位于指定索引处的元素。

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引。

*_I0*<br/>
索引。

### <a name="return-value"></a>返回值

位于指定索引处的元素。

##  <a name="operator_eq"></a> 运算符 =

复制指定[纹理](texture-class.md)到此对象。

```
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>参数

*_Other*<br/>
`texture`要从复制对象。

### <a name="return-value"></a>返回值

对此引用`texture`对象。

##  <a name="rank"></a> 排名

获取的排名`texture`对象。

```
static const int rank = _Rank;
```

##  <a name="row_pitch"></a> row_pitch

获取 2D 或 3D 中每行之间的字节数的临时在 CPU 上的纹理。

```
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

##  <a name="set"></a> 设置

设置指定索引处的元素的值。

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
元素的索引。

*_Rank*<br/>
索引的秩。

*值*<br/>
该元素的新值。

##  <a name="ctor"></a> 纹理

初始化 `texture` 类的新实例。

```
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

texture(int _E0) restrict(cpu);

texture(int _E0, int _E1) restrict(cpu);

texture(int _E0, int _E1, int _E2) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const texture& _Src,
    const Concurrency::accelerator_view& _Acc_view);

texture(
    texture&& _Other);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av);

texture(
    const texture& _Src);
```

### <a name="parameters"></a>参数

*_Acc_view*<br/>
[Accelerator_view](accelerator-view-class.md)指定纹理位置。

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md)指定纹理位置。

*_Associated_av*<br/>
指定的首选的目标的 accelerator_view 复制到或从该纹理。

*_Bits_per_scalar_element*<br/>
每个基础标量类型的纹理中每个标量元素位数。 一般情况下，受支持的值是 8、 16、 32 和 64。 如果指定 0，则比特数是与基础 scalar_type 相同。 64 时才有效双纹理。

*_Ext*<br/>
纹理每个维度中的范围。

*_E0*<br/>
纹理的最高有效组件。

*_E1*<br/>
下一步-到-最高有效组件的纹理。

*_E2*<br/>
纹理的范围的最低有效组件。

*_Input_iterator*<br/>
输入迭代器的类型。

*_Mipmap_levels*<br/>
在基础纹理 mipmap 级别数。 如果指定 0，纹理将具有指定范围的可能的最小大小下的 mipmap 级别的完整范围。

*_Rank*<br/>
范围的等级。

*_Source*<br/>
指向主缓冲区的指针。

*_Src*<br/>
为要复制的纹理。

*_Src_byte_size*<br/>
源缓冲区中的字节数。

*_Src_first*<br/>
进入源容器开始迭代器。

*_Src_last*<br/>
进入源容器结束迭代器。

*_Other*<br/>
其他数据源。

*_Rank*<br/>
区域的等级。

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
