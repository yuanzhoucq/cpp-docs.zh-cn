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
ms.openlocfilehash: 3b3899a0c4a49aa7fb1bd82af330f5f1cc7329c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329797"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 类

为双接口部分`IDispatch`提供默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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
[在]双接口。

*皮伊德*<br/>
[在]指向*T*的 IID 的指针。

*普利比德*<br/>
[在]指向类型库 LIBID 的指针，其中包含有关接口的信息。 默认情况下，传递服务器级类型库。

*w 主要*<br/>
[在]类型库的主要版本。 默认情况下，该值为 1。

*wMinor*<br/>
[在]类型库的次要版本。 默认情况下，值为 0。

*提赫班*<br/>
[在]用于管理*T*的类型信息的类。默认情况下，该值为`CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[I 调度：：I 调度](#idispatchimpl)|构造函数。 调用`AddRef`管理双接口类型信息的受保护成员变量。 析构函数调用 `Release`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IDispatchimpl：获取名称](#getidsofnames)|将一组名称映射为对应的一组调度标识符。|
|[IDispatchImpl：：获取类型信息](#gettypeinfo)|检索双接口的类型信息。|
|[IDispatchImpl：：获取类型信息计数](#gettypeinfocount)|确定双接口是否有可用的类型信息。|
|[IDispatchImpl：：调用](#invoke)|提供对双接口公开的方法和属性的访问。|

## <a name="remarks"></a>备注

`IDispatchImpl`为对象上`IDispatch`任何双接口的一部分提供默认实现。 双接口派生自`IDispatch`并仅使用与自动化兼容的类型。 与接口一样，双接口支持早期绑定和后期绑定;但是，双接口还支持 vtable 绑定。

下面的示例显示了`IDispatchImpl`的典型实现。

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

默认情况下，`IDispatchImpl`类在注册表中查找*T*的类型信息。 要实现未注册的接口，`IDispatchImpl`可以使用类，而无需使用预定义的版本号访问注册表。 如果创建的对象`IDispatchImpl`具有 0xFFFF 作为*wMajor*的值，0xFFFF 作为*wMinor*的值，`IDispatchImpl`则类将从 .dll 文件而不是注册表中检索类型库。

`IDispatchImpl`包含管理双接口类型信息的`CComTypeInfoHolder`静态类型成员。 如果有多个对象实现同一`CComTypeInfoHolder`双接口，则仅使用

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`IDispatchImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchimpl：获取名称

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

请参阅[IDispatch：获取](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames)Windows SDK 中的名称。

## <a name="idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl：：获取类型信息

检索双接口的类型信息。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

请参阅[IDispatch：在](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo)Windows SDK 中获取类型信息。

## <a name="idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl：：获取类型信息计数

确定双接口是否有可用的类型信息。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>备注

请参阅`IDispatch::GetTypeInfoCount`Windows SDK。

## <a name="idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>I 调度：：I 调度

构造函数。 调用`AddRef`管理双接口类型信息的受保护成员变量。 析构函数调用 `Release`。

```
IDispatchImpl();
```

## <a name="idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl：：调用

提供对双接口公开的方法和属性的访问。

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

请参阅[IDispatch：：](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)在 Windows SDK 中调用。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
