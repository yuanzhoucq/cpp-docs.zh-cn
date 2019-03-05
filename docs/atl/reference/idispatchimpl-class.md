---
title: IDispatchImpl 类
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: bf6b416337c58f5e9b8a62dda841615412573666
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293207"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 类

提供一个默认实现`IDispatch`双重接口的一部分。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>参数

*T*<br/>
[in]双重接口。

*piid*<br/>
[in]指向 IID *T*。

*plibid*<br/>
[in]一个指向包含有关接口的信息的类型库的 LIBID。 默认情况下，传递服务器级类型库。

*wMajor*<br/>
[in]类型库的主要版本。 默认情况下，值为 1。

*wMinor*<br/>
[in]类型库的次版本。 默认情况下，值为 0。

*tihclass*<br/>
[in]用于管理的类型信息的类*T*。默认情况下，该值为 `CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|构造函数。 调用`AddRef`管理双重接口的类型信息的受保护的成员变量上。 析构函数调用 `Release`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|将一组名称映射为对应的一组调度标识符。|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|检索双重接口的类型信息。|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|确定是否存在可用于双重接口的类型信息。|
|[IDispatchImpl::Invoke](#invoke)|可以访问的方法和属性公开的双重接口。|

## <a name="remarks"></a>备注

`IDispatchImpl` 提供一个默认实现`IDispatch`对象上的任何双接口的一部分。 双重接口派生`IDispatch`，并使用只有自动化兼容类型。 调度接口，如双重接口支持早期绑定和后期绑定;但是，双重接口还支持 vtable 绑定。

下面的示例演示的典型实现`IDispatchImpl`。

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

默认情况下`IDispatchImpl`类会查找的类型信息*T*注册表中。 若要实现取消注册的接口，可以使用`IDispatchImpl`类，而使用预定义的版本号访问注册表。 如果您创建`IDispatchImpl`对象，它具有的值为 0xFFFF *wMajor*和 0xFFFF 的值作为*wMinor*，则`IDispatchImpl`类从.dll 文件而不是检索类型库注册表。

`IDispatchImpl` 包含类型的静态成员`CComTypeInfoHolder`管理双重接口的类型信息。 如果有多个对象的实现相同的双重接口，只有一个实例`CComTypeInfoHolder`使用。

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`IDispatchImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames

将一组名称映射为对应的一组调度标识符。

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>备注

请参阅[IDispatch::GetIDsOfNames](/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) Windows SDK 中。

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

检索双重接口的类型信息。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

请参阅[IDispatch::GetTypeInfo](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) Windows SDK 中。

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

确定是否存在可用于双重接口的类型信息。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>备注

请参阅`IDispatch::GetTypeInfoCount`Windows SDK 中。

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

构造函数。 调用`AddRef`管理双重接口的类型信息的受保护的成员变量上。 析构函数调用 `Release`。

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

可以访问的方法和属性公开的双重接口。

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>备注

请参阅[idispatch:: Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) Windows SDK 中。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
