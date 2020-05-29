---
title: ICollectionOnSTLImpl 类
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: a8ccab08b89da8c1b8ef56c8932e27a6c74e62aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329905"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl 类

此类提供集合类使用的方法。

## <a name="syntax"></a>语法

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>参数

*T*<br/>
COM 集合接口。

*拼贴*<br/>
C++标准库容器类。

*项目类型*<br/>
容器接口公开的项的类型。

*复制项目*<br/>
[复制策略类](../../atl/atl-copy-policy-classes.md)。

*枚举类型*<br/>
[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)- 兼容枚举器类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[ICollectiononSTLimpl：：get__NewEnum](#newenum)|返回集合的枚举对象。|
|[ICollectiononSTLimpl：：获取计数](#get_count)|返回集合中的元素数。|
|[ICollectiononSTLimpl：get_Item](#get_item)|从集合返回请求的项。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[ICollectiononSTLimpl：m_coll](#m_coll)|集合。|

## <a name="remarks"></a>备注

此类为集合接口的三种方法提供实现[：getcount、get_Item](#get_count)和[get_Item](#get_item)[get__NewEnum](#newenum)。

要使用此类：

- 定义（或借用）要实现的集合接口。

- 基于此集合接口的`ICollectionOnSTLImpl`专门化派生类。

- 使用派生类实现来自 未由`ICollectionOnSTLImpl`处理的集合接口的任何方法。

> [!NOTE]
> 如果集合接口是双接口，请从[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)派生类，如果希望`ICollectionOnSTLImpl`ATL 提供`IDispatch`方法的实现，则将专业化作为第一个模板参数传递。

- 将项添加到[m_coll](#m_coll)成员以填充集合。

有关详细信息和示例，请参阅[ATL 集合和枚举器](../../atl/atl-collections-and-enumerators.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a>ICollectiononSTLimpl：：获取计数

此方法返回集合中的项数。

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>参数

*pcount*<br/>
[出]集合中的元素数。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a>ICollectiononSTLimpl：get_Item

此方法从集合中返回指定的项。

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>参数

*索引*<br/>
[在]集合中项的基于 1 的索引。

*普瓦尔*<br/>
[出]对应于*索引*的项 。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

通过使用在`ICollectionOnSTLImpl`专门化中作为模板参数传递[的复制策略类](../../atl/atl-copy-policy-classes.md)的复制方法，在[m_coll](#m_coll)的指定位置复制数据，从而获取该项目。

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a>ICollectiononSTLimpl：：get__NewEnum

返回集合的枚举对象。

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>参数

*普恩克*<br/>
[出]新创建的枚举器对象的**I 未知**指针。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

### <a name="remarks"></a>备注

新创建的枚举器在原始集合上维护迭代器`m_coll`（因此不创建副本），并在集合对象上保留 COM 引用，以确保集合在存在未完成的枚举器时保持活动状态。

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a>ICollectiononSTLimpl：m_coll

此成员保存集合表示的项。

```
CollType m_coll;
```

## <a name="see-also"></a>另请参阅

[ATL集合示例](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)
