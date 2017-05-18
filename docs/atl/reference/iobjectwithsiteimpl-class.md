---
title: "IObjectWithSiteImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 49c52810417650c3d80fe4d0c09ccb2b67208ad4
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="iobjectwithsiteimpl-class"></a>IObjectWithSiteImpl 类
此类提供方法允许对象与其站点进行通信。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>
    class ATL_NO_VTABLE IObjectWithSiteImpl :
    public IObjectWithSite
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IObjectWithSiteImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](#getsite)|查询的接口指针的站点。|  
|[IObjectWithSiteImpl::SetChildSite](#setchildsite)|与该站点提供的对象**IUnknown**指针。|  
|[IObjectWithSiteImpl::SetSite](#setsite)|与该站点提供的对象**IUnknown**指针。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m_spUnkSite](#m_spunksite)|管理站点的**IUnknown**指针。|  
  
## <a name="remarks"></a>备注  
 [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)接口允许对象与其站点进行通信。 类`IObjectWithSiteImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
 `IObjectWithSiteImpl`指定两种方法。 客户端首次调用`SetSite`，传递该站点的**IUnknown**指针。 此指针存储在该对象，并且更高版本可以通过调用检索`GetSite`。  
  
 通常情况下，派生您的类从`IObjectWithSiteImpl`时您正在创建的对象不是控件。 对于控件而言，派生您的类从[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)，它还提供了站点指针。 不从您的类同时`IObjectWithSiteImpl`和`IOleObjectImpl`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="getsite"></a>IObjectWithSiteImpl::GetSite  
 查询为指向由所标识的接口的站点`riid`。  
  
```
STDMETHOD(GetSite)(
    REFIID riid,
    void** ppvSite);
```  
  
### <a name="remarks"></a>备注  
 如果站点支持此接口，通过返回指针`ppvSite`。 否则为`ppvSite`设置为**NULL**。  
  
 请参阅[IObjectWithSite::GetSite](http://msdn.microsoft.com/library/windows/desktop/ms694452)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="m_spunksite"></a>IObjectWithSiteImpl::m_spUnkSite  
 管理站点的**IUnknown**指针。  
  
```
CComPtr<IUnknown> m_spUnkSite;
```  
  
### <a name="remarks"></a>备注  
 `m_spUnkSite`最初接收通过调用此指针[SetSite](#setsite)。  
  
##  <a name="setchildsite"></a>IObjectWithSiteImpl::SetChildSite  
 与该站点提供的对象**IUnknown**指针。  
  
```
HRESULT SetChildSite(IUnknown* pUnkSite);
```  
  
### <a name="parameters"></a>参数  
 *pUnkSite*  
 [in]指向**IUnknown**管理此对象的站点的接口指针。 如果为 NULL，该对象应调用`IUnknown::Release`此时对象不再知道其站点的任何现有网站上。  
  
### <a name="return-value"></a>返回值  
 返回 `S_OK`。  
  
##  <a name="setsite"></a>IObjectWithSiteImpl::SetSite  
 与该站点提供的对象**IUnknown**指针。  
  
```
STDMETHOD(SetSite)(IUnknown* pUnkSite);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

