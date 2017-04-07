---
title: "IConnectionPointContainerImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 81a68cae1d961f2846c1a807432f22ae92ca3b89
ms.lasthandoff: 02/24/2017

---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl 类
此类实现连接点容器，用来管理一组[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE IConnectionPointContainerImpl 
   : public IConnectionPointContainer
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IConnectionPointContainerImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|创建一个枚举器循环访问可连接对象中所支持的连接点。|  
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|检索支持指定的 IID 与连接点的接口指针。|  
  
## <a name="remarks"></a>备注  
 `IConnectionPointContainerImpl`实现连接点容器，用来管理一组[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)对象。 `IConnectionPointContainerImpl`提供客户端可以调用来检索有关可连接对象的详细信息的两种方法︰  
  
- `EnumConnectionPoints`允许客户端，以确定对象支持的传出接口。  
  
- `FindConnectionPoint`允许客户端，以确定对象是否支持特定的传出接口。  
  
 使用 ATL 中的连接点的信息，请参阅文章[连接点](../../atl/atl-connection-points.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="enumconnectionpoints"></a>IConnectionPointContainerImpl::EnumConnectionPoints  
 创建一个枚举器循环访问可连接对象中所支持的连接点。  
  
```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPointContainer::EnumConnectionPoints](http://msdn.microsoft.com/library/windows/desktop/ms682460)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="findconnectionpoint"></a>IConnectionPointContainerImpl::FindConnectionPoint  
 检索支持指定的 IID 与连接点的接口指针。  
  
```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IConnectionPointContainer::FindConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms692476)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [类概述](../../atl/atl-class-overview.md)

