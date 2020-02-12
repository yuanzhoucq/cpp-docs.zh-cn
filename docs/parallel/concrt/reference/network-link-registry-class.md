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
ms.openlocfilehash: 430190c11ec06a4f26eb9d8c4237552848420ad7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138892"
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
要存储在 `network_link_registry`中的块数据类型。

## <a name="members"></a>Members

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|`const_pointer`|一种类型，它提供指向 `network_link_registry` 对象中的 `const` 元素的指针。|
|`const_reference`|一种类型，该类型提供对存储在用于读取和执行 const 操作的 `network_link_registry` 对象中的 `const` 元素的引用。|
|`iterator`|一种类型，它提供可读取或修改 `network_link_registry` 对象中的任何元素的迭代器。|
|`type`|一种类型，它表示存储在 `network_link_registry` 对象中的块类型。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[add](#add)|当在派生类中重写时，向 `network_link_registry` 对象添加链接。|
|[begin](#begin)|当在派生类中重写时，将返回一个迭代器，该迭代器指向 `network_link_registry` 对象中的第一个元素。|
|[contains](#contains)|当在派生类中重写时，搜索指定块的 `network_link_registry` 对象。|
|[count](#count)|当在派生类中重写时，返回 `network_link_registry` 对象中的项数。|
|[remove](#remove)|当在派生类中重写时，从 `network_link_registry` 对象中移除指定的块。|

## <a name="remarks"></a>备注

对于并发访问而言，`network link registry` 是安全的。

## <a name="inheritance-hierarchy"></a>继承层次结构

`network_link_registry`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="add"></a>把

当在派生类中重写时，向 `network_link_registry` 对象添加链接。

```cpp
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

## <a name="begin"></a>准备

当在派生类中重写时，将返回一个迭代器，该迭代器指向 `network_link_registry` 对象中的第一个元素。

```cpp
virtual iterator begin() = 0;
```

### <a name="return-value"></a>返回值

用于寻址 `network_link_registry` 对象中第一个元素的迭代器。

### <a name="remarks"></a>备注

迭代器的结束状态由 `NULL` 链接指示。

## <a name="contains"></a>有

当在派生类中重写时，搜索指定块的 `network_link_registry` 对象。

```cpp
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向在 `network_link_registry` 对象中搜索的块的指针。

### <a name="return-value"></a>返回值

如果找到该块，**则为 true** ; 否则为**false** 。

## <a name="count"></a>计

当在派生类中重写时，返回 `network_link_registry` 对象中的项数。

```cpp
virtual size_t count() = 0;
```

### <a name="return-value"></a>返回值

`network_link_registry` 对象中的项数。

## <a name="remove"></a>取消

当在派生类中重写时，从 `network_link_registry` 对象中移除指定的块。

```cpp
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要删除的块的指针（如果找到）。

### <a name="return-value"></a>返回值

如果找到并删除了链接，**则为 true** ; 否则为**false** 。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)
