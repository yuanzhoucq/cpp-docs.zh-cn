---
title: writeonly_texture_view 类
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 8978a548ed246c59d7e7f007f1180685c7343a14
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126235"
---
# <a name="writeonly_texture_view-class"></a>writeonly_texture_view 类

提供对纹理的 writeonly 访问。

## <a name="syntax"></a>语法

```cpp
template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view;

template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>参数

*value_type*<br/>
纹理中元素的类型。

*_Rank*<br/>
纹理的排名。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`scalar_type`||
|`value_type`|纹理中元素的类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[writeonly_texture_view 构造函数](#ctor)|初始化 `writeonly_texture_view` 类的新实例。|
|[~ writeonly_texture_view 析构函数](#ctor)|销毁 `writeonly_texture_view` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[set](#set)|设置指定索引处的元素的值。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[operator=](#operator_eq)|将指定 `writeonly_texture_view` 对象复制到此对象。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[rank 常量](#rank)|获取 `writeonly_texture_view` 对象的排名。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>要求

**标头：** amp_graphics。h

**命名空间：** Concurrency：： graphics

## <a name="dtor"></a>~ writeonly_texture_view

销毁 `writeonly_texture_view` 的对象。

```cpp
~writeonly_texture_view() restrict(amp,cpu);
```

## <a name="operator_eq"></a>operator =

将指定 `writeonly_texture_view` 对象复制到此对象。

```cpp
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Other*<br/>
要从中复制的 `writeonly_texture_view` 对象。

### <a name="return-value"></a>返回值

对此 `writeonly_texture_view` 对象的引用。

## <a name="rank"></a>级别

获取 `writeonly_texture_view` 对象的排名。

```cpp
static const int rank = _Rank;
```

## <a name="set"></a>字符集

设置指定索引处的元素的值。

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>参数

*_Index*<br/>
元素的索引。

*value*<br/>
该元素的新值。

## <a name="ctor"></a>writeonly_texture_view

初始化 `writeonly_texture_view` 类的新实例。

```cpp
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>参数

*_Rank*<br/>
纹理的排名。

*value_type*<br/>
纹理中元素的类型。

*_Src*<br/>
用于创建 `writeonly_texture_view` 的纹理。

## <a name="see-also"></a>另请参阅

[Concurrency::graphics 命名空间](concurrency-graphics-namespace.md)
