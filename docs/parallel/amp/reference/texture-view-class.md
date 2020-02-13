---
title: texture_view 类
ms.date: 11/04/2016
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: 6bf4b9666d746199cea92fa2bd52b691c67e4a5b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126340"
---
# <a name="texture_view-class"></a>texture_view 类

提供对纹理的读访问和写访问权限。 `texture_view` 仅可用于读取其值类型为 `int`、`unsigned int`或 `float` 具有默认32位 bpse 的纹理。 若要读取其他纹理格式，请使用 `texture_view<const value_type, _Rank>`。

## <a name="syntax"></a>语法

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>参数

*value_type*<br/>
纹理聚合中元素的类型。

*_Rank*<br/>
`texture_view`的排名。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`value_type`|纹理聚合中元素的类型。|
|`coordinates_type`|用于指定 `texture_view`中的纹素的坐标类型，即与具有值类型 `float`的关联纹理具有相同级别的 `short_vector`。|
|`gather_return_type`|用于收集操作的返回类型-即，一个排名为4的 `short_vector`，其中包含从采样的四个纹素值中收集的四个同源颜色组件。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[texture_view 构造函数](#ctor)|已重载。 构造一个 `texture_view` 实例。|
|[~ texture_view 析构函数](#ctor)|销毁 `texture_view` 实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|已重载。 使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素中的 alpha （w）分量。|
|[gather_blue](#gather_blue)|已重载。 使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素的蓝色（z）分量。|
|[gather_green](#gather_green)|已重载。 使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素的绿色（y）分量。|
|[gather_red](#gather_red)|已重载。 使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素的红色（x）分量。|
|[get](#get)|已重载。 按索引获取元素值。|
|[sample](#sample)|已重载。 使用指定的采样配置，在指定的坐标和详细程度上采集纹理。|
|[set](#set)|按索引设置元素的值。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator()](#operator_call)|已重载。 按索引获取元素值。|
|[operator\[\]](#operator_at)|已重载。 按索引获取元素值。|
|[operator=](#operator_eq)|已重载。 赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[value_type](#value_type)|`texture_view`的元素的值类型。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Texture_base`

`texture_view`

## <a name="requirements"></a>要求

**标头：** amp_graphics。h

**命名空间：** concurrency：： graphics

## <a name="dtor"></a>~ texture_view

销毁 `texture_view` 实例。

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="ctor"></a>texture_view

构造一个 `texture_view` 实例。

```cpp
texture_view(// [1] constructor
    texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [2] constructor
    texture<value_type, _Rank>& _Src,
    unsigned int _Mipmap_level = 0) restrict(cpu);

texture_view(// [3] constructor
    const texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [4] constructor
    const texture<value_type, _Rank>& _Src,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);

texture_view(// [5] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [6] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [7] copy constructor
    const texture_view<const value_type, _Rank>& _Other,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);
```

### <a name="parameters"></a>参数

*_Src*<br/>
[1，2]构造函数，创建可写 `texture_view` 的 `texture`。

[3，4]构造函数，将在其上创建不可写 `texture_view` `texture`。

*_Other*<br/>
[5] 复制构造函数源可写 `texture_view`。

[6，7]复制构造函数源不可写入 `texture_view`。

*_Mipmap_level*<br/>
此可写 `texture_view` 绑定到的源 `texture` 上的特定 mipmap 级别。 默认值为0，表示顶级（最详细） mip 级别。

*_Most_detailed_mip*<br/>
视图的顶级（最详细） mip 级别，相对于指定的 `texture_view` 对象。

*_Mip_levels*<br/>
可通过 `texture_view`访问的 mipmap 级别数。

## <a name="gather_red"></a>gather_red

使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素的红色（x）分量。

```cpp
const gather_return_type gather_red(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Address_mode*<br/>
用于采样 `texture_view`的地址模式。 所有维度的地址模式均相同。

*_Sampler*<br/>
用于对 `texture_view`进行采样的采样器配置。

*_Coord*<br/>
从中获取示例的坐标。 小数坐标值用于在样本纹素之间进行插入。

### <a name="return-value"></a>返回值

包含4个采样纹素值的红色（x）分量的排名4的小矢量。

## <a name="gather_green"></a>gather_green

使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素的绿色（y）分量。

```cpp
const gather_return_type gather_green(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Address_mode*<br/>
用于采样 `texture_view`的地址模式。 所有维度的地址模式均相同。

*_Sampler*<br/>
用于对 `texture_view`进行采样的采样器配置。

*_Coord*<br/>
从中获取示例的坐标。 小数坐标值用于在样本纹素之间进行插入。

### <a name="return-value"></a>返回值

包含4个采样纹素值的绿色（y）分量的排名4短矢量。

## <a name="gather_blue"></a>gather_blue

使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素的蓝色（z）分量。

```cpp
const gather_return_type gather_blue(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Address_mode*<br/>
用于采样 `texture_view`的地址模式。 所有维度的地址模式均相同。

*_Sampler*<br/>
用于对 `texture_view`进行采样的采样器配置。

*_Coord*<br/>
从中获取示例的坐标。 小数坐标值用于在样本纹素之间进行插入。

### <a name="return-value"></a>返回值

包含4个采样纹素值的红色（x）分量的排名4的小矢量。

## <a name="gather_alpha"></a>gather_alpha

使用指定的采样配置对指定坐标处的纹理取样，并返回四个采样纹素中的 alpha （w）分量。

```cpp
const gather_return_type gather_alpha(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Address_mode*<br/>
用于采样 `texture_view`的地址模式。 所有维度的地址模式均相同。

*_Sampler*<br/>
用于对 `texture_view`进行采样的采样器配置。

*_Coord*<br/>
从中获取示例的坐标。 小数坐标值用于在样本纹素之间进行插入。

### <a name="return-value"></a>返回值

包含4个采样纹素值的 alpha （w）分量的排名4短矢量。

## <a name="get"></a>获取

获取指定索引处的元素的值。

```cpp
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
要获取的元素的索引，可能是多维的。

*_Mip_level*<br/>
要从其获取值的 mipmap 级别。 默认值0表示最详细的 mipmap 级别。

### <a name="return-value"></a>返回值

元素的值。

## <a name="operator_eq"></a>operator =

将与指定 `texture_view` 相同纹理的视图分配给此 `texture_view` 实例。

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
[1，2]复制构造函数可写的 `texture_view` 对象。

[3] 复制构造函数一个不可写的 `texture_view` 对象。

### <a name="return-value"></a>返回值

对此 `texture_view` 实例的引用。

## <a name="operator_at"></a>运算符 []

按索引返回元素值。

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引，可能是多维的。

*_I0*<br/>
一维索引。

### <a name="return-value"></a>返回值

`_Index`索引的元素值。

## <a name="operator_call"></a>operator （）

按索引返回元素值。

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);

value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

value_type operator() (
    int _I0) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引，可能是多维的。

*_I0*<br/>
索引的最重要的组件。

*_I1*<br/>
索引的最高有效组件。

*_I2*<br/>
索引的最小有效组件。

### <a name="return-value"></a>返回值

`_Index`索引的元素值。

## <a name="sample"></a>范例

使用指定的采样配置，在指定的坐标和详细程度上采集纹理。

```cpp
value_type sample(
    const sampler& _Sampler,
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);

template<
    filter_mode _Filter_mode = filter_linear,
    address_mode _Address_mode = address_clamp
>
value_type sample(
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Filter_mode*<br/>
用于采样 texture_view 的筛选器模式。 对于 "最小化"、"最大化" 和 "mipmap" 筛选器，筛选模式是相同的。

*_Address_mode*<br/>
用于采样 texture_view 的地址模式。 所有维度的地址模式均相同。

*_Sampler*<br/>
用于对 texture_view 进行采样的采样器配置。

*_Coord*<br/>
从中获取示例的坐标。 小数坐标值用于在纹素值之间进行内插。

*_Level_of_detail*<br/>
值指定要从中采样的 mipmap 级别。 小数值用于在两个 mipmap 级别之间进行内插。 默认详细信息级别为0，表示最详细的 mip 级别。

### <a name="return-value"></a>返回值

内插示例值。

## <a name="set"></a>字符集

将指定索引处的元素的值设置为指定值。

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
要设置的元素的索引，可能是多维的。

*value*<br/>
要将元素设置到的值。

## <a name="value_type"></a>value_type

Texture_view 的元素的值类型。

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>另请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
