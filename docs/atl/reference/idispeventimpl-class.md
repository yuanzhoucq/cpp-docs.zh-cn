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
ms.openlocfilehash: fa6e9f972accd0115d9f1e3248bd97ddde0c3c63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329757"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 类

此类提供方法的`IDispatch`实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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
源对象的唯一标识符。 当`IDispEventImpl`复合控件的基类是时，使用此参数使用所需包含控件的资源 ID。 在其他情况下，使用任意正整数。

*T*<br/>
用户的类，派生自`IDispEventImpl`。

*皮迪德*<br/>
指向此类实现的事件不接口的 IID 的指针。 此接口必须在类型库中定义，该类型库由*plibid、wMajor*和*wMinor*表示。 *wMajor*

*普利比德*<br/>
指向类型库的指针，用于定义*pdiid*指向的调度接口。 如果 **&GUID_NULL，** 类型库将从源事件的对象加载。

*w 主要*<br/>
类型库的主版本。 默认值为 0。

*wMinor*<br/>
类型库的次版本。 默认值为 0。

*提赫班*<br/>
用于管理*T*的类型信息的类。默认值是类型的`CComTypeInfoHolder`类。但是，您可以通过提供 以外的`CComTypeInfoHolder`类型的类来覆盖此模板参数。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[IDispEventImpl：：_tihclass](../../atl/reference/idispeventimpl-class.md)|用于管理类型信息的类。 默认为 `CComTypeInfoHolder`。|

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[IDispEventImpl：：IDispeventImpl](#idispeventimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IDispeventimpl：：从Id获取Funcinfo](#getfuncinfofromid)|查找指定调度标识符的函数索引。|
|[IDispeventimpl：：获取名称的 Idds](#getidsofnames)|将单个成员和一组可选的参数名称映射到相应的整数 DISPID。|
|[IDispEventImpl：：获取类型信息](#gettypeinfo)|检索对象的类型信息。|
|[IDispEventImpl：：获取类型信息计数](#gettypeinfocount)|检索类型信息接口的数量。|
|[IDispeventImpl：：获取用户定义类型](#getuserdefinedtype)|检索用户定义类型的基本类型。|

## <a name="remarks"></a>备注

`IDispEventImpl`提供了一种实现事件接口的方法，而无需为该接口上的每个方法/事件提供实现代码。 `IDispEventImpl`提供了方法的`IDispatch`实现。 您只需为您感兴趣的事件提供实现。

`IDispEventImpl`与类中的事件接收器映射结合使用，将事件路由到相应的处理程序函数。 要使用此类：

向要处理的每个对象上每个事件的事件向事件接收器映射添加[SINK_ENTRY](composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)宏。 当用作`IDispEventImpl`复合控件的基类时，可以调用[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)建立和断开事件接收器映射中所有条目的事件源的连接。 在其他情况下，或为了进行更大的控制，请致电[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)以建立源对象和基类之间的连接。 致电[DispEventUn 建议](idispeventsimpleimpl-class.md#dispeventunadvise)断开连接。

您必须从`IDispEventImpl`（使用*nID*的唯一值 ）派生出需要为其处理事件的每个对象。 可以通过对一个源对象取消建议来重用基类，然后针对不同的源对象提供建议，但一次由单个对象可以处理的最大源对象数受基类数`IDispEventImpl`的限制。

`IDispEventImpl`提供与[IDispEventSimple](../../atl/reference/idispeventsimpleimpl-class.md)相同的功能，只不过它从类型库中获取有关接口的类型信息，而不是将其作为指向[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构的指针提供。 当您`IDispEventSimpleImpl`没有描述事件接口的类型库或希望避免与使用类型库关联的开销时，请使用。

> [!NOTE]
> `IDispEventImpl`并提供`IDispEventSimpleImpl`它们自己的实现，`IUnknown::QueryInterface`使每个`IDispEventImpl`类和`IDispEventSimpleImpl`基类充当单独的 COM 标识，同时仍然允许直接访问主 COM 对象中的类成员。

ActiveX 事件接收器的 CE ATL 实现仅支持事件处理程序方法中 HRESULT 类型的返回值或 void;任何其他返回值不受支持，其行为未定义。

有关详细信息，请参阅支持[IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_IDispEvent`

`_IDispEventLocator`

[IDispevent 简单](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispeventimpl：：从Id获取Funcinfo

查找指定调度标识符的函数索引。

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>参数

*Iid*<br/>
[在]对函数 ID 的引用。

*不一名会员*<br/>
[在]函数的调度 ID。

*Lcid*<br/>
[在]函数 ID 的区域设置上下文。

info**<br/>
[在]指示如何调用函数的结构。

### <a name="return-value"></a>返回值

标准 HRESULT 值。

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispeventimpl：：获取名称的 Idds

将单个成员和一组可选的参数名称映射到相应的整数 DISPID，可用于后续调用[IDispatch：：：invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)。

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>备注

请参阅[IDispatch：获取](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames)Windows SDK 中的名称。

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl：：获取类型信息

检索对象的类型信息，然后可以使用该信息获取接口的类型信息。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl：：获取类型信息计数

检索对象提供的类型信息接口的数量（0 或 1）。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>备注

请参阅 IDispatch：在 Windows SDK 中[获取类型信息计数](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)。

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispeventImpl：：获取用户定义类型

检索用户定义类型的基本类型。

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>参数

*Pti*<br/>
[在]指向包含用户定义类型的[ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo)接口的指针。

*Hrt*<br/>
[在]要检索的类型说明的句柄。

### <a name="return-value"></a>返回值

变体的类型。

### <a name="remarks"></a>备注

请参阅[ITypeInfo：：获取参考类型信息](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)。

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl：：IDispeventImpl

构造函数。 存储类模板参数*plibid、pdiid、wMajor*和*wMajor* *wMinor 的值*。 *plibid*

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl：：tihclass

此 typedef 是类模板参数*tihclass*的实例。

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>备注

默认情况下，类为`CComTypeInfoHolder`。 `CComTypeInfoHolder`管理类的类型信息。

## <a name="see-also"></a>另请参阅

[_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[类概述](../../atl/atl-class-overview.md)
