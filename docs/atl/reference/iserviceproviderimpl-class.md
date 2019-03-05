---
title: IServiceProviderImpl 类
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: e52c28d528e187713d2d0925fed23bd8cd4493d5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298667"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl 类

此类提供的默认实现`IServiceProvider`接口。

## <a name="syntax"></a>语法

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IServiceProviderImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|创建或访问指定的服务并返回到该服务的指定接口的接口指针。|

## <a name="remarks"></a>备注

`IServiceProvider`接口定位其 GUID 指定的服务并在服务上返回所请求的接口的接口指针。 类`IServiceProviderImpl`提供此接口的默认实现。

`IServiceProviderImpl` 指定一种方法：[QueryService](#queryservice)，它创建或访问指定的服务并返回到该服务的指定接口的接口指针。

`IServiceProviderImpl` 使用服务映射，开头[BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) ，以结束[END_SERVICE_MAP](service-map-macros.md#end_service_map)。

服务映射包含两个条目：[SERVICE_ENTRY](service-map-macros.md#service_entry)，指示该对象支持的一个指定的服务 id (SID) 和[SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)，它调用`QueryService`链接到另一个对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService

创建或访问指定的服务并返回到该服务的指定接口的接口指针。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*guidService*<br/>
[in]为服务标识符 (SID) 的指针。

*riid*<br/>
[in]调用方是访问接口的标识符。

*ppvObj*<br/>
[out]指向所请求的接口的间接指针。

### <a name="return-value"></a>返回值

返回的 HRESULT 值是以下值之一：

|返回值|含义|
|------------------|-------------|
|S_OK|该服务已成功创建或检索。|
|E_INVALIDARG|一个或多个自变量无效。|
|E_OUTOFMEMORY|内存不足，无法创建服务。|
|E_UNEXPECTED|发生未知错误。|
|E_NOINTERFACE|所请求的接口不是此服务的一部分或该服务是未知的。|

### <a name="remarks"></a>备注

`QueryService` 返回指定的服务中请求的接口的间接指针。 调用方负责在不再需要时释放此指针。

当您调用`QueryService`，则传递两个服务标识符 (*guidService*) 和接口标识符 (*riid*)。 *GuidService*指定想要访问，其中的服务和*riid*标识是服务的一部分的接口。 作为回报，您将收到间接指向的接口。

实现接口的对象也可能实现接口的其他服务的一部分。 考虑以下情况：

- 这些接口的一些可能是可选的。 在服务说明中定义的并不是所有接口都都需要出现或每个返回的对象上的服务的每个实现。

- 与对的调用不同`QueryInterface`，传递不同的服务标识符并不一定意味着返回不同的组件对象模型 (COM) 对象。

- 返回的对象可能不是服务定义的一部分的其他接口。

两个不同的服务，如 SID_SMyService 和 SID_SYourService，可以同时使用相同的接口，即使指定接口的实现可能有两个服务之间共有的任何内容。 此方法有效，因为调用`QueryService`（SID_SMyService，IID_IDispatch） 可以返回不同的对象比`QueryService`（SID_SYourService，IID_IDispatch）。 指定一个不同的服务标识符时，将不会假定对象标识。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
