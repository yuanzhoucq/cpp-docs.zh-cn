---
title: sampler 类 |Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
dev_langs:
- C++
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee5d50976b6d91bff6d84ec288560ff1348c73d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424685"
---
# <a name="sampler-class"></a>sampler 类

采样器类聚合用于纹理采样的采样配置信息。

## <a name="syntax"></a>语法

```cpp
class sampler;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[采样器构造函数](#ctor)|已重载。 构造采样器实例。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|返回`address_mode`与采样器对象关联。|
|[get_border_color](#get_border_color)|返回与采样器对象关联的边框颜色。|
|[get_filter_mode](#get_filter_mode)|返回`filter_mode`与采样器对象关联。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[operator=](#operator_eq)|已重载。 赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[address_mode](#address_mode)|获取的地址模式`sampler`对象。|
|[border_color](#border_color)|获取边框颜色的`sampler`对象。|
|[filter_mode](#filter_mode)|获取的筛选器模式`sampler`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`sampler`

## <a name="requirements"></a>要求

**标头：** amp_graphics.h

**Namespace:** concurrency:: graphics

##  <a name="ctor"></a> 采样器

构造的实例[sampler 类](sampler-class.md)。

```cpp
sampler() restrict(cpu);    // [1] default constructor

sampler(                    // [2] constructor
    filter_mode _Filter_mode) restrict(cpu);

sampler(                    // [3] constructor
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [4] constructor
    filter_mode _Filter_mode,
    address_mode _Address_mode,
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

sampler(                    // [5] copy constructor
    const sampler& _Other) restrict(amp,
    cpu);

sampler(                    // [6] move constructor
    sampler&& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>参数

*_Filter_mode*<br/>
要在采样中使用的筛选器模式。

*_Address_mode*<br/>
要在采样中使用的所有维度的寻址模式。

*_Border_color*<br/>
如果寻址模式是 address_border，则将使用边框颜色。 默认值为 `float_4(0.0f, 0.0f, 0.0f, 0.0f)`。

*_Other*<br/>
[5] 复制构造函数`sampler`要复制到新对象`sampler`实例。

[6] 移动构造函数`sampler`对象将移到新`sampler`实例。

##  <a name="address_mode"></a> address_mode

获取的地址模式`sampler`对象。

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

##  <a name="border_color"></a> border_color

获取边框颜色的`sampler`对象。

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

##  <a name="filter_mode"></a> filter_mode

获取的筛选器模式`sampler`对象。

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

##  <a name="get_address_mode"></a> get_address_mode

返回为此配置的筛选器模式`sampler`。

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>返回值

为采样器配置的寻址模式。

##  <a name="get_border_color"></a> get_border_color

返回为此配置的边框颜色`sampler`。

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>返回值

包含边框颜色的 float_4。

##  <a name="get_filter_mode"></a> get_filter_mode

返回为此配置的筛选器模式`sampler`。

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>返回值

为采样器配置筛选器模式。

##  <a name="operator_eq"></a> 运算符 =

将另一个采样器对象的值分配给现有的采样器。

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
[1] 复制赋值运算符`sampler`要复制到此对象`sampler`。

[2] 移动赋值运算符`sampler`要移到此对象`sampler`。

### <a name="return-value"></a>返回值

对此采样器实例的引用。

## <a name="see-also"></a>请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
