---
title: "IServiceProviderImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
dev_langs: C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 39dbab33f631ab9e0dc2b605169e92b6d12d78a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl 类
此类提供的默认实现`IServiceProvider`接口。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IServiceProviderImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|创建或访问指定的服务并返回服务的指定接口的接口指针。|  
  
## <a name="remarks"></a>备注  
 `IServiceProvider`接口定位其 GUID 指定的服务，并在服务上返回所请求的接口的接口指针。 类`IServiceProviderImpl`提供此接口的默认实现。  
  
 **IServiceProviderImpl**指定一种方法： [QueryService](#queryservice)，它创建或访问指定的服务并返回服务的指定接口的接口指针。  
  
 `IServiceProviderImpl`使用服务映射，开头[BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map)结束[END_SERVICE_MAP](service-map-macros.md#end_service_map)。  
  
 服务映射包含两个条目： [SERVICE_ENTRY](service-map-macros.md#service_entry)，表示支持的对象，指定的服务 id (SID) 和[SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)，哪些调用`QueryService`链接到另一个对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="queryservice"></a>IServiceProviderImpl::QueryService  
 创建或访问指定的服务并返回服务的指定接口的接口指针。  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 [IN]`guidService`  
 指向服务标识符 (SID)。  
  
 [IN]`riid`  
 为访问调用方的接口标识符。  
  
 [OUT]`ppvObj`  
 指向所请求的接口的间接指针。  
  
### <a name="return-value"></a>返回值  
 返回`HRESULT`值是以下之一：  
  
|返回值|含义|  
|------------------|-------------|  
|S_OK|服务已成功创建或检索。|  
|E_INVALIDARG|一个或多个参数无效。|  
|E_OUTOFMEMORY|内存不足，无法创建服务。|  
|E_UNEXPECTED|发生未知错误。|  
|E_NOINTERFACE|所请求的接口不是此服务的一部分，或者服务未知。|  
  
### <a name="remarks"></a>备注  
 `QueryService`返回指定的服务中的请求接口的间接指针。 调用方负责在不再需要释放此指针。  
  
 当调用`QueryService`，则传递两个服务标识符 ( `guidService`) 和接口标识符 ( `riid`)。 `guidService`指定访问权限，要向其中的服务和`riid`标识服务的一部分的接口。 反过来，你会收到间接指向的接口。  
  
 实现接口的对象也可能实现属于其他服务的接口。 考虑以下情况：  
  
-   这些接口的一些可能是可选的。 并非所有在服务说明中定义的接口都一定存在，或者在每个返回的对象上每个服务实现。  
  
-   与对的调用不同`QueryInterface`，传递不同的服务标识符并不一定意味着返回不同的组件对象模型 (COM) 对象。  
  
-   返回的对象可能具有不属于的服务定义的其他接口。  
  
 两个不同的服务，如 SID_SMyService 和 SID_SYourService，可以同时指定使用相同的接口，即使接口的实现可能具有共同点之间的两个服务没有任何内容。 此方法有效，因为调用`QueryService`（SID_SMyService，IID_IDispatch） 可以返回不同的对象比`QueryService`（SID_SYourService，IID_IDispatch）。 指定不同的服务标识符时，将不会假定对象标识。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)
