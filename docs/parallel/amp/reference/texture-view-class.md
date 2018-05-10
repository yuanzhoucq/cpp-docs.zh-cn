---
title: texture_view 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3db02d9cafb87c0f173546687ad01390e09b9f68
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="textureview-class"></a>texture_view 类
提供为纹理的写访问权限和读取访问权限。 `texture_view` 仅用于读取其值类型的纹理`int`， `unsigned int`，或`float`具有默认值 32 位 bpse。 若要读取其他纹理格式，使用`texture_view<const value_type, _Rank>`。  
  
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
 `value_type`  
 纹理聚合中的元素的类型。  
  
 `_Rank`  
 秩`texture_view`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`value_type`|纹理聚合中的元素的类型。|  
|`coordinates_type`|一种用于指定在纹素的坐标`texture_view`— 即`short_vector`，具有相同的排名为所具有的值类型的关联纹理`float`。|  
|`gather_return_type`|返回类型，用于收集操作-即，级别 4`short_vector`包含四个同构颜色组件收集从采样的四个纹素值。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[texture_view 构造函数](#ctor)|已重载。 构造`texture_view`实例。|  
|[~ texture_view 析构函数](#ctor)|销毁`texture_view`实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[gather_alpha](#gather_alpha)|已重载。 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的字母 (w) 组件。|  
|[gather_blue](#gather_blue)|已重载。 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的蓝色 (z) 组件。|  
|[gather_green](#gather_green)|已重载。 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的绿色 (y) 组件。|  
|[gather_red](#gather_red)|已重载。 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的红色 (x) 组件。|  
|[get](#get)|已重载。 按索引获取此元素的值。|  
|[示例](#sample)|已重载。 使用指定的采样配置示例在指定的坐标和的详细信息级别的纹理。|  
|[set](#set)|按索引设置元素的值。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator()](#operator_call)|已重载。 按索引获取此元素的值。|  
|[operator[]](#operator_at)|已重载。 按索引获取此元素的值。|  
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
  
##  <a name="dtor"></a> ~ texture_view 

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
 `_Src`  
 [1，2]构造函数  
 `texture`在其上可写`texture_view`创建。  
  
 [3，4]构造函数  
 `texture`在其上不可写入`texture_view`创建。  
  
 `_Other`  
 [5] 复制构造函数  
 可写的源`texture_view`。  
  
 [6，7]复制构造函数  
 非可写的源`texture_view`。  
  
 `_Mipmap_level`  
 源上的特定 mipmap 级别`texture`此可写`texture_view`将绑定到。 默认值为 0，它表示顶级 （最详细） mip 级别。  
  
 `_Most_detailed_mip`  
 排名靠前的视图中，相对于指定的级别 （最详细） mip 级别`texture_view`对象。  
  
 `_Mip_levels`  
 可通过访问 mipmap 级别数`texture_view`。  
  
##  <a name="gather_red"></a> gather_red 

 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的红色 (x) 组件。  
  
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
 `_Address_mode`  
 要使用的地址模式示例`texture_view`。 对于所有维度相同的寻址模式。  
  
 `_Sampler`  
 要使用的采样器配置示例`texture_view`。  
  
 `_Coord`  
 要采用从示例的坐标。 小数部分组成的坐标值用于之间示例纹素插值。  
  
### <a name="return-value"></a>返回值  
 级别 4 短矢量包含 4 的红色 (x) 部分采样纹素值。  
  
##  <a name="gather_green"></a> gather_green 

 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的绿色 (y) 组件。  
  
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
 `_Address_mode`  
 要使用的地址模式示例`texture_view`。 对于所有维度相同的寻址模式。  
  
 `_Sampler`  
 要使用的采样器配置示例`texture_view`。  
  
 `_Coord`  
 要采用从示例的坐标。 小数部分组成的坐标值用于之间示例纹素插值。  
  
### <a name="return-value"></a>返回值  
 级别 4 短矢量包含 4 的绿色 (y) 部分采样纹素值。  
  
##  <a name="gather_blue"></a> gather_blue 

 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的蓝色 (z) 组件。  
  
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
 `_Address_mode`  
 要使用的地址模式示例`texture_view`。 对于所有维度相同的寻址模式。  
  
 `_Sampler`  
 要使用的采样器配置示例`texture_view`。  
  
 `_Coord`  
 要采用从示例的坐标。 小数部分组成的坐标值用于之间示例纹素插值。  
  
### <a name="return-value"></a>返回值  
 级别 4 短矢量包含 4 的红色 (x) 部分采样纹素值。  
  
##  <a name="gather_alpha"></a> gather_alpha 

 使用指定的采样配置示例指定坐标处的纹理，并返回四个抽样纹素的字母 (w) 组件。  
  
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
 `_Address_mode`  
 要使用的地址模式示例`texture_view`。 对于所有维度相同的寻址模式。  
  
 `_Sampler`  
 要使用的采样器配置示例`texture_view`。  
  
 `_Coord`  
 要采用从示例的坐标。 小数部分组成的坐标值用于之间示例纹素插值。  
  
### <a name="return-value"></a>返回值  
 级别 4 短矢量包含字母 (w) 组件的 4 采样纹素值。  
  
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
 `_Index`  
 要获取，可能是多维的元素的索引。  
  
 `_Mip_level`  
 我们应从中获取的值 mipmap 级别。 默认值 0 表示最详细的 mipmap 级别。  
  
### <a name="return-value"></a>返回值  
 元素的值。  
  
##  <a name="operator_eq"></a> 运算符 = 

 将分配为指定的相同纹理视图`texture_view`至此`texture_view`实例。  
  
```  
texture_view<value_type, _Rank>& operator= (// [1] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

 
texture_view<const value_type, _Rank>& operator= (// [2] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

 
texture_view<const value_type, _Rank>& operator= (// [3] copy constructor  
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 [1，2]复制构造函数  
 可写`texture_view`对象。  
  
 [3] 复制构造函数  
 不可写`texture_view`对象。  
  
### <a name="return-value"></a>返回值  
 对此引用`texture_view`实例。  
  
##  <a name="operator_at"></a> operator] 

 按索引返回该元素的值。  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);

 
value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 索引中，可能是多维。  
  
 `_I0`  
 一维索引。  
  
### <a name="return-value"></a>返回值  
 按索引的元素值`_Index`。  
  
##  <a name="operator_call"></a> operator （) 

 按索引返回该元素的值。  
  
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
 `_Index`  
 索引中，可能是多维。  
  
 `_I0`  
 索引的最高有效组件。  
  
 `_I1`  
 索引的下一步-到-最高有效组件。  
  
 `_I2`  
 索引的最低有效组件。  
  
### <a name="return-value"></a>返回值  
 按索引的元素值`_Index`。  
  
##  <a name="sample"></a> 示例 

 使用指定的采样配置示例在指定的坐标和的详细信息级别的纹理。  
  
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
 `_Filter_mode`  
 要使用示例 texture_view 的筛选器模式。 筛选器模式是最小化、 最大化，和 mipmap 筛选器相同的。  
  
 `_Address_mode`  
 要用于示例 texture_view 寻址模式。 对于所有维度相同的寻址模式。  
  
 `_Sampler`  
 要使用示例 texture_view 的采样器配置。  
  
 `_Coord`  
 要采用从示例的坐标。 小数部分组成的坐标值用于纹素值之间插入。  
  
 `_Level_of_detail`  
 值指定要从示例的 mipmap 级别。 小数部分的值用于两个 mipmap 级别之间插值。 默认级别的详细信息是 0，它表示最详细的 mip 级别。  
  
### <a name="return-value"></a>返回值  
 内插的示例值中。  
  
##  <a name="set"></a> 设置 

 设置为指定的值的指定索引处的元素的值。  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>参数  
 `_Index`  
 要设置，可能是多维的元素的索引。  
  
 `value`  
 要将元素设置为的值。  
  
##  <a name="value_type"></a> value_type 

 Texture_view 元素的值类型。  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>请参阅  
 [Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
