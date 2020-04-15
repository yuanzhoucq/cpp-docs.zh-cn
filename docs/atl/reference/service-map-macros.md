---
title: 服务映射宏
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: eb2fe41c79135a7ac2ced9bc3242b070170716b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325945"
---
# <a name="service-map-macros"></a>服务映射宏

这些宏定义服务映射和条目。

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|标记 ATL 服务映射的开头。|
|[END_SERVICE_MAP](#end_service_map)|标记 ATL 服务映射的末尾。|
|[SERVICE_ENTRY](#service_entry)|指示对象支持特定的服务 ID。|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|指示[IServiceProviderImpl：query 服务](#queryservice)链接到指定的对象。|

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="begin_service_map"></a><a name="begin_service_map"></a>BEGIN_SERVICE_MAP

标记服务映射的开头。

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>参数

*类*<br/>
[在]指定包含服务映射的类。

### <a name="remarks"></a>备注

使用服务映射在 COM 对象上实现服务提供商功能。 首先，您必须从[IServiceProviderImpl 派生](../../atl/reference/iserviceproviderimpl-class.md)您的类。 有两种类型的条目：

- [SERVICE_ENTRY](#service_entry)  指示对指定服务 ID （SID） 的支持。

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)  指示[IServiceProviderImpl：query 服务](#queryservice)链接到另一个指定的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a>END_SERVICE_MAP

标记服务映射的末尾。

```
END_SERVICE_MAP()
```

### <a name="example"></a>示例

请参阅[BEGIN_SERVICE_MAP](#begin_service_map)的示例。

## <a name="service_entry"></a><a name="service_entry"></a>SERVICE_ENTRY

指示对象支持*SID*指定的服务 ID。

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>参数

*希*<br/>
服务 ID。

### <a name="example"></a>示例

请参阅[BEGIN_SERVICE_MAP](#begin_service_map)的示例。

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

指示[IServiceProviderImpl：query 服务](#queryservice)链接到*朋克*指定的对象。

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>参数

*朋 克*<br/>
指向要链接的**I 未知**接口的指针。

### <a name="example"></a>示例

请参阅[BEGIN_SERVICE_MAP](#begin_service_map)的示例。

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

[宏](../../atl/reference/atl-macros.md)
