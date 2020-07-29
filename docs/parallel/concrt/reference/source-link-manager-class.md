---
title: source_link_manager 类
ms.date: 11/04/2016
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
ms.openlocfilehash: 98f99bb5aec85a640eaf83a07fae3a1b667f7d91
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228422"
---
# <a name="source_link_manager-class"></a>source_link_manager 类

`source_link_manager` 对象管理到 `ISource` 块的消息块网络链接。

## <a name="syntax"></a>语法

```cpp
template<class _LinkRegistry>
class source_link_manager;
```

### <a name="parameters"></a>参数

*_LinkRegistry*<br/>
网络链接注册表。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`const_pointer`|一种类型，它提供指向 **`const`** 对象中元素的指针 `source_link_manager` 。|
|`const_reference`|一种类型，它提供对 **`const`** 存储在对象中的元素的引用， `source_link_manager` 以便读取和执行 const 运算。|
|`iterator`|一种类型，它提供可读取或修改对象中的任何元素的迭代器 `source_link_manager` 。|
|`type`|由对象管理的链接注册表的类型 `source_link_manager` 。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[source_link_manager](#ctor)|构造 `source_link_manager` 对象。|
|[~ source_link_manager 析构函数](#dtor)|销毁 `source_link_manager` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[add](#add)|将源链接添加到 `source_link_manager` 对象。|
|[准备](#begin)|返回一个迭代器，该迭代器指向对象中的第一个元素 `source_link_manager` 。|
|[contains](#contains)|在 `network_link_registry` 此对象内搜索 `source_link_manager` 指定块的。|
|[计数](#count)|计算对象中链接块的数目 `source_link_manager` 。|
|[reference](#reference)|获取对对象的引用 `source_link_manager` 。|
|[register_target_block](#register_target_block)|注册包含此对象的目标块 `source_link_manager` 。|
|[拆卸](#release)|释放对象上的引用 `source_link_manager` 。|
|[删除](#remove)|从对象中删除链接 `source_link_manager` 。|
|[set_bound](#set_bound)|设置可以添加到此对象的源链接的最大数目 `source_link_manager` 。|

## <a name="remarks"></a>备注

当前，源块是引用计数的。 这是对象上的包装器， `network_link_registry` 它允许并发访问链接，并提供通过回调引用链接的功能。 消息块 `target_block` `propagator_block` 应该将此类用于其源链接。

## <a name="inheritance-hierarchy"></a>继承层次结构

`source_link_manager`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="add"></a><a name="add"></a>把

将源链接添加到 `source_link_manager` 对象。

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

## <a name="begin"></a><a name="begin"></a>准备

返回一个迭代器，该迭代器指向对象中的第一个元素 `source_link_manager` 。

```cpp
iterator begin();
```

### <a name="return-value"></a>返回值

用于寻址对象中第一个元素的迭代器 `source_link_manager` 。

### <a name="remarks"></a>备注

迭代器的结束状态由 `NULL` 链接指示。

## <a name="contains"></a><a name="contains"></a>有

在 `network_link_registry` 此对象内搜索 `source_link_manager` 指定块的。

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要在对象中搜索的块的指针 `source_link_manager` 。

### <a name="return-value"></a>返回值

**`true`** 如果找到指定的块，则 **`false`** 为; 否则为。

## <a name="count"></a><a name="count"></a>计

计算对象中链接块的数目 `source_link_manager` 。

```cpp
size_t count();
```

### <a name="return-value"></a>返回值

对象中链接块的数目 `source_link_manager` 。

## <a name="reference"></a><a name="reference"></a>对

获取对对象的引用 `source_link_manager` 。

```cpp
void reference();
```

## <a name="register_target_block"></a><a name="register_target_block"></a>register_target_block

注册包含此对象的目标块 `source_link_manager` 。

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
包含此对象的目标块 `source_link_manager` 。

## <a name="release"></a><a name="release"></a>拆卸

释放对象上的引用 `source_link_manager` 。

```cpp
void release();
```

## <a name="remove"></a><a name="remove"></a>取消

从对象中删除链接 `source_link_manager` 。

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要删除的块的指针（如果找到）。

### <a name="return-value"></a>返回值

**`true`** 如果找到并删除了链接，则 **`false`** 为; 否则为。

## <a name="set_bound"></a><a name="set_bound"></a>set_bound

设置可以添加到此对象的源链接的最大数目 `source_link_manager` 。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>参数

*_MaxLinks*<br/>
最大链接数。

## <a name="source_link_manager"></a><a name="ctor"></a>source_link_manager

构造 `source_link_manager` 对象。

```cpp
source_link_manager();
```

## <a name="source_link_manager"></a><a name="dtor"></a>~ source_link_manager

销毁 `source_link_manager` 对象。

```cpp
~source_link_manager();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)
