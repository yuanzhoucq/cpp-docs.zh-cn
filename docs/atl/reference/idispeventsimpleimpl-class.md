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
ms.openlocfilehash: 1578518b8918f59b1da54f474e82cf899f3c76f6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285537"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 类

此类提供的实现`IDispatch`方法，而不从类型库中获取类型信息。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>参数

*nID*<br/>
源对象的唯一标识符。 当`IDispEventSimpleImpl`类的基类为复合控件，此参数使用所需的所包含控件的资源 ID。 在其他情况下，使用任意的正整数。

*T*<br/>
用户的类，该类派生自`IDispEventSimpleImpl`。

*pdiid*<br/>
指向此类实现的事件调度接口的 IID 的指针。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|建立与默认事件源的连接。|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|建立与事件源的连接。|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|断开与事件源的连接。|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|返回 E_NOTIMPL。|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|返回 E_NOTIMPL。|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|返回 E_NOTIMPL。|
|[IDispEventSimpleImpl::Invoke](#invoke)|调用事件处理程序列出在事件接收器映射。|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|断开与默认事件源的连接。|

## <a name="remarks"></a>备注

`IDispEventSimpleImpl` 提供一种而无需创建实现事件调度接口的方式，提供针对该接口上每个方法/事件的实现代码。 `IDispEventSimpleImpl` 提供的实现`IDispatch`方法。 只需提供你感兴趣处理的事件的实现。

`IDispEventSimpleImpl` 结合使用与事件路由到相应的处理程序函数在类中的事件接收器映射。 若要使用此类：

- 添加[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏为你想要处理的每个对象的每个事件的事件接收器映射。

- 通过将传递指向的提供类型信息的每个事件[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)作为每个条目的参数的结构。 在 x86 平台，`_ATL_FUNC_INFO.cc`值必须是 CC_CDECL 调用 __stdcall 方法的回调函数。

- 调用[DispEventAdvise](#dispeventadvise)之间建立连接的源对象和类的基类。

- 调用[DispEventUnadvise](#dispeventunadvise)断开连接。

您必须派生自`IDispEventSimpleImpl`(使用的值是唯一*nID*) 为每个需要处理事件的对象。 通过对一个源对象对不同的源对象，然后告知取消通知，可以重用类的基类，但可以一次处理由单个对象的源对象的最大数目受数`IDispEventSimpleImpl`基类。

`IDispEventSimplImpl` 提供与相同的功能[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)，但它不会从类型库的接口的类型信息。 向导生成代码仅基于`IDispEventImpl`，但你可以使用`IDispEventSimpleImpl`通过手动添加代码。 使用`IDispEventSimpleImpl`时你不具有一个类型库描述事件接口，或者想要避免与使用类型库相关的开销。

> [!NOTE]
> `IDispEventImpl` 并`IDispEventSimpleImpl`提供其自己的实现`IUnknown::QueryInterface`启用每个`IDispEventImpl`或`IDispEventSimpleImpl`基类，以充当不同的 COM 标识，同时仍允许在您主要的 COM 对象的直接访问类成员。

CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或 void 从在事件处理程序方法; 这些方法任何其他返回值是不受支持，而且其行为是未定义。

有关详细信息，请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="advise"></a>  IDispEventSimpleImpl::Advise

调用此方法以建立与所表示的事件源的连接*pUnk*。

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
[in]一个指向`IUnknown`事件源对象的接口。

### <a name="return-value"></a>返回值

则为 S_OK 或任何失败的 HRESULT 值。

### <a name="remarks"></a>备注

建立连接后，事件从触发*pUnk*将路由到事件接收器映射通过在类中的处理程序。

> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要区分调用此方法的范围限定您感兴趣的与特定基类的调用。

`Advise` 建立的连接与默认的事件源，它将获取由该对象的默认事件源的 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。

##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise

调用此方法以建立与所表示的事件源的连接*pUnk*。

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
[in]一个指向`IUnknown`事件源对象的接口。

*piid*<br/>
指向 IID 的事件源对象的指针。

### <a name="return-value"></a>返回值

则为 S_OK 或任何失败的 HRESULT 值。

### <a name="remarks"></a>备注

随后，从触发事件*pUnk*将路由到事件接收器映射通过在类中的处理程序。

> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要区分调用此方法的范围限定您感兴趣的与特定基类的调用。

`DispEventAdvise` 建立的连接中指定的事件源与`pdiid`。

##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise

断开与所表示的事件源的连接*pUnk*。

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
[in]一个指向`IUnknown`事件源对象的接口。

*piid*<br/>
指向 IID 的事件源对象的指针。

### <a name="return-value"></a>返回值

则为 S_OK 或任何失败的 HRESULT 值。

### <a name="remarks"></a>备注

断开连接后，事件将无法再路由到事件接收器映射中列出的处理程序函数。

> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要区分调用此方法的范围限定您感兴趣的与特定基类的调用。

`DispEventAdvise` 已建立与中指定的事件源的连接将中断`pdiid`。

##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames

此实现`IDispatch::GetIDsOfNames`返回 E_NOTIMPL。

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>备注

请参阅[IDispatch::GetIDsOfNames](/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) Windows SDK 中。

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

此实现`IDispatch::GetTypeInfo`返回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>备注

请参阅[IDispatch::GetTypeInfo](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) Windows SDK 中。

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

此实现`IDispatch::GetTypeInfoCount`返回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>备注

请参阅[IDispatch::GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) Windows SDK 中。

##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke

此实现`IDispatch::Invoke`调用事件处理程序列出在事件接收器映射。

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

请参阅[idispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)。

##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise

断开与所表示的事件源的连接*pUnk*。

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
[in]一个指向`IUnknown`事件源对象的接口。

### <a name="return-value"></a>返回值

则为 S_OK 或任何失败的 HRESULT 值。

### <a name="remarks"></a>备注

断开连接后，事件将无法再路由到事件接收器映射中列出的处理程序函数。

> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要区分调用此方法的范围限定您感兴趣的与特定基类的调用。

`Unadvise` 已建立与中指定的默认事件源的连接将中断`pdiid`。

`Unavise` 一个具有默认事件源的连接中断，它所获取的默认事件源的对象由 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。

## <a name="see-also"></a>请参阅

[_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl 类](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[类概述](../../atl/atl-class-overview.md)
