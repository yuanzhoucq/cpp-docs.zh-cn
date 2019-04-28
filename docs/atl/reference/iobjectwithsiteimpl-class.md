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
ms.openlocfilehash: ad27c4288d7e16949fe38ea6b8a686e3d6916ee6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275225"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 类

此类提供允许其站点进行通信的对象的方法。

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

|名称|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|查询的接口指针的站点。|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|与该站点提供的对象`IUnknown`指针。|
|[IObjectWithSiteImpl::SetSite](#setsite)|与该站点提供的对象`IUnknown`指针。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理站点的`IUnknown`指针。|

## <a name="remarks"></a>备注

[IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite)接口允许对象与其站点通信。 类`IObjectWithSiteImpl`提供默认实现此接口并实现`IUnknown`信息发送给转储调试中的设备生成。

`IObjectWithSiteImpl` 指定两种方法。 客户端首次调用`SetSite`，并传递站点的`IUnknown`指针。 此指针在对象中存储和更高版本可以通过调用检索`GetSite`。

通常情况下，派生从类`IObjectWithSiteImpl`时您正在创建的对象不是控件。 对于控件类派生您的类从[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)，它还提供站点指针。 不是从这两个派生类`IObjectWithSiteImpl`和`IOleObjectImpl`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite

查询指向由标识的接口的指针的站点`riid`。

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>备注

如果站点支持此接口，通过返回的指针`ppvSite`。 否则为`ppvSite`设置为 NULL。

请参阅[IObjectWithSite::GetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-getsite) Windows SDK 中。

##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite

管理站点的`IUnknown`指针。

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>备注

`m_spUnkSite` 最初接收通过调用此指针[SetSite](#setsite)。

##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite

与该站点提供的对象`IUnknown`指针。

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>参数

*pUnkSite*<br/>
[in]指向`IUnknown`管理此对象的站点的接口指针。 如果为 NULL，该对象应调用`IUnknown::Release`此时对象不再知道其站点的任何现有站点上。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite

与该站点提供的对象`IUnknown`指针。

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>备注

请参阅[IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite) Windows SDK 中。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
