---
title: network_link_registry 类
ms.date: 11/04/2016
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
ms.openlocfilehash: 18fabd0e741c144201f299271cdd01eb9ac55fac
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222675"
---
# <a name="network_link_registry-class"></a>network_link_registry 类

`network_link_registry` 抽象基类管理源块和目标块之间的链接。

## <a name="syntax"></a>语法

```cpp
template<class _Block>
class network_link_registry;
```

### <a name="parameters"></a>参数

*_Block*<br/>
要存储在中的块数据类型 `network_link_registry` 。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`const_pointer`|一种类型，它提供指向 **`const`** 对象中元素的指针 `network_link_registry` 。|
|`const_reference`|一种类型，它提供对 **`const`** 存储在对象中的元素的引用， `network_link_registry` 以便读取和执行 const 运算。|
|`iterator`|一种类型，它提供可读取或修改对象中的任何元素的迭代器 `network_link_registry` 。|
|`type`|一种类型，它表示存储在对象中的块类型 `network_link_registry` 。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[add](#add)|当在派生类中重写时，将添加一个指向对象的链接 `network_link_registry` 。|
|[准备](#begin)|当在派生类中重写时，将返回一个迭代器，该迭代器指向对象中的第一个元素 `network_link_registry` 。|
|[contains](#contains)|当在派生类中重写时，在对象中搜索 `network_link_registry` 指定的块。|
|[计数](#count)|当在派生类中重写时，返回对象中的项数 `network_link_registry` 。|
|[删除](#remove)|当在派生类中重写时，从对象中移除指定的块 `network_link_registry` 。|

## <a name="remarks"></a>备注

`network link registry`对于并发访问而言，是不安全的。

## <a name="inheritance-hierarchy"></a>继承层次结构

`network_link_registry`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="add"></a><a name="add"></a>把

当在派生类中重写时，将添加一个指向对象的链接 `network_link_registry` 。

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

## <a name="begin"></a><a name="begin"></a>准备

当在派生类中重写时，将返回一个迭代器，该迭代器指向对象中的第一个元素 `network_link_registry` 。

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>返回值

用于寻址对象中第一个元素的迭代器 `network_link_registry` 。

### <a name="remarks"></a>备注

迭代器的结束状态由 `NULL` 链接指示。

## <a name="contains"></a><a name="contains"></a>有

当在派生类中重写时，在对象中搜索 `network_link_registry` 指定的块。

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向在对象中搜索的块的指针 `network_link_registry` 。

### <a name="return-value"></a>返回值

**`true`** 如果找到该块，则 **`false`** 为; 否则为。

## <a name="count"></a><a name="count"></a>计

当在派生类中重写时，返回对象中的项数 `network_link_registry` 。

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>返回值

`network_link_registry` 对象中的项数。

## <a name="remove"></a><a name="remove"></a>取消

当在派生类中重写时，从对象中移除指定的块 `network_link_registry` 。

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要删除的块的指针（如果找到）。

### <a name="return-value"></a>返回值

**`true`** 如果找到并删除了链接，则 **`false`** 为; 否则为。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)
