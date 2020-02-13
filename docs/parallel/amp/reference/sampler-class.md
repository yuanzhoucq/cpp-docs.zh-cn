---
title: sampler 类
ms.date: 06/28/2018
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
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
ms.openlocfilehash: 8f47bf6e9b88dba1e94e9e2ed2b93c8d2d3f9b8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126343"
---
# <a name="sampler-class"></a>sampler 类

采样器类聚合要用于纹理采样的采样配置信息。

## <a name="syntax"></a>语法

```cpp
class sampler;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[采样器构造函数](#ctor)|已重载。 构造采样器实例。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[get_address_mode](#get_address_mode)|返回与采样器对象关联的 `address_mode`。|
|[get_border_color](#get_border_color)|返回与采样器对象关联的边框颜色。|
|[get_filter_mode](#get_filter_mode)|返回与采样器对象关联的 `filter_mode`。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator=](#operator_eq)|已重载。 赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[address_mode](#address_mode)|获取 `sampler` 对象的地址模式。|
|[border_color](#border_color)|获取 `sampler` 对象的边框颜色。|
|[filter_mode](#filter_mode)|获取 `sampler` 对象的筛选器模式。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`sampler`

## <a name="requirements"></a>要求

**标头：** amp_graphics。h

**命名空间：** concurrency：： graphics

## <a name="ctor"></a>采样

构造[采样器类](sampler-class.md)的实例。

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
要用于所有维度采样的寻址模式。

*_Border_color*<br/>
Address_border 地址模式时要使用的边框颜色。 默认值是 `float_4(0.0f, 0.0f, 0.0f, 0.0f)`。

*_Other*<br/>
[5] 复制构造函数要复制到新的 `sampler` 实例的 `sampler` 对象。

[6] 将构造函数移至新的 `sampler` 实例 `sampler` 对象。

## <a name="address_mode"></a>address_mode

获取 `sampler` 对象的地址模式。

```cpp
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;
```

## <a name="border_color"></a>border_color

获取 `sampler` 对象的边框颜色。

```cpp
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;
```

## <a name="filter_mode"></a>filter_mode

获取 `sampler` 对象的筛选器模式。

```cpp
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;
```

## <a name="get_address_mode"></a>get_address_mode

返回为此 `sampler`配置的筛选器模式。

```cpp
Concurrency::graphics::address_mode get_address_mode() const __GPU;
```

### <a name="return-value"></a>返回值

为采样器配置的地址模式。

## <a name="get_border_color"></a>get_border_color

返回为此 `sampler`配置的边框颜色。

```cpp
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```

### <a name="return-value"></a>返回值

包含边框颜色的 float_4。

## <a name="get_filter_mode"></a>get_filter_mode

返回为此 `sampler`配置的筛选器模式。

```cpp
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```

### <a name="return-value"></a>返回值

为采样器配置的筛选器模式。

## <a name="operator_eq"></a>operator =

将另一个采样器对象的值分配给现有采样器。

```cpp
sampler& operator= (    // [1] copy assignment operator
    const sampler& _Other) restrict(amp, cpu);

sampler& operator= (    // [2] move assignment operator
    sampler&& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
[1] 复制赋值运算符要复制到此 `sampler`的 `sampler` 对象。

[2] 移动赋值运算符要移入此 `sampler`的 `sampler` 对象。

### <a name="return-value"></a>返回值

对此采样器实例的引用。

## <a name="see-also"></a>另请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
