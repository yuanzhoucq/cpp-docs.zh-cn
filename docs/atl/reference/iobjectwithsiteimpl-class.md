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
ms.openlocfilehash: e857f739e3ff7235c473e99abbef6aab0d3f4205
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495833"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 类

此类提供了允许对象与其站点进行通信的方法。

## <a name="syntax"></a>语法

```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IObjectWithSiteImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::GetSite](#getsite)|查询站点中的接口指针。|
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|为对象提供站点的`IUnknown`指针。|
|[IObjectWithSiteImpl::SetSite](#setsite)|为对象提供站点的`IUnknown`指针。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理站点的`IUnknown`指针。|

## <a name="remarks"></a>备注

[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)接口允许对象与其站点进行通信。 类`IObjectWithSiteImpl`提供此接口的默认实现, 并通过`IUnknown`在调试版本中将信息发送到转储设备来实现。

`IObjectWithSiteImpl`指定两个方法。 客户端首先调用`SetSite`, 同时传递站点的`IUnknown`指针。 此指针存储在对象中, 以后可以通过调用来`GetSite`检索。

通常, 当你创建的对象`IObjectWithSiteImpl`不是控件时, 将从派生类。 对于控件, 从[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)派生您的类, 它还提供了站点指针。 不要从`IObjectWithSiteImpl`和`IOleObjectImpl`派生你的类。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IObjectWithSite`

`IObjectWithSiteImpl`

## <a name="requirements"></a>要求

**标头:** atlcom。h

##  <a name="getsite"></a>IObjectWithSiteImpl::GetSite

在站点中查询指向由标识`riid`的接口的指针。

```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```

### <a name="remarks"></a>备注

如果站点支持此接口, 则通过`ppvSite`返回指针。 否则, `ppvSite`设置为 NULL。

请参阅 Windows SDK 中的[IObjectWithSite:: GetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-getsite) 。

##  <a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite

管理站点的`IUnknown`指针。

```
CComPtr<IUnknown> m_spUnkSite;
```

### <a name="remarks"></a>备注

`m_spUnkSite`最初通过调用[SetSite](#setsite)接收此指针。

##  <a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite

为对象提供站点的`IUnknown`指针。

```
HRESULT SetChildSite(IUnknown* pUnkSite);
```

### <a name="parameters"></a>参数

*pUnkSite*<br/>
中指向管理此`IUnknown`对象的站点的接口指针的指针。 如果为 NULL, 则对象应`IUnknown::Release`在任何现有站点上调用, 此时对象将不再知道其站点。

### <a name="return-value"></a>返回值

返回 S_OK。

##  <a name="setsite"></a>IObjectWithSiteImpl:: SetSite

为对象提供站点的`IUnknown`指针。

```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
