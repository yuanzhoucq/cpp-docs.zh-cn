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
ms.openlocfilehash: b8a37293166ec21aeb9410f05fb70c9753ec4f22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230410"
---
# <a name="texture-class"></a>texture 类

纹理是在范围域中的上的数据聚合 `accelerator_view` 。 它是变量集合，每个元素对应于一个范围域中的一个元素。 每个变量都保留与 c + + 基元类型（ **`unsigned int`** 、 **`int`** 、 **`float`** 、 **`double`** ）、标量类型（ `norm` 、或 `unorm` ）或短向量类型相对应的值。

## <a name="syntax"></a>语法

```cpp
template <typename value_type,  int _Rank>
class texture;
```

### <a name="parameters"></a>参数

*value_type*<br/>
纹理中元素的类型。

*_Rank*<br/>
纹理的排名。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`scalar_type`|标量类型。|
|`value_type`|值类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[纹理构造函数](#ctor)|初始化 `texture` 类的新实例。|
|[~ 纹理析构函数](#ctor)|销毁 `texture` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[copy_to](#copy_to)|`texture`通过执行深层复制，将对象复制到目标。|
|[data](#data)|返回一个 CPU 指针，该指针指向此纹理的原始数据。|
|[get](#get)|返回指定索引处的元素的值。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|返回作为要将此纹理复制到的首选目标的[accelerator_view](accelerator-view-class.md) 。|
|[get_depth_pitch](#get_depth_pitch)|返回 CPU 上3D 暂存纹理中每个深度切片之间的字节数。|
|[get_row_pitch](#get_row_pitch)|返回 CPU 上2D 或3D 暂存纹理中每行之间的字节数。|
|[set](#set)|设置指定索引处的元素的值。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[operator （）](#operator_call)|返回由参数指定的元素值。|
|[操作员\[\]](#operator_at)|返回指定索引处的元素。|
|[operator =](#operator_eq)|将指定的[纹理](texture-class.md)对象复制到此对象。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[rank 常量](#rank)|获取对象的秩 `texture` 。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|获取要将此纹理复制到的首选目标的[accelerator_view](accelerator-view-class.md) 。|
|[depth_pitch](#depth_pitch)|获取 CPU 上3D 暂存纹理中每个深度切片之间的字节数。|
|[row_pitch](#row_pitch)|获取 CPU 上2D 或3D 过渡纹理中每行之间的字节数。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Texture_base`

`texture`

## <a name="requirements"></a>要求

**标头：** amp_graphics。h

**命名空间：** Concurrency：： graphics

## <a name="texture"></a><a name="dtor"></a>~ 纹理

销毁 `texture` 对象。

```cpp
~texture() restrict(cpu);
```

## <a name="associated_accelerator_view"></a><a name="associated_accelerator_view"></a>associated_accelerator_view

获取要将此纹理复制到的首选目标的[accelerator_view](accelerator-view-class.md) 。

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a><a name="copy_to"></a>copy_to

`texture`通过执行深层复制，将对象复制到目标。

```cpp
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>参数

*_Dest*<br/>
要复制到的对象。

*_Rank*<br/>
纹理的排名。

*value_type*<br/>
纹理中元素的类型。

## <a name="data"></a><a name="data"></a> 数据

返回一个 CPU 指针，该指针指向此纹理的原始数据。

```cpp
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>返回值

指向纹理的原始数据的指针。

## <a name="depth_pitch"></a><a name="depth_pitch"></a>depth_pitch

获取 CPU 上3D 暂存纹理中每个深度切片之间的字节数。

```cpp
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

## <a name="get"></a><a name="get"></a>获取

返回指定索引处的元素的值。

```cpp
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
元素的索引。

### <a name="return-value"></a>返回值

位于指定索引处的元素的值。

## <a name="get_associated_accelerator_view"></a><a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

返回作为要将此纹理复制到的首选目标的 accelerator_view。

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>返回值

作为此纹理要复制到的首选目标的[accelerator_view](accelerator-view-class.md) 。

## <a name="get_depth_pitch"></a><a name="get_depth_pitch"></a>get_depth_pitch

返回 CPU 上3D 暂存纹理中每个深度切片之间的字节数。

```cpp
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>返回值

CPU 上3D 暂存纹理中每个深度切片之间的字节数。

## <a name="get_row_pitch"></a><a name="get_row_pitch"></a>get_row_pitch

返回二维暂存纹理中每行之间或三维过渡纹理中深度切片的每一行之间的字节数。

```cpp
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>返回值

二维暂存纹理中每行之间或三维过渡纹理中深度切片的每一行之间的字节数。

## <a name="operator"></a><a name="operator_call"></a>operator （）

返回由参数指定的元素值。

```cpp
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
索引的最重要的组件。

*_I1*<br/>
索引的最高有效组件。

*_I2*<br/>
索引的最小有效组件。

*_Rank*<br/>
索引的排名。

### <a name="return-value"></a>返回值

由参数指定的元素值。

## <a name="operator"></a><a name="operator_at"></a>运算符 []

返回指定索引处的元素。

```cpp
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

## <a name="operator"></a><a name="operator_eq"></a>operator =

将指定的[纹理](texture-class.md)对象复制到此对象。

```cpp
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>参数

*_Other*<br/>
`texture`要从中进行复制的对象。

### <a name="return-value"></a>返回值

对此对象的引用 `texture` 。

## <a name="rank"></a><a name="rank"></a>级别

获取对象的秩 `texture` 。

```cpp
static const int rank = _Rank;
```

## <a name="row_pitch"></a><a name="row_pitch"></a>row_pitch

获取 CPU 上2D 或3D 过渡纹理中每行之间的字节数。

```cpp
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

## <a name="set"></a><a name="set"></a>字符集

设置指定索引处的元素的值。

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
元素的索引。

*_Rank*<br/>
索引的排名。

*value*<br/>
该元素的新值。

## <a name="texture"></a><a name="ctor"></a>褐色

初始化 `texture` 类的新实例。

```cpp
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
指定纹理位置的[accelerator_view](accelerator-view-class.md) 。

*_Av*<br/>
指定纹理位置的[accelerator_view](accelerator-view-class.md) 。

*_Associated_av*<br/>
一个 accelerator_view，指定此纹理的副本的首选目标。

*_Bits_per_scalar_element*<br/>
纹理的基础标量类型中每个标量元素的位数。 通常，支持的值为8、16、32和64。 如果指定0，则位数与基础 scalar_type 相同。 64仅对基于双重的纹理有效。

*_Ext*<br/>
纹理的每个维度中的范围。

*_E0*<br/>
纹理的最重要的组件。

*_E1*<br/>
纹理的最高有效组件。

*_E2*<br/>
纹理范围内最不重要的组件。

*_Input_iterator*<br/>
输入迭代器的类型。

*_Mipmap_levels*<br/>
基础纹理中的 mipmap 级别数。 如果指定0，纹理的 mipmap 级别将会下降到指定范围内可能的最小大小。

*_Rank*<br/>
范围的秩。

*_Source*<br/>
指向主机缓冲区的指针。

*_Src*<br/>
要复制的纹理。

*_Src_byte_size*<br/>
源缓冲区中的字节数。

*_Src_first*<br/>
源容器中的开始迭代器。

*_Src_last*<br/>
源容器中的结束迭代器。

*_Other*<br/>
其他数据源。

*_Rank*<br/>
部分的秩。

## <a name="see-also"></a>另请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
