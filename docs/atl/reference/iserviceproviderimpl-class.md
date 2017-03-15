---
title: "IServiceProviderImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IServiceProviderImpl<T>
- ATL.IServiceProviderImpl<T>
- ATL.IServiceProviderImpl
- ATL::IServiceProviderImpl
- IServiceProviderImpl
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
caps.latest.revision: 22
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
ms.openlocfilehash: 69a59fe23b3ca787dee86b1bbdc6775a44903f91
ms.lasthandoff: 02/24/2017

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
 您的类，派生自`IServiceProviderImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|创建或访问指定的服务并返回服务的指定接口的接口指针。|  
  
## <a name="remarks"></a>备注  
 `IServiceProvider`接口定位通过 GUID 指定的服务，并在服务上返回所请求的接口的接口指针。 类`IServiceProviderImpl`提供此接口的默认实现。  
  
 **IServiceProviderImpl**指定一种方法︰ [QueryService](#queryservice)，它创建或访问指定的服务并返回服务的指定接口的接口指针。  
  
 `IServiceProviderImpl`使用服务映射中，从开始[BEGIN_SERVICE_MAP](http://msdn.microsoft.com/library/3c6ae156-8776-4588-8227-2d234daec236)结束[END_SERVICE_MAP](http://msdn.microsoft.com/library/9a35d02a-014c-413a-bb0b-bcca11ab45a6)。  
  
 服务映射中包含两个条目︰ [SERVICE_ENTRY](http://msdn.microsoft.com/library/e65ff9cc-15e8-41cf-b686-f99eb6686ca9)，指示该对象，支持指定的服务 id (SID) 和[SERVICE_ENTRY_CHAIN](http://msdn.microsoft.com/library/09be4ce4-3ccd-4ff2-a95e-a9d5275354c1)，后者调用`QueryService`链接到另一个对象。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-namequeryservicea--iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderImpl::QueryService  
 创建或访问指定的服务并返回服务的指定接口的接口指针。  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>参数  
 [IN]`guidService`  
 为服务标识符 (SID) 的指针。  
  
 [IN]`riid`  
 调用方是访问接口的标识符。  
  
 [OUT]`ppvObj`  
 指向所请求的接口的间接指针。  
  
### <a name="return-value"></a>返回值  
 返回`HRESULT`值是以下之一︰  
  
|返回值|含义|  
|------------------|-------------|  
|S_OK|该服务已成功创建或检索。|  
|E_INVALIDARG|一个或多个参数无效。|  
|E_OUTOFMEMORY|内存不足，无法创建服务。|  
|E_UNEXPECTED|发生未知错误。|  
|E_NOINTERFACE|所请求的接口不是此服务的一部分，或者服务未知。|  
  
### <a name="remarks"></a>备注  
 `QueryService`返回对指定服务中请求的接口的间接指针。 调用方负责在不再需要释放此指针。  
  
 当您调用`QueryService`，传递两个服务标识符 ( `guidService`) 和接口标识符 ( `riid`)。 `guidService`指定访问权限，要向其中的服务和`riid`标识是服务的一部分的接口。 作为回报，您将收到间接指向的接口。  
  
 实现该接口的对象也可能实现属于其他服务的接口。 考虑以下情况：  
  
-   这些接口的一些可能是可选的。 并非所有在服务说明中定义的接口都需要出现或每个返回的对象上每个服务实现。  
  
-   与不同的是对调用`QueryInterface`，传递不同的服务标识符并不一定意味着将返回一个不同的组件对象模型 (COM) 对象。  
  
-   返回的对象可能具有不是服务定义的一部分的其他接口。  
  
 两个不同的服务，如 SID_SMyService 和 SID_SYourService，可以同时指定使用同一个接口，即使接口的实现可能具有两个服务之间的共同点没有任何内容。 此方法有效，因为调用`QueryService`（SID_SMyService、 IID_IDispatch） 可以返回不同的对象比`QueryService`（SID_SYourService、 IID_IDispatch）。 指定一个不同的服务标识符时，将不会假定对象标识。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

