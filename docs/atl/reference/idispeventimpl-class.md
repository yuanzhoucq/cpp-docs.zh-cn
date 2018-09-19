---
title: IDispEventImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 815a276cb07a91da73acb68a32cceef4b2138325
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093828"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 类

此类提供的实现`IDispatch`方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

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
源对象的唯一标识符。 当`IDispEventImpl`类的基类为复合控件，此参数使用所需的所包含控件的资源 ID。 在其他情况下，使用任意的正整数。

*T*<br/>
用户的类，该类派生自`IDispEventImpl`。

*pdiid*<br/>
指向此类实现的事件调度接口的 IID 的指针。 此接口必须由表示类型库中定义*plibid*， *wMajor*，并*wMinor*。

*plibid*<br/>
对类型库，用于定义调度接口的指针指向的*pdiid*。 如果 **& GUID_NULL**，将从溯源事件的对象加载类型库。

*wMajor*<br/>
类型库的主版本。 默认值为 0。

*wMinor*<br/>
类型库的次版本。 默认值为 0。

*tihclass*<br/>
用于管理的类型信息的类*T*。默认值为类型的类`CComTypeInfoHolder`; 但是，您可以通过提供一种类型的类而不覆盖此模板参数`CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用于管理的类型信息的类。 默认情况下， `CComTypeInfoHolder`。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|查找指定的调度标识符的函数的索引。|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|将单个成员和一组可选的参数名称映射到一组对应的整数 Dispid。|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|检索对象的类型信息。|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|检索类型信息接口的数量。|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|检索用户定义类型的基本类型。|

## <a name="remarks"></a>备注

`IDispEventImpl` 提供一种而无需创建实现事件调度接口的方式，提供针对该接口上每个方法/事件的实现代码。 `IDispEventImpl` 提供的实现`IDispatch`方法。 只需提供你感兴趣处理的事件的实现。

`IDispEventImpl` 结合使用与事件路由到相应的处理程序函数在类中的事件接收器映射。 若要使用此类：

添加[SINK_ENTRY](composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)宏为你想要处理的每个对象的每个事件的事件接收器映射。 使用时`IDispEventImpl`作为复合控件的基类，可以调用[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)建立和断开与事件源的连接的所有项在事件都接收器映射。 在其他情况下，或者对于更强的控制，调用[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)之间建立连接的源对象和类的基类。 调用[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)断开连接。  

您必须派生自`IDispEventImpl`(使用的值是唯一*nID*) 为每个需要处理事件的对象。 通过对一个源对象对不同的源对象，然后告知取消通知，可以重用类的基类，但可以一次处理由单个对象的源对象的最大数目受数`IDispEventImpl`基类。

`IDispEventImpl` 提供与相同的功能[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)，但它获取从类型库，而不是让它作为一个指向提供有关接口的类型信息[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构。 使用`IDispEventSimpleImpl`时目前不具有一个类型库描述事件接口，或者想要避免与使用类型库相关的开销。

> [!NOTE]
> `IDispEventImpl` 并`IDispEventSimpleImpl`提供其自己的实现`IUnknown::QueryInterface`启用每个`IDispEventImpl`和`IDispEventSimpleImpl`基类，以充当不同的 COM 标识，同时仍允许在您主要的 COM 对象的直接访问类成员。

CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或 void 从在事件处理程序方法; 这些方法任何其他返回值是不受支持，而且其行为是未定义。

有关详细信息，请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId

查找指定的调度标识符的函数的索引。

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>参数

*iid*<br/>
[in]对函数的 ID 的引用。

*dispidMember*<br/>
[in]函数的调度 ID。

*lcid*<br/>
[in]区域设置上下文的函数 id。

*信息*<br/>
[in]结构，该值指示如何调用该函数。

### <a name="return-value"></a>返回值

标准的 HRESULT 值。

##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames

单个成员和一组可选的参数名称映射到一组对应的整数 Dispid，可以在后续调用使用[idispatch:: Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke)。

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>备注

请参阅[IDispatch::GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) Windows SDK 中。

##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo

检索对象的类型信息，然后可以使用该信息获取接口的类型信息。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount

检索对象提供的类型信息接口的数量（0 或 1）。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>备注

请参阅[IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) Windows SDK 中。

##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType

检索用户定义类型的基本类型。

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>参数

*PTI*<br/>
[in]一个指向[ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo)包含用户定义类型的接口。

*hrt*<br/>
[in]要检索的类型说明的句柄。

### <a name="return-value"></a>返回值

变体类型。

### <a name="remarks"></a>备注

请参阅[ITypeInfo::GetRefTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)。

##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl

构造函数。 存储类模板参数的值*plibid*， *pdiid*， *wMajor*，以及*wMinor*。

```
IDispEventImpl();
```

##  <a name="tihclass"></a>  IDispEventImpl::tihclass

此 typedef 是类模板参数的实例*tihclass*。

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>备注

默认情况下，类是`CComTypeInfoHolder`。 `CComTypeInfoHolder` 管理类的类型信息。

## <a name="see-also"></a>请参阅

[_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[类概述](../../atl/atl-class-overview.md)