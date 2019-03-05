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
ms.openlocfilehash: 0f2b627afa216f03592fe913afece1a80f5bd5a6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275657"
---
# <a name="textureview-class"></a>texture_view 类

提供了读取访问权限和写入访问权限给纹理。 `texture_view` 仅可用于读取值类型是的纹理`int`， `unsigned int`，或`float`具有默认 32 位 bpse 的纹理。 若要了解其他纹理格式，使用`texture_view<const value_type, _Rank>`。

## <a name="syntax"></a>语法

```
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

#### <a name="parameters"></a>参数

*value_type*<br/>
纹理聚合中元素的类型。

*_Rank*<br/>
秩`texture_view`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`value_type`|纹理聚合中元素的类型。|
|`coordinates_type`|用于指定中的纹理的坐标的类型`texture_view`— 即`short_vector`具有相同的排名为具有值类型的关联纹理`float`。|
|`gather_return_type`|返回类型用于收集操作-即，级别 4`short_vector`包含四个相同颜色组件收集从四个采样的纹理值。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[texture_view 构造函数](#ctor)|已重载。 构造`texture_view`实例。|
|[~ texture_view 析构函数](#ctor)|销毁`texture_view`实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|已重载。 通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的 alpha (w) 组件。|
|[gather_blue](#gather_blue)|已重载。 通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的蓝色 (z) 组件。|
|[gather_green](#gather_green)|已重载。 通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的绿色 (y) 组件。|
|[gather_red](#gather_red)|已重载。 通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的红色 (x) 组件。|
|[get](#get)|已重载。 按索引获取此元素的值。|
|[sample](#sample)|已重载。 通过使用特定的采样配置采样指定的坐标和详细级别的纹理。|
|[set](#set)|按索引设置元素的值。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator()](#operator_call)|已重载。 按索引获取此元素的值。|
|[operator\[\]](#operator_at)|已重载。 按索引获取此元素的值。|
|[operator=](#operator_eq)|已重载。 赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[value_type](#value_type)|元素的值类型`texture_view`。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Texture_base`

`texture_view`

## <a name="requirements"></a>要求

**标头：** amp_graphics.h

**Namespace:** concurrency:: graphics

##  <a name="dtor"></a> ~texture_view

销毁`texture_view`实例。

```
~texture_view() restrict(amp, cpu);
```

##  <a name="ctor"></a> texture_view

构造`texture_view`实例。

```
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
[1，2]构造函数`texture`在其上的可写`texture_view`创建。

[3，4]构造函数`texture`的不可写`texture_view`创建。

*_Other*<br/>
[5] 复制构造函数可写的源`texture_view`。

[6，7] 之内复制构造函数的非可写的源`texture_view`。

*_Mipmap_level*<br/>
在源上的特定 mipmap`texture`此可写的`texture_view`将绑定到。 默认值为 0，它表示最高级别 （最详细） mip 级别。

*_Most_detailed_mip*<br/>
排名靠前的视图，相对于指定的级别 （最详细） mip 级别`texture_view`对象。

*_Mip_levels*<br/>
可通过访问 mipmap 级别数`texture_view`。

##  <a name="gather_red"></a> gather_red

通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的红色 (x) 组件。

```
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
要使用的地址模式示例`texture_view`。 寻址模式是为所有维度相同的。

*_Sampler*<br/>
若要使用的采样器配置到示例`texture_view`。

*_Coord*<br/>
要采用示例的坐标。 部分坐标值用于内插在示例纹理之间。

### <a name="return-value"></a>返回值

级别 4 短矢量包含的红色 (x) 部分的 4 个采样纹理值。

##  <a name="gather_green"></a> gather_green

通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的绿色 (y) 组件。

```
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
要使用的地址模式示例`texture_view`。 寻址模式是为所有维度相同的。

*_Sampler*<br/>
若要使用的采样器配置到示例`texture_view`。

*_Coord*<br/>
要采用示例的坐标。 部分坐标值用于内插在示例纹理之间。

### <a name="return-value"></a>返回值

级别 4 短矢量包含的绿色 (y) 部分的 4 个采样纹理值。

##  <a name="gather_blue"></a> gather_blue

通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的蓝色 (z) 组件。

```
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
要使用的地址模式示例`texture_view`。 寻址模式是为所有维度相同的。

*_Sampler*<br/>
若要使用的采样器配置到示例`texture_view`。

*_Coord*<br/>
要采用示例的坐标。 部分坐标值用于内插在示例纹理之间。

### <a name="return-value"></a>返回值

级别 4 短矢量包含的红色 (x) 部分的 4 个采样纹理值。

##  <a name="gather_alpha"></a> gather_alpha

通过使用特定的采样配置采样指定坐标处的纹理，并返回四个采样纹理的 alpha (w) 组件。

```
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
要使用的地址模式示例`texture_view`。 寻址模式是为所有维度相同的。

*_Sampler*<br/>
若要使用的采样器配置到示例`texture_view`。

*_Coord*<br/>
要采用示例的坐标。 部分坐标值用于内插在示例纹理之间。

### <a name="return-value"></a>返回值

级别 4 短矢量包含的 alpha (w) 组件的 4 个采样纹理值。

##  <a name="get"></a> 获取

获取指定索引处的元素的值。

```
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
若要获取，可能是多维的元素的索引。

*_Mip_level*<br/>
我们应从其获取值的 mipmap 级别。 默认值 0 表示最详细的 mipmap 级别。

### <a name="return-value"></a>返回值

元素的值。

##  <a name="operator_eq"></a> 运算符 =

将分配同一纹理与指定的视图`texture_view`到此`texture_view`实例。

```
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
[1，2]复制构造函数的可写`texture_view`对象。

[3] 复制构造函数的非可写`texture_view`对象。

### <a name="return-value"></a>返回值

对此引用`texture_view`实例。

##  <a name="operator_at"></a> operator[]

按索引返回元素值。

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
索引，可能是多维。

*_I0*<br/>
一维索引。

### <a name="return-value"></a>返回值

按索引元素值`_Index`。

##  <a name="operator_call"></a> operator()

按索引返回元素值。

```
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
索引，可能是多维。

*_I0*<br/>
索引的最高有效组件。

*_I1*<br/>
索引的下一步-到-最高有效组件。

*_I2*<br/>
索引的最低有效组件。

### <a name="return-value"></a>返回值

按索引元素值`_Index`。

##  <a name="sample"></a> 示例

通过使用特定的采样配置采样指定的坐标和详细级别的纹理。

```
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
要用于 texture_view 取样的筛选器模式。 筛选器模式下是相同的最小化、 最大化和 mipmap 筛选器。

*_Address_mode*<br/>
要用于取样 texture_view 的寻址模式。 寻址模式是为所有维度相同的。

*_Sampler*<br/>
要用于采样 texture_view 的采样器配置。

*_Coord*<br/>
要采用示例的坐标。 部分坐标值用于内插在纹素值之间。

*_Level_of_detail*<br/>
该值指定要从示例的 mipmap 级别。 小数部分值用于内插在两个 mipmap 级别之间。 详细信息的默认级别为 0，它表示最详细的 mip 级别。

### <a name="return-value"></a>返回值

内插的示例值。

##  <a name="set"></a> 设置

设置为指定的值的指定索引处的元素的值。

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
若要设置，可能是多维的元素的索引。

*值*<br/>
要将元素设置的值。

##  <a name="value_type"></a> value_type

纹理视图的元素的值类型。

```
typedef typename const value_type value_type;
```

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
