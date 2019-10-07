---
title: IDispEventImpl 类
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: e82a397b6d2abb66f773908c72a287c979e5ae1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495923"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 类

此类提供`IDispatch`方法的实现。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>参数

*nID*<br/>
源对象的唯一标识符。 当`IDispEventImpl`是复合控件的基类时, 为此参数使用所需包含控件的资源 ID。 在其他情况下, 请使用任意正整数。

*T*<br/>
用户的类, 它派生自`IDispEventImpl`。

*pdiid*<br/>
指向由此类实现的事件调度接口的 IID 的指针。 此接口必须在由*plibid*、 *wMajor*和*wMinor*表示的类型库中定义。

*plibid*<br/>
一个指针, 指向用于定义*pdiid*指向的调度接口的类型库。 如果 **&AMP; GUID_NULL**, 将从获得事件的对象中加载类型库。

*wMajor*<br/>
类型库的主版本。 默认值为 0。

*wMinor*<br/>
类型库的次版本。 默认值为 0。

*tihclass*<br/>
用于管理*T*的类型信息的类。默认值为类型`CComTypeInfoHolder`的类; 但是, 可以通过提供除之外`CComTypeInfoHolder`的类型的类来重写此模板参数。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|name|描述|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用于管理类型信息的类。 默认情况下`CComTypeInfoHolder`,。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|查找指定调度标识符的函数索引。|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|将一个成员和一组可选的参数名称映射到一组相应的整数 Dispid。|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|检索对象的类型信息。|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|检索类型信息接口的数量。|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|检索用户定义类型的基本类型。|

## <a name="remarks"></a>备注

`IDispEventImpl`提供实现事件调度接口的方法, 无需为该接口上的每个方法/事件提供实现代码。 `IDispEventImpl`提供`IDispatch`方法的实现。 你只需为你感兴趣处理的事件提供实现。

`IDispEventImpl`与类中的事件接收器映射结合使用, 以将事件路由到适当的处理程序函数。 使用此类:

向要处理的每个对象上的每个事件的事件接收器映射添加[SINK_ENTRY](composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)宏。 使用`IDispEventImpl`作为复合控件的基类时, 可以调用[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)来建立和中断与事件接收器映射中所有项的事件源的连接。 在其他情况下, 或者为了更好地控制, 请调用[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)以建立源对象与基类之间的连接。 调用[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)断开连接。

对于需要处理事件`IDispEventImpl`的每个对象, 必须从 (为*nID*使用唯一值) 派生。 您可以通过 unadvising 对一个源对象重复使用基类, 然后针对不同的源对象进行通知, 但是单个对象可以同时处理的最大源对象数受`IDispEventImpl`基类的数目限制。

`IDispEventImpl`提供与[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)相同的功能, 不同之处在于从类型库获取有关接口的类型信息, 而不是将其作为指向[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构的指针提供。 如果`IDispEventSimpleImpl`你没有用于描述事件接口的类型库, 或者想要避免使用类型库关联的开销, 请使用。

> [!NOTE]
> `IDispEventImpl`和`IDispEventSimpleImpl`提供自己的`IUnknown::QueryInterface`实现来使每`IDispEventImpl`个`IDispEventSimpleImpl`和基类充当单独的 com 标识, 同时仍然允许直接访问主 com 对象中的类成员。

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中类型为 HRESULT 或 void 的返回值;不支持任何其他返回值, 并且其行为不确定。

有关详细信息, 请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="getfuncinfofromid"></a>IDispEventImpl:: GetFuncInfoFromId

查找指定调度标识符的函数索引。

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>参数

*iid*<br/>
中对函数 ID 的引用。

*dispidMember*<br/>
中函数的调度 ID。

*lcid*<br/>
中函数 ID 的区域设置上下文。

info<br/>
中指示如何调用函数的结构。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="getidsofnames"></a>IDispEventImpl:: Idispatch.getidsofnames

将一个成员和一组可选的自变量名称映射到一组相应的整数 Dispid, 后者可用于后续调用[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDispatch:: idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 。

##  <a name="gettypeinfo"></a>IDispEventImpl:: GetTypeInfo

检索对象的类型信息，然后可以使用该信息获取接口的类型信息。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

##  <a name="gettypeinfocount"></a>IDispEventImpl:: GetTypeInfoCount

检索对象提供的类型信息接口的数量（0 或 1）。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 。

##  <a name="getuserdefinedtype"></a>IDispEventImpl:: GetUserDefinedType

检索用户定义类型的基本类型。

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>参数

*pTI*<br/>
中指向包含用户定义类型的[ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo)接口的指针。

*hrt*<br/>
中要检索的类型说明的句柄。

### <a name="return-value"></a>返回值

变体的类型。

### <a name="remarks"></a>备注

请参阅[ITypeInfo:: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)。

##  <a name="idispeventimpl"></a>IDispEventImpl:: IDispEventImpl

构造函数。 存储类模板参数*plibid*、 *pdiid*、 *wMajor*和*wMinor*的值。

```
IDispEventImpl();
```

##  <a name="tihclass"></a>IDispEventImpl:: tihclass

此 typedef 是类模板参数*tihclass*的实例。

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>备注

默认情况下, 类为`CComTypeInfoHolder`。 `CComTypeInfoHolder`管理类的类型信息。

## <a name="see-also"></a>请参阅

[_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[类概述](../../atl/atl-class-overview.md)
