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
ms.openlocfilehash: 0d1ee9acc1cfabc71ecf33fcb5919d826899c671
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329560"
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

*普科克劳西德*<br/>
指向同类标识符的指针。

*psrcid*<br/>
指向共类默认传出接口的标识符的指针。

*普利比德*<br/>
指向类型库 LIBID 的指针，其中包含有关接口的信息。 默认情况下，传递服务器级类型库。

*w 主要*<br/>
类型库的主版本。 默认值为 1。

*wMinor*<br/>
类型库的次版本。 默认值为 0。

*提赫班*<br/>
用于管理共类类型信息的类。 默认值为 `CComTypeInfoHolder`。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|名称|说明|
|----------|-----------------|
|[I提供类信息2impl：：i提供类信息2impl](#iprovideclassinfo2impl)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I提供类信息2Impl：：获取类信息](#getclassinfo)|检索指向同`ITypeInfo`类类型信息的指针。|
|[I提供类信息2impl：：获取GUID](#getguid)|检索对象传出的 dispinterface 的 GUID。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[I提供ClassInfo2Impl：：_tih](#_tih)|管理共类的类型信息。|

## <a name="remarks"></a>备注

[IProvideClassInfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)接口通过添加`GetGUID`方法扩展[IProvideClassInfo。](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo) 此方法允许客户端为其默认事件集检索对象的传出接口 IID。 类`IProvideClassInfo2Impl`提供 和`IProvideClassInfo``IProvideClassInfo2`方法的默认实现。

`IProvideClassInfo2Impl`包含管理 coclass 的类型`CComTypeInfoHolder`信息的类型静态成员。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IProvideClassInfo2`

`IProvideClassInfo2Impl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>I提供类信息2Impl：：获取类信息

检索指向同`ITypeInfo`类类型信息的指针。

```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```

### <a name="remarks"></a>备注

请参阅[I 提供类信息：在](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo-getclassinfo)Windows SDK 中获取类信息。

## <a name="iprovideclassinfo2implgetguid"></a><a name="getguid"></a>I提供类信息2impl：：获取GUID

检索对象传出的 dispinterface 的 GUID。

```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```

### <a name="remarks"></a>备注

请参阅[I提供ClassInfo2：在](/windows/win32/api/ocidl/nf-ocidl-iprovideclassinfo2-getguid)Windows SDK 中获取GUID。

## <a name="iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>I提供类信息2impl：：i提供类信息2impl

构造函数。

```
IProvideClassInfo2Impl();
```

### <a name="remarks"></a>备注

调用`AddRef`[_tih](#_tih)成员。 析构函数调用 `Release`。

## <a name="iprovideclassinfo2impl_tih"></a><a name="_tih"></a>I提供ClassInfo2Impl：：_tih

此静态数据成员是类模板参数*tihclass*的实例，默认情况下是`CComTypeInfoHolder`。

```
static  tihclass
    _tih;
```

### <a name="remarks"></a>备注

`_tih`管理共类的类型信息。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
