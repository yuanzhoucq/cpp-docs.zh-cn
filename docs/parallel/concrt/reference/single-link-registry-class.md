---
title: single_link_registry 类
ms.date: 11/04/2016
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
ms.openlocfilehash: c29caf6d31df316e80b15fe6827c81e34ece8a18
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142726"
---
# <a name="single_link_registry-class"></a>single_link_registry 类

`single_link_registry` 对象是仅管理单个源块或目标块的 `network_link_registry`。

## <a name="syntax"></a>语法

```cpp
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```

### <a name="parameters"></a>参数

*_Block*<br/>
要存储在 `single_link_registry` 对象中的块数据类型。

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[single_link_registry](#ctor)|构造 `single_link_registry` 对象。|
|[~ single_link_registry 析构函数](#dtor)|销毁 `single_link_registry` 的对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[add](#add)|向 `single_link_registry` 对象添加链接。 （重写[network_link_registry：： add](network-link-registry-class.md#add)。）|
|[begin](#begin)|返回 `single_link_registry` 对象中第一个元素的迭代器。 （重写[network_link_registry：： begin](network-link-registry-class.md#begin)。）|
|[contains](#contains)|在 `single_link_registry` 对象中搜索指定的块。 （重写[network_link_registry：： contains](network-link-registry-class.md#contains)。）|
|[count](#count)|计算 `single_link_registry` 对象中的项数。 （重写[network_link_registry：： count](network-link-registry-class.md#count)。）|
|[remove](#remove)|删除 `single_link_registry` 对象的链接。 （重写[network_link_registry：： remove](network-link-registry-class.md#remove)。）|

## <a name="inheritance-hierarchy"></a>继承层次结构

[network_link_registry](network-link-registry-class.md)

`single_link_registry`

## <a name="requirements"></a>要求

**标头：** agents.h

**命名空间：** 并发

## <a name="add"></a>把

向 `single_link_registry` 对象添加链接。

```cpp
virtual void add(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要添加的块的指针。

### <a name="remarks"></a>备注

如果此注册表中已经有一个链接，该方法将引发[invalid_link_target](invalid-link-target-class.md)异常。

## <a name="begin"></a>准备

返回 `single_link_registry` 对象中第一个元素的迭代器。

```cpp
virtual iterator begin();
```

### <a name="return-value"></a>返回值

用于寻址 `single_link_registry` 对象中第一个元素的迭代器。

### <a name="remarks"></a>备注

结束状态由 `NULL` 链接指示。

## <a name="contains"></a>有

在 `single_link_registry` 对象中搜索指定的块。

```cpp
virtual bool contains(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要在 `single_link_registry` 对象中搜索的块的指针。

### <a name="return-value"></a>返回值

如果找到链接，**则为 true** ; 否则为**false** 。

## <a name="count"></a>计

计算 `single_link_registry` 对象中的项数。

```cpp
virtual size_t count();
```

### <a name="return-value"></a>返回值

`single_link_registry` 对象中的项数。

## <a name="remove"></a>取消

删除 `single_link_registry` 对象的链接。

```cpp
virtual bool remove(_EType _Link);
```

### <a name="parameters"></a>参数

*_Link*<br/>
指向要删除的块的指针（如果找到）。

### <a name="return-value"></a>返回值

如果找到并删除了链接，**则为 true** ; 否则为**false** 。

## <a name="ctor"></a>single_link_registry

构造 `single_link_registry` 对象。

```cpp
single_link_registry();
```

## <a name="dtor"></a>~ single_link_registry

销毁 `single_link_registry` 的对象。

```cpp
virtual ~single_link_registry();
```

### <a name="remarks"></a>备注

如果在删除链接之前调用此方法，则该方法会引发[invalid_operation](invalid-operation-class.md)异常。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[multi_link_registry 类](multi-link-registry-class.md)
