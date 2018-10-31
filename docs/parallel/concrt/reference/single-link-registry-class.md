---
title: single_link_registry 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f03e3366caaf6b18ecb8f401fb3209f859113ca0
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163629"
---
# <a name="singlelinkregistry-class"></a>single_link_registry 类

`single_link_registry` 对象是仅管理单个源块或目标块的 `network_link_registry`。

## <a name="syntax"></a>语法

```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

#### <a name="parameters"></a>参数

*（_b)*<br/>
块数据类型存储在`single_link_registry`对象。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[single_link_registry](#ctor)|构造 `single_link_registry` 对象。|
|[~ single_link_registry 析构函数](#dtor)|销毁`single_link_registry`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[add](#add)|将添加一个指向`single_link_registry`对象。 (重写[network_link_registry:: add](network-link-registry-class.md#add)。)|
|[begin](#begin)|返回一个迭代器中的第一个元素到`single_link_registry`对象。 (重写[network_link_registry:: begin](network-link-registry-class.md#begin)。)|
|[包含](#contains)|搜索`single_link_registry`指定块的对象。 (重写[network_link_registry:: contains](network-link-registry-class.md#contains)。)|
|[count](#count)|中的项的计数`single_link_registry`对象。 (重写[network_link_registry:: count](network-link-registry-class.md#count)。)|
|[remove](#remove)|移除从链接`single_link_registry`对象。 (重写[network_link_registry:: remove](network-link-registry-class.md#remove)。)|

## <a name="inheritance-hierarchy"></a>继承层次结构

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

##  <a name="add"></a> 添加

将添加一个指向`single_link_registry`对象。

```
virtual void add(_EType _Link);
```

### <a name="parameters"></a>参数

*链接 （_l)*<br/>
指向要添加的块的指针。

### <a name="remarks"></a>备注

该方法将引发[invalid_link_target](invalid-link-target-class.md)异常，如果此注册表中已存在一个链接。

##  <a name="begin"></a> 开始

返回一个迭代器中的第一个元素到`single_link_registry`对象。

```
virtual iterator begin();
```

### <a name="return-value"></a>返回值

中的第一个元素的迭代器`single_link_registry`对象。

### <a name="remarks"></a>备注

最终状态由`NULL`链接。

##  <a name="contains"></a> 包含

搜索`single_link_registry`指定块的对象。

```
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>参数

*链接 （_l)*<br/>
指向要在其中搜索中的块的指针`single_link_registry`对象。

### <a name="return-value"></a>返回值

**true**找到了指定链接，如果**false**否则为。

##  <a name="count"></a> 计数

中的项的计数`single_link_registry`对象。

```
virtual size_t count();
```

### <a name="return-value"></a>返回值

中的项数`single_link_registry`对象。

##  <a name="remove"></a> 删除

移除从链接`single_link_registry`对象。

```
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>参数

*链接 （_l)*<br/>
指向块被删除，如果找到。

### <a name="return-value"></a>返回值

**true**找到该链接并将其删除，如果**false**否则为。

##  <a name="ctor"></a> single_link_registry

构造 `single_link_registry` 对象。

```
single_link_registry();
```

##  <a name="dtor"></a> ~ single_link_registry

销毁`single_link_registry`对象。

```
virtual ~single_link_registry();
```

### <a name="remarks"></a>备注

该方法将引发[invalid_operation](invalid-operation-class.md)异常，它调用之前删除的链接。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)
