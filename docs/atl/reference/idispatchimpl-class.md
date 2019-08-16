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
ms.openlocfilehash: 7e9cb903742cdc31c1d9bba2c4aabbb0472407c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495952"
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 类

为双重接口的`IDispatch`部分提供默认实现。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

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
中双重接口。

*piid*<br/>
中指向*T*的 IID 的指针。

*plibid*<br/>
中一个指针, 指向包含接口相关信息的类型库的 LIBID。 默认情况下, 将传递服务器级类型库。

*wMajor*<br/>
中类型库的主版本。 默认情况下, 该值为1。

*wMinor*<br/>
中类型库的次版本。 默认情况下, 该值为0。

*tihclass*<br/>
中用于管理*T*的类型信息的类。默认情况下，该值为 `CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|构造函数。 对`AddRef`管理双重接口的类型信息的受保护成员变量调用。 析构函数调用 `Release`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|将一组名称映射为对应的一组调度标识符。|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|检索双重接口的类型信息。|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|确定是否有可用于双重接口的类型信息。|
|[IDispatchImpl::Invoke](#invoke)|提供对由双重接口公开的方法和属性的访问。|

## <a name="remarks"></a>备注

`IDispatchImpl`为对象的任何双重接口`IDispatch`的部分提供默认实现。 双重接口派生自`IDispatch` , 并且仅使用自动化兼容类型。 与调度接口一样, 双重接口支持早期绑定和后期绑定;但是, 双重接口还支持 vtable 绑定。

下面的示例演示的`IDispatchImpl`典型实现。

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

默认情况下, `IDispatchImpl`类会在注册表中查找*T*的类型信息。 若要实现未注册的接口, 可以使用`IDispatchImpl`类, 而无需使用预定义的版本号访问注册表。 如果创建`IDispatchImpl`的对象的值为0xffff 作为*wMajor*的值, 而将0xffff 作为*wMinor*的值, 则`IDispatchImpl`类将从 .dll 文件而不是注册表中检索类型库。

`IDispatchImpl`包含类型的静态成员, `CComTypeInfoHolder`该类型管理双重接口的类型信息。 如果有多个实现相同双重接口的对象, `CComTypeInfoHolder`则仅使用一个实例。

## <a name="inheritance-hierarchy"></a>继承层次结构

`T`

`IDispatchImpl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="getidsofnames"></a>IDispatchImpl:: Idispatch.getidsofnames

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

请参阅 Windows SDK 中的[IDispatch:: idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 。

##  <a name="gettypeinfo"></a>IDispatchImpl:: GetTypeInfo

检索双重接口的类型信息。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IDispatch:: GetTypeInfo](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfo) 。

##  <a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount

确定是否有可用于双重接口的类型信息。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>备注

请`IDispatch::GetTypeInfoCount`参阅 Windows SDK 中的。

##  <a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl

构造函数。 对`AddRef`管理双重接口的类型信息的受保护成员变量调用。 析构函数调用 `Release`。

```
IDispatchImpl();
```

##  <a name="invoke"></a>IDispatchImpl:: Invoke

提供对由双重接口公开的方法和属性的访问。

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

请参阅 Windows SDK 中的[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) 。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
