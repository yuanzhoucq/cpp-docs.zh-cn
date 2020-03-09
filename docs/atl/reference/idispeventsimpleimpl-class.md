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
ms.openlocfilehash: 3ceb436e4f20a17ecd086fb68f9c1cfdcbe0be3e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864715"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 类

此类提供 `IDispatch` 方法的实现，而不从类型库获取类型信息。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>参数

*nID*<br/>
源对象的唯一标识符。 如果 `IDispEventSimpleImpl` 是复合控件的基类，请使用此参数所需的所含控件的资源 ID。 在其他情况下，请使用任意正整数。

*T*<br/>
用户的类，它派生自 `IDispEventSimpleImpl`。

*pdiid*<br/>
指向由此类实现的事件调度接口的 IID 的指针。

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IDispEventSimpleImpl：： Advise](#advise)|建立与默认事件源的连接。|
|[IDispEventSimpleImpl：:D ispEventAdvise](#dispeventadvise)|建立与事件源的连接。|
|[IDispEventSimpleImpl：:D ispEventUnadvise](#dispeventunadvise)|中断与事件源的连接。|
|[IDispEventSimpleImpl：： Idispatch.getidsofnames](#getidsofnames)|返回 E_NOTIMPL。|
|[IDispEventSimpleImpl：： GetTypeInfo](#gettypeinfo)|返回 E_NOTIMPL。|
|[IDispEventSimpleImpl：： GetTypeInfoCount](#gettypeinfocount)|返回 E_NOTIMPL。|
|[IDispEventSimpleImpl：： Invoke](#invoke)|调用事件接收器映射中列出的事件处理程序。|
|[IDispEventSimpleImpl：： Unadvise](#unadvise)|断开与默认事件源的连接。|

## <a name="remarks"></a>备注

`IDispEventSimpleImpl` 提供了一种实现事件调度接口的方法，无需为该接口上的每个方法/事件提供实现代码。 `IDispEventSimpleImpl` 提供 `IDispatch` 方法的实现。 你只需为你感兴趣处理的事件提供实现。

`IDispEventSimpleImpl` 与类中的事件接收器映射结合使用，以将事件路由到适当的处理程序函数。 使用此类：

- 将[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏添加到要处理的每个对象上的事件接收器映射。

- 提供每个事件的类型信息，方法是将指向[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构的指针作为参数传递给每个项。 在 x86 平台上，`_ATL_FUNC_INFO.cc` 值必须与 __stdcall 的调用方法的回调函数 CC_CDECL。

- 调用[DispEventAdvise](#dispeventadvise) ，以在源对象与基类之间建立连接。

- 调用[DispEventUnadvise](#dispeventunadvise)断开连接。

对于需要处理事件的每个对象，必须从 `IDispEventSimpleImpl` （为*nID*使用唯一值）派生。 您可以通过 unadvising 对一个源对象重复使用基类，然后针对不同的源对象进行通知，但是单个对象可以同时处理的最大源对象数受 `IDispEventSimpleImpl` 基类的数目的限制。

`IDispEventSimplImpl` 提供与[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)相同的功能，只不过它不会从类型库获取有关接口的类型信息。 向导仅基于 `IDispEventImpl`生成代码，但您可以通过手动添加代码来使用 `IDispEventSimpleImpl`。 如果你没有描述事件接口的类型库，或者想要避免使用类型库关联的开销，请使用 `IDispEventSimpleImpl`。

> [!NOTE]
> `IDispEventImpl` 和 `IDispEventSimpleImpl` 提供自己的实现 `IUnknown::QueryInterface`，使每个 `IDispEventImpl` 或 `IDispEventSimpleImpl` 基类充当单独的 COM 标识，同时仍然允许直接访问主 COM 对象中的类成员。

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中类型为 HRESULT 或 void 的返回值;不支持任何其他返回值，并且其行为不确定。

有关详细信息，请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="advise"></a>IDispEventSimpleImpl：： Advise

调用此方法以建立与*pUnk*所表示的事件源的连接。

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
中指向事件源对象的 `IUnknown` 接口的指针。

### <a name="return-value"></a>返回值

S_OK 或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

建立连接后，从*pUnk*激发的事件将通过事件接收器映射路由到您的类中的处理程序。

> [!NOTE]
>  如果类派生自多个 `IDispEventSimpleImpl` 类，则需要通过将调用的范围限定为你感兴趣的特定基类来消除对此方法的调用。

`Advise` 将建立与默认事件源的连接，它将获取由[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)确定的对象的默认事件源的 IID。

##  <a name="dispeventadvise"></a>IDispEventSimpleImpl：:D ispEventAdvise

调用此方法以建立与*pUnk*所表示的事件源的连接。

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
中指向事件源对象的 `IUnknown` 接口的指针。

*piid*<br/>
指向事件源对象的 IID 的指针。

### <a name="return-value"></a>返回值

S_OK 或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

然后，从*pUnk*激发的事件将通过事件接收器映射路由到类中的处理程序。

> [!NOTE]
>  如果类派生自多个 `IDispEventSimpleImpl` 类，则需要通过将调用的范围限定为你感兴趣的特定基类来消除对此方法的调用。

`DispEventAdvise` 与 `pdiid`中指定的事件源建立连接。

##  <a name="dispeventunadvise"></a>IDispEventSimpleImpl：:D ispEventUnadvise

断开与*pUnk*所表示的事件源的连接。

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
中指向事件源对象的 `IUnknown` 接口的指针。

*piid*<br/>
指向事件源对象的 IID 的指针。

### <a name="return-value"></a>返回值

S_OK 或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

连接中断后，事件将不再路由到事件接收器映射中列出的处理程序函数。

> [!NOTE]
>  如果类派生自多个 `IDispEventSimpleImpl` 类，则需要通过将调用的范围限定为你感兴趣的特定基类来消除对此方法的调用。

`DispEventAdvise` 中断使用 `pdiid`中指定的事件源建立的连接。

##  <a name="getidsofnames"></a>IDispEventSimpleImpl：： Idispatch.getidsofnames

此 `IDispatch::GetIDsOfNames` 的实现返回 E_NOTIMPL。

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDispatch：： idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 。

##  <a name="gettypeinfo"></a>IDispEventSimpleImpl：： GetTypeInfo

此 `IDispatch::GetTypeInfo` 的实现返回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDispatch：： GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 。

##  <a name="gettypeinfocount"></a>IDispEventSimpleImpl：： GetTypeInfoCount

此 `IDispatch::GetTypeInfoCount` 的实现返回 E_NOTIMPL。

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDispatch：： GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 。

##  <a name="invoke"></a>IDispEventSimpleImpl：： Invoke

此 `IDispatch::Invoke` 实现调用事件接收器映射中列出的事件处理程序。

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

请参阅[IDispatch：： Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

##  <a name="unadvise"></a>IDispEventSimpleImpl：： Unadvise

断开与*pUnk*所表示的事件源的连接。

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>参数

*pUnk*<br/>
中指向事件源对象的 `IUnknown` 接口的指针。

### <a name="return-value"></a>返回值

S_OK 或任何故障 HRESULT 值。

### <a name="remarks"></a>备注

连接中断后，事件将不再路由到事件接收器映射中列出的处理程序函数。

> [!NOTE]
>  如果类派生自多个 `IDispEventSimpleImpl` 类，则需要通过将调用的范围限定为你感兴趣的特定基类来消除对此方法的调用。

`Unadvise` 中断使用 `pdiid`中指定的默认事件源建立的连接。

`Unavise` 中断与默认事件源的连接，它将获取由[AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)确定的对象的默认事件源的 IID。

## <a name="see-also"></a>另请参阅

[_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventImpl 类](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[类概述](../../atl/atl-class-overview.md)
