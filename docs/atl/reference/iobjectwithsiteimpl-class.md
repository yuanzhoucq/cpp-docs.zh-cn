---
title: IObjectWithSiteImpl 类
ms.date: 11/04/2016
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
ms.openlocfilehash: 034e5dd42f6e10286520bb2a08effc40b0aca71a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329648"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 类

此类提供允许对象与其站点通信的方法。

## <a name="syntax"></a>语法

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IObjectWithSiteImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IObject 与网站impl：：获取网站](#getsite)|查询接口指针的站点。|
|[IObject 与网站impl：：设置儿童网站](#setchildsite)|使用站点的`IUnknown`指针向对象提供。|
|[IObject 与网站impl：：设置网站](#setsite)|使用站点的`IUnknown`指针向对象提供。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[IObject 与 Siteimpl：：m_spUnkSite](#m_spunksite)|管理站点的`IUnknown`指针。|

## <a name="remarks"></a>备注

[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)接口允许对象与其站点通信。 类`IObjectWithSiteImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

`IObjectWithSiteImpl`指定两种方法。 客户端首先调用`SetSite`，传递站点的`IUnknown`指针。 此指针存储在对象中，以后可以通过调用`GetSite`来检索。

通常，在创建不是控件的对象`IObjectWithSiteImpl`时，派生类。 对于控件，从[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)派生类 ，该函数还提供站点指针。 不要从`IObjectWithSiteImpl`和`IOleObjectImpl`派生类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="iobjectwithsiteimplgetsite"></a><a name="getsite"></a>IObject 与网站impl：：获取网站

查询站点的指向 标识的接口的`riid`指针。

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>备注

如果站点支持此接口，则通过`ppvSite`返回指针。 否则，`ppvSite`设置为 NULL。

请参阅[IObject 与网站：：在](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite)Windows SDK 中获取网站。

## <a name="iobjectwithsiteimplm_spunksite"></a><a name="m_spunksite"></a>IObject 与 Siteimpl：：m_spUnkSite

管理站点的`IUnknown`指针。

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>备注

`m_spUnkSite`最初通过调用[SetSite](#setsite)接收此指针。

## <a name="iobjectwithsiteimplsetchildsite"></a><a name="setchildsite"></a>IObject 与网站impl：：设置儿童网站

使用站点的`IUnknown`指针向对象提供。

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>参数

*pUnkSite*<br/>
[在]指向管理此`IUnknown`对象的站点的接口指针。 如果 NULL，则对象应`IUnknown::Release`调用对象不再知道其站点的任何现有站点。

### <a name="return-value"></a>返回值

返回S_OK。

## <a name="iobjectwithsiteimplsetsite"></a><a name="setsite"></a>IObject 与网站impl：：设置网站

使用站点的`IUnknown`指针向对象提供。

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>备注

请参阅[IObject 与网站：：在](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)Windows SDK 中设置网站。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
