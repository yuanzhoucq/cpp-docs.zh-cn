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
ms.openlocfilehash: 278ca6b1b9aac9539680d90b6fa0b18df22fc2f0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496014"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 类

此类实现连接点容器以管理[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象的集合。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IConnectionPointContainerImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|创建一个枚举器, 用于循环访问可连接对象中支持的连接点。|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|检索指向支持指定 IID 的连接点的接口指针。|

## <a name="remarks"></a>备注

`IConnectionPointContainerImpl`实现连接点容器以管理[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象的集合。 `IConnectionPointContainerImpl`提供了两个客户端可以调用来检索有关可连接对象的详细信息的方法:

- `EnumConnectionPoints`允许客户端确定对象支持的传出接口。

- `FindConnectionPoint`允许客户端确定对象是否支持特定的输出接口。

有关在 ATL 中使用连接点的信息, 请参阅文章[连接点](../../atl/atl-connection-points.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints

创建一个枚举器, 用于循环访问可连接对象中支持的连接点。

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IConnectionPointContainer:: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) 。

##  <a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint

检索指向支持指定 IID 的连接点的接口指针。

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) 。

## <a name="see-also"></a>请参阅

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[类概述](../../atl/atl-class-overview.md)
