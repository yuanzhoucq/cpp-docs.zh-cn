---
title: IConnectionPointContainerImpl 类
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: f6009a1341d6715d6d2f170d3ff2aa1aa4ffcb96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329867"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 类

此类实现连接点容器来管理[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象的集合。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IConnectionPointContainerImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IConnectionPoint 容器 impl：：枚举连接点](#enumconnectionpoints)|创建枚举器以通过可连接对象中支持的连接点迭代。|
|[IConnectionPoint 容器 impl：：查找连接点](#findconnectionpoint)|检索指向支持指定 IID 的连接点的接口指针。|

## <a name="remarks"></a>备注

`IConnectionPointContainerImpl`实现连接点容器以管理[IConnectPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象的集合。 `IConnectionPointContainerImpl`提供了两种方法，客户端可以调用这些方法来检索有关可连接对象的详细信息：

- `EnumConnectionPoints`允许客户端确定对象支持哪个传出接口。

- `FindConnectionPoint`允许客户端确定对象是否支持特定的传出接口。

有关在 ATL 中使用连接点的信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="iconnectionpointcontainerimplenumconnectionpoints"></a><a name="enumconnectionpoints"></a>IConnectionPoint 容器 impl：：枚举连接点

创建枚举器以通过可连接对象中支持的连接点迭代。

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>备注

请参阅[IConnectPoint 容器：Windows SDK 中的枚举连接点](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints)。

## <a name="iconnectionpointcontainerimplfindconnectionpoint"></a><a name="findconnectionpoint"></a>IConnectionPoint 容器 impl：：查找连接点

检索指向支持指定 IID 的连接点的接口指针。

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>备注

请参阅[IConnectPoint 容器：在](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint)Windows SDK 中查找连接点。

## <a name="see-also"></a>另请参阅

[IConnectionPoint 容器](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[类概述](../../atl/atl-class-overview.md)
