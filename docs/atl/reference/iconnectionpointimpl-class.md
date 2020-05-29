---
title: IConnectionPointImpl 类
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
ms.openlocfilehash: c62ac3310a579379674674a7a9a517e3f2fd60e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329856"
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl 类

此类实现连接点。

## <a name="syntax"></a>语法

```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IConnectionPointImpl`。

*皮伊德*<br/>
指向连接点对象表示的接口 IID 的指针。

*CDV*<br/>
管理连接的类。 默认值为[CComDynamicUnkarray，](../../atl/reference/ccomdynamicunkarray-class.md)它允许无限制的连接。 您还可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，它指定固定数量的连接。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IConnectionPointimpl：：建议](#advise)|在连接点和接收器之间建立连接。|
|[IConnectionPointimpl：：枚举连接](#enumconnections)|创建枚举器以循环通过连接点的连接。|
|[IConnection点impl：：获取连接接口](#getconnectioninterface)|检索连接点表示的接口的 IID。|
|[IConnectionPointimpl：：获取连接点容器](#getconnectionpointcontainer)|检索指向可连接对象的接口指针。|
|[IConnectionPointimpl：：取消建议](#unadvise)|终止以前通过`Advise`建立的连接。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[IConnectionPointimpl：：m_vec](#m_vec)|管理连接点的连接。|

## <a name="remarks"></a>备注

`IConnectionPointImpl`实现一个连接点，它允许对象向客户端公开传出接口。 客户端在称为接收器的对象上实现此接口。

ATL 使用[IConnectionPoint 容器Impl](../../atl/reference/iconnectionpointcontainerimpl-class.md)来实现可连接对象。 可连接对象中的每个连接点表示一个传出接口，由*piid*标识。 *CDV*类管理连接点和接收器之间的连接。 每个连接都由"cookie"唯一标识。

有关在 ATL 中使用连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_ICPLocator`

`IConnectionPointImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="iconnectionpointimpladvise"></a><a name="advise"></a>IConnectionPointimpl：：建议

在连接点和接收器之间建立连接。

```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```

### <a name="remarks"></a>备注

使用["不建议"](#unadvise)终止连接呼叫。

请参阅[IConnectionPoint：：Windows](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) SDK 中的建议。

## <a name="iconnectionpointimplenumconnections"></a><a name="enumconnections"></a>IConnectionPointimpl：：枚举连接

创建枚举器以循环通过连接点的连接。

```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```

### <a name="remarks"></a>备注

请参阅[IConnectPoint：Windows](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-enumconnections) SDK 中的枚举连接。

## <a name="iconnectionpointimplgetconnectioninterface"></a><a name="getconnectioninterface"></a>IConnection点impl：：获取连接接口

检索连接点表示的接口的 IID。

```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```

### <a name="remarks"></a>备注

请参阅[IConnectPoint：获取](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectioninterface)Windows SDK 中的连接接口。

## <a name="iconnectionpointimplgetconnectionpointcontainer"></a><a name="getconnectionpointcontainer"></a>IConnectionPointimpl：：获取连接点容器

检索指向可连接对象的接口指针。

```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```

### <a name="remarks"></a>备注

请参阅[IConnectPoint：获取](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-getconnectionpointcontainer)Windows SDK 中的连接点容器。

## <a name="iconnectionpointimplm_vec"></a><a name="m_vec"></a>IConnectionPointimpl：：m_vec

管理连接点对象和接收器之间的连接。

```
CDV m_vec;
```

### <a name="remarks"></a>备注

默认情况下，`m_vec`是[CComDynamic Unkarray 类型](../../atl/reference/ccomdynamicunkarray-class.md)。

## <a name="iconnectionpointimplunadvise"></a><a name="unadvise"></a>IConnectionPointimpl：：取消建议

终止以前通过[通知](#advise)建立的连接。

```
STDMETHOD(Unadvise)(DWORD dwCookie);
```

### <a name="remarks"></a>备注

请参阅[IConnectPoint：：](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)在 Windows SDK 中取消建议。

## <a name="see-also"></a>另请参阅

[IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint)<br/>
[类概述](../../atl/atl-class-overview.md)
