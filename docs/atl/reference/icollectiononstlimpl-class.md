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
ms.openlocfilehash: 6842f1c75ebbc9c3dfdd93f30d52fd2cb2936c03
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779217"
---
# <a name="icollectiononstlimpl-class"></a>ICollectionOnSTLImpl 类

此类提供了使用集合类的方法。

## <a name="syntax"></a>语法

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>参数

*T*<br/>
COM 集合接口。

*CollType*<br/>
C + + 标准库容器类。

*ItemType*<br/>
容器接口所显示的项的类型。

*CopyItem*<br/>
一个[复制策略类](../../atl/atl-copy-policy-classes.md)。

*EnumType*<br/>
一个[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)-兼容的枚举器类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|返回集合的枚举器对象。|
|[ICollectionOnSTLImpl::getcount](#get_count)|返回集合中的元素数。|
|[ICollectionOnSTLImpl::get_Item](#get_item)|从集合返回请求的项。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|集合。|

## <a name="remarks"></a>备注

此类提供了三种方法的集合接口的实现： [getcount](#get_count)， [get_Item](#get_item)，并[get__NewEnum](#newenum)。

若要使用此类：

- 定义 （或借用） 想要实现的集合接口。

- 您的类派生的专用化`ICollectionOnSTLImpl`基于此集合接口。

- 使用派生的类实现中未处理的集合接口的任何方法`ICollectionOnSTLImpl`。

> [!NOTE]
>  如果集合接口是双重接口，派生类从[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)，并传入`ICollectionOnSTLImpl`如果你想 ATL 提供的实现的第一个模板参数的专用化`IDispatch`方法。

- 将项添加到[程序 m_coll](#m_coll)要填充的集合成员。

有关详细信息和示例，请参阅[ATL 集合和枚举器](../../atl/atl-collections-and-enumerators.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="get_count"></a>  ICollectionOnSTLImpl::getcount

此方法返回集合中项的数目。

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>参数

*pcount*<br/>
[out]集合中的元素数。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="get_item"></a>  ICollectionOnSTLImpl::get_Item

此方法从集合中返回指定的项。

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>参数

*Tuple*<br/>
[in]集合中的项的从 1 开始的索引。

*pvar*<br/>
[out]对应的项*索引*。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

通过将复制的数据中指定的位置获取项[程序 m_coll](#m_coll)使用的复制方法[复制策略类](../../atl/atl-copy-policy-classes.md)作为模板参数中传递`ICollectionOnSTLImpl`专用化。

##  <a name="newenum"></a>  ICollectionOnSTLImpl::get__NewEnum

返回集合的枚举器对象。

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>参数

*ppUnk*<br/>
[out]**IUnknown**新创建的枚举数对象的指针。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

### <a name="remarks"></a>备注

新创建枚举器保留对原始集合的迭代器`m_coll`，（因此不会创建副本） 并要确保集合保持活动状态，尽管有未完成的枚举器的集合对象上保存的 COM 引用。

##  <a name="m_coll"></a>  ICollectionOnSTLImpl::m_coll

此成员保留表示集合的项。

```
CollType m_coll;
```

## <a name="see-also"></a>请参阅

[ATLCollections 示例](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)
