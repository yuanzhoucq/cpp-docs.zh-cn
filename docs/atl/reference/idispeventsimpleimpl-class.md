---
title: IDispEventSimpleImpl 类
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 779e143094760c7bd868ad33f590f7fd8f004762
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329736"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 类

此类提供方法的实现，`IDispatch`而不从类型库中获取类型信息。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>参数

*nID*<br/>
源对象的唯一标识符。 当`IDispEventSimpleImpl`复合控件的基类是时，使用此参数使用所需包含控件的资源 ID。 在其他情况下，使用任意正整数。

*T*<br/>
用户的类，派生自`IDispEventSimpleImpl`。

*皮迪德*<br/>
指向此类实现的事件不接口的 IID 的指针。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IDispEvent 简单：：建议](#advise)|建立与默认事件源的连接。|
|[IDispEvent 简单：:Dispevent建议](#dispeventadvise)|建立与事件源的连接。|
|[IDispEvent 简单：:Dispevent 无建议](#dispeventunadvise)|断开与事件源的连接。|
|[IDispevent 简单页： ：获取名称](#getidsofnames)|返回 E_NOTIMPL。|
|[IDispevent 简单：：获取类型信息](#gettypeinfo)|返回 E_NOTIMPL。|
|[IDispevent 简单：：获取类型信息计数](#gettypeinfocount)|返回 E_NOTIMPL。|
|[IDispevent 简单：：调用](#invoke)|调用事件接收器映射中列出的事件处理程序。|
|[IDispEvent 简单：：无建议](#unadvise)|断开与默认事件源的连接。|

## <a name="remarks"></a>备注

`IDispEventSimpleImpl`提供了一种实现事件接口的方法，而无需为该接口上的每个方法/事件提供实现代码。 `IDispEventSimpleImpl`提供了方法的`IDispatch`实现。 您只需为您感兴趣的事件提供实现。

`IDispEventSimpleImpl`与类中的事件接收器映射结合使用，将事件路由到相应的处理程序函数。 要使用此类：

- 向要处理的每个对象上每个事件的事件向事件接收器映射添加[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏。

- 通过将指向[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构的指针作为参数传递给每个条目，从而为每个事件提供类型信息。 在 x86 平台上，`_ATL_FUNC_INFO.cc`必须使用__stdcall回调函数调用方法CC_CDECL该值。

- 调用[DispEvent 建议](#dispeventadvise)以建立源对象和基类之间的连接。

- 致电[DispEventUn 建议](#dispeventunadvise)断开连接。

您必须从`IDispEventSimpleImpl`（使用*nID*的唯一值 ）派生出需要为其处理事件的每个对象。 可以通过对一个源对象取消建议来重用基类，然后针对不同的源对象提供建议，但一次由单个对象可以处理的最大源对象数受基类数`IDispEventSimpleImpl`的限制。

`IDispEventSimplImpl`提供与[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)相同的功能，只不过它不从类型库中获取有关接口的类型信息。 向导仅基于`IDispEventImpl`生成代码，但可以通过手动添加代码来`IDispEventSimpleImpl`使用。 当您`IDispEventSimpleImpl`没有描述事件接口的类型库或希望避免与使用类型库关联的开销时，请使用。

> [!NOTE]
> `IDispEventImpl`并提供`IDispEventSimpleImpl`它们自己的实现，`IUnknown::QueryInterface`使每个`IDispEventImpl`或`IDispEventSimpleImpl`基类充当单独的 COM 标识，同时仍然允许直接访问主 COM 对象中的类成员。

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中 HRESULT 类型的返回值或 void;任何其他返回值不受支持，其行为未定义。

有关详细信息，请参阅支持[IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEvent 简单：：建议

调用此方法以建立与*pUnk*表示的事件源的连接。

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]指向事件源对象的`IUnknown`接口的指针。

### <a name="return-value"></a>返回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

建立连接后，从*pUnk*触发的事件将通过事件接收器映射路由到类中的处理程序。

> [!NOTE]
> 如果类派生自多个`IDispEventSimpleImpl`类，则需要通过将调用与感兴趣的特定基类进行范围界定来消除对此方法的歧义调用。

`Advise`建立与默认事件源的连接，它获取由[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)确定的对象的默认事件源的 IID。

## <a name="idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEvent 简单：:Dispevent建议

调用此方法以建立与*pUnk*表示的事件源的连接。

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]指向事件源对象的`IUnknown`接口的指针。

*皮伊德*<br/>
指向事件源对象的 IID 的指针。

### <a name="return-value"></a>返回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

随后，从*pUnk*触发的事件将通过事件接收器映射路由到类中的处理程序。

> [!NOTE]
> 如果类派生自多个`IDispEventSimpleImpl`类，则需要通过将调用与感兴趣的特定基类进行范围界定来消除对此方法的歧义调用。

`DispEventAdvise`建立与 中`pdiid`指定的事件源的连接。

## <a name="idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEvent 简单：:Dispevent 无建议

断开与*pUnk*表示的事件源的连接。

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]指向事件源对象的`IUnknown`接口的指针。

*皮伊德*<br/>
指向事件源对象的 IID 的指针。

### <a name="return-value"></a>返回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

连接断开后，事件将不再路由到事件接收器映射中列出的处理程序函数。

> [!NOTE]
> 如果类派生自多个`IDispEventSimpleImpl`类，则需要通过将调用与感兴趣的特定基类进行范围界定来消除对此方法的歧义调用。

`DispEventAdvise`中断与 中`pdiid`指定的事件源建立的连接。

## <a name="idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispevent 简单页： ：获取名称

返回的`IDispatch::GetIDsOfNames`这种实现E_NOTIMPL。

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>备注

请参阅[IDispatch：获取](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames)Windows SDK 中的名称。

## <a name="idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispevent 简单：：获取类型信息

返回的`IDispatch::GetTypeInfo`这种实现E_NOTIMPL。

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>备注

请参阅[IDispatch：在](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo)Windows SDK 中获取类型信息。

## <a name="idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispevent 简单：：获取类型信息计数

返回的`IDispatch::GetTypeInfoCount`这种实现E_NOTIMPL。

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>备注

请参阅 IDispatch：在 Windows SDK 中[获取类型信息计数](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。

## <a name="idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispevent 简单：：调用

此实现`IDispatch::Invoke`调用事件接收器映射中列出的事件处理程序。

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>备注

请参阅[IDispatch：：调用](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

## <a name="idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEvent 简单：：无建议

断开与*pUnk*表示的事件源的连接。

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*朋 克*<br/>
[在]指向事件源对象的`IUnknown`接口的指针。

### <a name="return-value"></a>返回值

S_OK或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

连接断开后，事件将不再路由到事件接收器映射中列出的处理程序函数。

> [!NOTE]
> 如果类派生自多个`IDispEventSimpleImpl`类，则需要通过将调用与感兴趣的特定基类进行范围界定来消除对此方法的歧义调用。

`Unadvise`中断与 中`pdiid`指定的默认事件源建立的连接。

`Unavise`断开与默认事件源的连接，它获取由[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)确定的对象的默认事件源的 IID。

## <a name="see-also"></a>另请参阅

[_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl 类](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[类概述](../../atl/atl-class-overview.md)
