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
ms.openlocfilehash: 2537ed857651b5210b104a270b3d827246b8339a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273343"
---
# <a name="networklinkregistry-class"></a>network_link_registry 类


  `network_link_registry` 抽象基类管理源块和目标块之间的链接。

## <a name="syntax"></a>语法

```
template<class _Block>
class network_link_registry;
```

#### <a name="parameters"></a>参数

*_Block*<br/>
块数据类型存储在`network_link_registry`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`const_pointer`|提供一个指针指向的类型`const`中的元素`network_link_registry`对象。|
|`const_reference`|提供对引用的类型`const`元素存储在`network_link_registry`用于读取和执行 const 操作的对象。|
|`iterator`|提供的迭代器的类型可读取或修改中的任何元素`network_link_registry`对象。|
|`type`|表示存储中的块类型的类型`network_link_registry`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[add](#add)|当在派生类中重写，将添加一个指向`network_link_registry`对象。|
|[begin](#begin)|当在派生类中重写时返回一个迭代器中的第一个元素到`network_link_registry`对象。|
|[contains](#contains)|当在派生类中重写，将搜索`network_link_registry`指定块的对象。|
|[count](#count)|当在派生类中重写时返回中的项数`network_link_registry`对象。|
|[remove](#remove)|当在派生类中重写中删除指定的块从`network_link_registry`对象。|

## <a name="remarks"></a>备注

`network link registry`是不安全的并发访问。

## <a name="inheritance-hierarchy"></a>继承层次结构

`network_link_registry`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="add"></a> add

当在派生类中重写，将添加一个指向`network_link_registry`对象。

```
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

##  <a name="begin"></a> begin

当在派生类中重写时返回一个迭代器中的第一个元素到`network_link_registry`对象。

```
virtual iterator begin() = 0;
```

### <a name="return-value"></a>返回值

中的第一个元素的迭代器`network_link_registry`对象。

### <a name="remarks"></a>备注

迭代器的最终状态由`NULL`链接。

##  <a name="contains"></a> 包含

当在派生类中重写，将搜索`network_link_registry`指定块的对象。

```
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要搜索的中的块的指针`network_link_registry`对象。

### <a name="return-value"></a>返回值

**true**找到块，如果**false**否则为。

##  <a name="count"></a> count

当在派生类中重写时返回中的项数`network_link_registry`对象。

```
virtual size_t count() = 0;
```

### <a name="return-value"></a>返回值

中的项数`network_link_registry`对象。

##  <a name="remove"></a> 删除

当在派生类中重写中删除指定的块从`network_link_registry`对象。

```
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向块被删除，如果找到。

### <a name="return-value"></a>返回值

**true**找到该链接并将其删除，如果**false**否则为。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[single_link_registry 类](single-link-registry-class.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)
