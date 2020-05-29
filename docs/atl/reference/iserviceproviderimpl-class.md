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
ms.openlocfilehash: ef0ee4f77441cb8d19ea2d6dcada1fed9faf2782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329418"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl 类

此类提供接口的`IServiceProvider`默认实现。

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

|名称|说明|
|----------|-----------------|
|[IServiceProviderimpl：query服务](#queryservice)|创建或访问指定的服务，并返回指向服务指定接口的接口指针。|

## <a name="remarks"></a>备注

接口`IServiceProvider`定位由其 GUID 指定的服务，并返回服务上请求的接口的接口指针。 类`IServiceProviderImpl`提供此接口的默认实现。

`IServiceProviderImpl`指定一种方法[：QueryService](#queryservice)，它创建或访问指定的服务，并返回指向服务指定接口的接口指针。

`IServiceProviderImpl`使用服务映射，从[BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map)开始，以[END_SERVICE_MAP](service-map-macros.md#end_service_map)结尾。

服务映射包含两个条目[：SERVICE_ENTRY](service-map-macros.md#service_entry)，它指示对象支持的指定服务 ID （SID），SERVICE_ENTRY_CHAIN 调用[SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain)`QueryService`链接到另一个对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderimpl：query服务

创建或访问指定的服务，并返回指向服务指定接口的接口指针。

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>参数

*吉德服务*<br/>
[在]指向服务标识符 （SID） 的指针。

*riid*<br/>
[在]调用方要访问的接口的标识符。

*普夫奥比*<br/>
[出]间接指针指向请求的接口。

### <a name="return-value"></a>返回值

返回的 HRESULT 值为以下值之一：

|返回值|含义|
|------------------|-------------|
|S_OK|已成功创建或检索服务。|
|E_INVALIDARG|一个或多个自变量无效。|
|E_OUTOFMEMORY|内存不足以创建服务。|
|E_UNEXPECTED|发生未知错误。|
|E_NOINTERFACE|请求的接口不是此服务的一部分，或者服务未知。|

### <a name="remarks"></a>备注

`QueryService`返回指向指定服务中请求的接口的间接指针。 调用方负责在不再需要此指针时释放它。

调用 时`QueryService`，将传递服务标识符 *（guidService*） 和接口标识符 *（riid*）。 *guidService*指定要访问的服务 *，riid*标识属于服务的接口。 作为回报，您将收到指向接口的间接指针。

实现接口的对象还可能实现属于其他服务的接口。 请注意以下几点：

- 其中一些接口可能是可选的。 服务描述中定义的接口并非都一定存在于服务的每个实现或每个返回的对象上。

- 与调用`QueryInterface`不同，传递不同的服务标识符并不一定意味着返回不同的组件对象模型 （COM） 对象。

- 返回的对象可能具有不属于服务定义的其他接口。

两个不同的服务（如SID_SMyService和SID_SYourService）都可以指定同一接口的使用，即使该接口的实现在两个服务之间可能没有任何共同之处。 这工作正常，因为对`QueryService`（SID_SMyService、IID_IDispatch） 的调用可以返回与`QueryService`（SID_SYourService、IID_IDispatch） 不同的对象。 指定其他服务标识符时，不会假定对象标识。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
