---
title: IConnectionPointImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl
- ATLCOM/ATL::IConnectionPointImpl::Advise
- ATLCOM/ATL::IConnectionPointImpl::EnumConnections
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionInterface
- ATLCOM/ATL::IConnectionPointImpl::GetConnectionPointContainer
- ATLCOM/ATL::IConnectionPointImpl::Unadvise
- ATLCOM/ATL::IConnectionPointImpl::m_vec
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], implementing
- IConnectionPointImpl class
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 444dea401fa711b40e4d8229b26c9cdbf6d1fcbc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="iconnectionpointimpl-class"></a>IConnectionPointImpl 类
此类实现连接点。  
  
## <a name="syntax"></a>语法  
  
```
template<class T, const IID* piid, class CDV = CComDynamicUnkArray>  
class ATL_NO_VTABLE IConnectionPointImpl : public _ICPLocator<piid>
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IConnectionPointImpl`。  
  
 `piid`  
 指向由连接点对象的接口的 IID 的指针。  
  
 `CDV`  
 管理连接一个类。 默认值是[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，它允许不受限制的连接。 你还可以使用[CComUnkArray](../../atl/reference/ccomunkarray-class.md)，它指定固定的数量的连接。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](#advise)|建立的连接点和接收器之间的连接。|  
|[IConnectionPointImpl::EnumConnections](#enumconnections)|创建一个枚举器循环访问的连接点的连接。|  
|[IConnectionPointImpl::GetConnectionInterface](#getconnectioninterface)|检索由连接点表示接口的 IID。|  
|[IConnectionPointImpl::GetConnectionPointContainer](#getconnectionpointcontainer)|检索到可连接对象的接口指针。|  
|[IConnectionPointImpl::Unadvise](#unadvise)|终止通过以前建立的连接`Advise`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[IConnectionPointImpl::m_vec](#m_vec)|管理连接点的连接。|  
  
## <a name="remarks"></a>备注  
 `IConnectionPointImpl` 实现连接点，这样要公开给客户端的传出接口的对象。 客户端在调用接收器的对象上实现此接口。  
  
 使用 ATL [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)实现可连接对象。 可连接对象中的每个连接点表示的传出接口，由标识`piid`。 类*CDV*管理之间的连接点和接收器的连接。 每个连接进行唯一标识的"cookie"。  
  
 有关使用 ATL 中的连接点的详细信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="advise"></a>  IConnectionPointImpl::Advise  
 建立的连接点和接收器之间的连接。  
  
```
STDMETHOD(Advise)(
    IUnknown* pUnkSink,
    DWORD* pdwCookie);
```  
  
### <a name="remarks"></a>备注  
 使用[Unadvise](#unadvise)终止连接调用。  
  
 请参阅[IConnectionPoint::Advise](http://msdn.microsoft.com/library/windows/desktop/ms678815) Windows SDK 中。  
  
##  <a name="enumconnections"></a>  IConnectionPointImpl::EnumConnections  
 创建一个枚举器循环访问的连接点的连接。  
  
```
STDMETHOD(EnumConnections)(IEnumConnections** ppEnum);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPoint::EnumConnections](http://msdn.microsoft.com/library/windows/desktop/ms680755) Windows SDK 中。  
  
##  <a name="getconnectioninterface"></a>  IConnectionPointImpl::GetConnectionInterface  
 检索由连接点表示接口的 IID。  
  
```
STDMETHOD(GetConnectionInterface)(IID* piid2);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPoint::GetConnectionInterface](http://msdn.microsoft.com/library/windows/desktop/ms693468) Windows SDK 中。  
  
##  <a name="getconnectionpointcontainer"></a>  IConnectionPointImpl::GetConnectionPointContainer  
 检索到可连接对象的接口指针。  
  
```
STDMETHOD(GetConnectionPointContainer)(IConnectionPointContainer** ppCPC);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPoint::GetConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms679669) Windows SDK 中。  
  
##  <a name="m_vec"></a>  IConnectionPointImpl::m_vec  
 管理连接点对象和接收器之间的连接。  
  
```
CDV m_vec;
```     
  
### <a name="remarks"></a>备注  
 默认情况下，`m_vec`属于类型[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)。  
  
##  <a name="unadvise"></a>  IConnectionPointImpl::Unadvise  
 终止通过以前建立的连接[建议](#advise)。  
  
```
STDMETHOD(Unadvise)(DWORD dwCookie);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPoint::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms686608) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [类概述](../../atl/atl-class-overview.md)
