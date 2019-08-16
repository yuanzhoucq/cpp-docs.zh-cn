---
title: IProvideClassInfo2Impl 类
ms.date: 11/04/2016
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
ms.openlocfilehash: f0ff3607002d32b4e21f7fc2199cc5da3662af8b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495541"
---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl 类

此类提供[IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)和[IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)方法的默认实现。

## <a name="syntax"></a>语法

```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```

#### <a name="parameters"></a>参数

*pcoclsid*<br/>
指向组件类标识符的指针。

*psrcid*<br/>
一个指针, 指向组件类默认传出调度接口的标识符。

*plibid*<br/>
一个指针, 指向包含接口相关信息的类型库的 LIBID。 默认情况下, 将传递服务器级类型库。

*wMajor*<br/>
类型库的主版本。 默认值为 1。

*wMinor*<br/>
类型库的次版本。 默认值为 0。

*tihclass*<br/>
用于管理组件类的类型信息的类。 默认值为 `CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|name|描述|
|----------|-----------------|
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|检索指向组件类的类型信息的指针。`ITypeInfo`|
|[IProvideClassInfo2Impl::GetGUID](#getguid)|检索对象的传出调度接口的 GUID。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[IProvideClassInfo2Impl::_tih](#_tih)|管理 coclass 的类型信息。|

## <a name="remarks"></a>备注

[IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)接口`GetGUID`通过添加方法来扩展[IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) 。 此方法允许客户端检索其默认事件集的对象传出接口 IID。 类`IProvideClassInfo2Impl`提供`IProvideClassInfo`和方法的默认实现。`IProvideClassInfo2`

`IProvideClassInfo2Impl`包含一个类型`CComTypeInfoHolder`的静态成员, 该成员管理组件类的类型信息。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="getclassinfo"></a>IProvideClassInfo2Impl:: (

检索指向组件类的类型信息的指针。`ITypeInfo`

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IProvideClassInfo:: (](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo) 。

##  <a name="getguid"></a>IProvideClassInfo2Impl:: GetGUID

检索对象的传出调度接口的 GUID。

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IProvideClassInfo2:: GetGUID](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid) 。

##  <a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl

构造函数。

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>备注

对`AddRef` [_tih](#_tih)成员的调用。 析构函数调用 `Release`。

##  <a name="_tih"></a>IProvideClassInfo2Impl::_tih

此静态数据成员是类模板参数*tihclass*的实例, 默认情况下为`CComTypeInfoHolder`。

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>备注

`_tih`管理 coclass 的类型信息。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
