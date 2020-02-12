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
ms.openlocfilehash: 35c7cc72520cdb0675abf9c15574a49e33741d0b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142700"
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

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`const_pointer`|一种类型，它提供指向 `source_link_manager` 对象中的 `const` 元素的指针。|
|`const_reference`|一种类型，该类型提供对存储在用于读取和执行 const 操作的 `source_link_manager` 对象中的 `const` 元素的引用。|
|`iterator`|一种类型，它提供可读取或修改 `source_link_manager` 对象中的任何元素的迭代器。|
|`type`|由 `source_link_manager` 对象管理的链接注册表的类型。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[source_link_manager](#ctor)|构造 `source_link_manager` 对象。|
|[~ source_link_manager 析构函数](#dtor)|销毁 `source_link_manager` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[add](#add)|将源链接添加到 `source_link_manager` 的对象。|
|[begin](#begin)|返回 `source_link_manager` 对象中第一个元素的迭代器。|
|[contains](#contains)|在此 `source_link_manager` 对象中搜索指定块的 `network_link_registry`。|
|[count](#count)|计算 `source_link_manager` 对象中链接块的数目。|
|[reference](#reference)|获取 `source_link_manager` 对象上的引用。|
|[register_target_block](#register_target_block)|注册包含此 `source_link_manager` 对象的目标块。|
|[release](#release)|释放 `source_link_manager` 对象上的引用。|
|[remove](#remove)|删除 `source_link_manager` 对象的链接。|
|[set_bound](#set_bound)|设置可以添加到此 `source_link_manager` 对象的源链接的最大数目。|

## <a name="remarks"></a>备注

当前，源块是引用计数的。 这是 `network_link_registry` 对象上的包装器，它允许并发访问链接，并提供通过回调引用链接的功能。 消息块（`target_block`s 或 `propagator_block`s）应将此类用于其源链接。

## <a name="inheritance-hierarchy"></a>继承层次结构

`source_link_manager`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="add"></a>把

将源链接添加到 `source_link_manager` 的对象。

```cpp
void add(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

## <a name="begin"></a>准备

返回 `source_link_manager` 对象中第一个元素的迭代器。

```cpp
iterator begin();
```

### <a name="return-value"></a>返回值

用于寻址 `source_link_manager` 对象中第一个元素的迭代器。

### <a name="remarks"></a>备注

迭代器的结束状态由 `NULL` 链接指示。

## <a name="contains"></a>有

在此 `source_link_manager` 对象中搜索指定块的 `network_link_registry`。

```cpp
bool contains(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要在 `source_link_manager` 对象中搜索的块的指针。

### <a name="return-value"></a>返回值

如果找到指定的块，**则为 true** ; 否则为**false** 。

## <a name="count"></a>计

计算 `source_link_manager` 对象中链接块的数目。

```cpp
size_t count();
```

### <a name="return-value"></a>返回值

`source_link_manager` 对象中的链接块的数目。

## <a name="reference"></a>对

获取 `source_link_manager` 对象上的引用。

```cpp
void reference();
```

## <a name="register_target_block"></a>register_target_block

注册包含此 `source_link_manager` 对象的目标块。

```cpp
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```

### <a name="parameters"></a>参数

*_PTarget*<br/>
包含此 `source_link_manager` 对象的目标块。

## <a name="release"></a>拆卸

释放 `source_link_manager` 对象上的引用。

```cpp
void release();
```

## <a name="remove"></a>取消

删除 `source_link_manager` 对象的链接。

```cpp
bool remove(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要删除的块的指针（如果找到）。

### <a name="return-value"></a>返回值

如果找到并删除了链接，**则为 true** ; 否则为**false** 。

## <a name="set_bound"></a>set_bound

设置可以添加到此 `source_link_manager` 对象的源链接的最大数目。

```cpp
void set_bound(size_t _MaxLinks);
```

### <a name="parameters"></a>参数

*_MaxLinks*<br/>
最大链接数。

## <a name="ctor"></a>source_link_manager

构造 `source_link_manager` 对象。

```cpp
source_link_manager();
```

## <a name="dtor"></a>~ source_link_manager

销毁 `source_link_manager` 的对象。

```cpp
~source_link_manager();
```

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)
