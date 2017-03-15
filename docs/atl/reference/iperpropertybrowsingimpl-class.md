---
title: "IPerPropertyBrowsingImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IPerPropertyBrowsingImpl
- IPerPropertyBrowsing
- ATL::IPerPropertyBrowsingImpl
- ATL::IPerPropertyBrowsingImpl<T>
- IPerPropertyBrowsingImpl
- ATL.IPerPropertyBrowsingImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8f2c2016a83cad906be22183fcffa20ae3da3042
ms.lasthandoff: 02/24/2017

---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 类
此类实现**IUnknown**并且允许客户端来访问对象的属性页中的信息。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IPerPropertyBrowsingImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|检索描述某一给定的属性的字符串。|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|检索对应于给定的属性可接受的值的字符串数组。|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|检索**VARIANT**包含由给定 DISPID 标识属性的值。 与从检索到的字符串名称相关联的 DISPID 是`GetPredefinedStrings`。 ATL 实现返回**E_NOTIMPL**。|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|检索与某一给定属性关联的属性页的 CLSID。|  
  
## <a name="remarks"></a>备注  
 [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432)接口允许客户端访问对象的属性页中的信息。 类`IPerPropertyBrowsingImpl`提供此接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
> [!NOTE]
>  如果您使用 Microsoft Access 作为容器应用程序，必须派生您的类从`IPerPropertyBrowsingImpl`。 否则，访问不会加载您的控件。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-namegetdisplaystringa--iperpropertybrowsingimplgetdisplaystring"></a><a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString  
 检索描述某一给定的属性的字符串。  
  
```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPerPropertyBrowsing::GetDisplayString](http://msdn.microsoft.com/library/windows/desktop/ms688734)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetpredefinedstringsa--iperpropertybrowsingimplgetpredefinedstrings"></a><a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings  
 填充每个数组具有零个项目。  
  
```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```  
  
### <a name="return-value"></a>返回值  
 ATL 的实现[GetPredefinedValue](#getpredefinedvalue)返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 请参阅[IPerPropertyBrowsing::GetPredefinedStrings](http://msdn.microsoft.com/library/windows/desktop/ms679724)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetpredefinedvaluea--iperpropertybrowsingimplgetpredefinedvalue"></a><a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue  
 检索**VARIANT**包含由给定 DISPID 标识属性的值。 与从检索到的字符串名称相关联的 DISPID 是`GetPredefinedStrings`。  
  
```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```  
  
### <a name="return-value"></a>返回值  
 返回**E_NOTIMPL**。  
  
### <a name="remarks"></a>备注  
 ATL 的实现[GetPredefinedStrings](#getpredefinedstrings)检索没有相应的字符串。  
  
 请参阅[IPerPropertyBrowsing::GetPredefinedValue](http://msdn.microsoft.com/library/windows/desktop/ms690401)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemappropertytopagea--iperpropertybrowsingimplmappropertytopage"></a><a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage  
 检索与指定的属性相关联的属性页的 CLSID。  
  
```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来获取此信息。  
  
 请参阅[IPerPropertyBrowsing::MapPropertyToPage](http://msdn.microsoft.com/library/windows/desktop/ms694476)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)

