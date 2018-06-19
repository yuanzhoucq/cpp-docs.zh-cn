---
title: IObjectWithSiteImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl
- ATLCOM/ATL::IObjectWithSiteImpl::GetSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetChildSite
- ATLCOM/ATL::IObjectWithSiteImpl::SetSite
- ATLCOM/ATL::IObjectWithSiteImpl::m_spUnkSite
dev_langs:
- C++
helpviewer_keywords:
- IObjectWithSiteImpl class
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c626db62a02fba70f926776ea214e664d2f7f82
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362034"
---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 类
此类提供允许与其站点通信对象的方法。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IObjectWithSiteImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|查询的接口指针的站点。|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|与该站点提供的对象**IUnknown**指针。|  
|[IObjectWithSiteImpl::SetSite](#setsite)|与该站点提供的对象**IUnknown**指针。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理站点的**IUnknown**指针。|  
  
## <a name="remarks"></a>备注  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)接口允许对象与其站点通信。 类`IObjectWithSiteImpl`提供默认实现此接口并实现**IUnknown**信息发送给转储设备在调试生成。  
  
 `IObjectWithSiteImpl` 指定两种方法。 客户端首先调用`SetSite`，传递站点的**IUnknown**指针。 此指针存储在该对象，和更高版本可以通过调用检索`GetSite`。  
  
 通常情况下，派生您的类从`IObjectWithSiteImpl`当您正在创建的对象不是一个控件。 有关控件，派生您的类从[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)，其中还提供站点指针。 不从您的类同时`IObjectWithSiteImpl`和`IOleObjectImpl`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="getsite"></a>  IObjectWithSiteImpl::GetSite  
 查询为指向由标识的接口的站点`riid`。  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>备注  
 如果站点支持此接口，通过返回指针`ppvSite`。 否则为`ppvSite`设置为**NULL**。  
  
 请参阅[IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452) Windows SDK 中。  
  
##  <a name="m_spunksite"></a>  IObjectWithSiteImpl::m_spUnkSite  
 管理站点的**IUnknown**指针。  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>备注  
 `m_spUnkSite` 最初接收通过调用此指针[SetSite](#setsite)。  
  
##  <a name="setchildsite"></a>  IObjectWithSiteImpl::SetChildSite  
 与该站点提供的对象**IUnknown**指针。  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>参数  
 *pUnkSite*  
 [in]指向**IUnknown**管理此对象的站点的接口指针。 如果为 NULL，应调用该对象`IUnknown::Release`此时对象不再知道其站点的任何现有站点上。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="setsite"></a>  IObjectWithSiteImpl::SetSite  
 与该站点提供的对象**IUnknown**指针。  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
