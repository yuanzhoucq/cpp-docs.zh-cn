---
title: multi_link_registry 类
ms.date: 11/04/2016
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
ms.openlocfilehash: 777b3f5206b4a595b5dcac653d608255e92f4ef6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231697"
---
# <a name="multi_link_registry-class"></a>multi_link_registry 类

`multi_link_registry` 对象是管理多个源块或多个目标块的 `network_link_registry`。

## <a name="syntax"></a>语法

```cpp
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>参数

*_Block*<br/>
要存储在对象中的块数据类型 `multi_link_registry` 。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[multi_link_registry](#ctor)|构造 `multi_link_registry` 对象。|
|[~ multi_link_registry 析构函数](#dtor)|销毁 `multi_link_registry` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[add](#add)|添加指向对象的链接 `multi_link_registry` 。 （重写[network_link_registry：： add](network-link-registry-class.md#add)。）|
|[准备](#begin)|返回一个迭代器，该迭代器指向对象中的第一个元素 `multi_link_registry` 。 （重写[network_link_registry：： begin](network-link-registry-class.md#begin)。）|
|[contains](#contains)|在对象中搜索 `multi_link_registry` 指定的块。 （重写[network_link_registry：： contains](network-link-registry-class.md#contains)。）|
|[计数](#count)|计算对象中项的数目 `multi_link_registry` 。 （重写[network_link_registry：： count](network-link-registry-class.md#count)。）|
|[删除](#remove)|从对象中删除链接 `multi_link_registry` 。 （重写[network_link_registry：： remove](network-link-registry-class.md#remove)。）|
|[set_bound](#set_bound)|设置对象可以容纳的链接数的上限 `multi_link_registry` 。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[network_link_registry](network-link-registry-class.md)

`multi_link_registry`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="add"></a><a name="add"></a>把

添加指向对象的链接 `multi_link_registry` 。

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

### <a name="remarks"></a>备注

如果链接已存在于注册表中，则该方法将引发[invalid_link_target](invalid-link-target-class.md)异常，如果已使用函数设置了绑定， `set_bound` 并且链接已被移除，则会引发该异常。

## <a name="begin"></a><a name="begin"></a>准备

返回一个迭代器，该迭代器指向对象中的第一个元素 `multi_link_registry` 。

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>返回值

用于寻址对象中第一个元素的迭代器 `multi_link_registry` 。

### <a name="remarks"></a>备注

结束状态由 `NULL` 链接指示。

## <a name="contains"></a><a name="contains"></a>有

在对象中搜索 `multi_link_registry` 指定的块。

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要在对象中搜索的块的指针 `multi_link_registry` 。

### <a name="return-value"></a>返回值

**`true`** 如果找到指定的块，则 **`false`** 为; 否则为。

## <a name="count"></a><a name="count"></a>计

计算对象中项的数目 `multi_link_registry` 。

```cpp
virtual size_t count();
```

### <a name="return-value"></a>返回值

`multi_link_registry` 对象中的项数。

## <a name="multi_link_registry"></a><a name="ctor"></a>multi_link_registry

构造 `multi_link_registry` 对象。

```cpp
multi_link_registry();
```

## <a name="multi_link_registry"></a><a name="dtor"></a>~ multi_link_registry

销毁 `multi_link_registry` 对象。

```cpp
virtual ~multi_link_registry();
```

### <a name="remarks"></a>备注

如果在删除所有链接之前调用，则方法会引发[invalid_operation](invalid-operation-class.md)异常。

## <a name="remove"></a><a name="remove"></a>取消

从对象中删除链接 `multi_link_registry` 。

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要删除的块的指针（如果找到）。

### <a name="return-value"></a>返回值

**`true`** 如果找到并删除了链接，则 **`false`** 为; 否则为。

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

设置对象可以容纳的链接数的上限 `multi_link_registry` 。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>参数

*_MaxLinks*<br/>
对象可容纳的最大链接数 `multi_link_registry` 。

### <a name="remarks"></a>备注

设置了界限后，取消某项的链接将导致 `multi_link_registry` 对象进入不可变状态，在该状态下进一步调用 `add` 将引发 `invalid_link_target` 异常。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)
