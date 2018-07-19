---
title: IConnectionPointContainerImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
dev_langs:
- C++
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d70989be8e8535336c831cb59fb9422c6e2c63e0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37886227"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 类
此类实现连接点容器来管理一系列[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>参数  
 *T*  
 您的类，派生自`IConnectionPointContainerImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|创建进行循环访问，可连接对象中所支持的连接点的枚举器。|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|检索到支持指定的 IID 的连接点的接口指针。|  
  
## <a name="remarks"></a>备注  
 `IConnectionPointContainerImpl` 实现连接点容器来管理一系列[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象。 `IConnectionPointContainerImpl` 提供了客户端可以调用以检索有关可连接对象的详细信息的两个方法：  
  
- `EnumConnectionPoints` 允许客户端确定对象支持的传出接口。  
  
- `FindConnectionPoint` 允许客户端确定对象是否支持特定的输出接口。  
  
 在 ATL 中使用连接点的信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints  
 创建进行循环访问，可连接对象中所支持的连接点的枚举器。  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPointContainer::EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460) Windows SDK 中。  
  
##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint  
 检索到支持指定的 IID 的连接点的接口指针。  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [类概述](../../atl/atl-class-overview.md)
