---
title: "IPerPropertyBrowsingImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
dev_langs: C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4e8755d4f9728476967196837b112a66613d6912
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl 类
此类实现**IUnknown**和允许客户端访问的对象的属性页中的信息。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IPerPropertyBrowsingImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|检索用于描述给定的属性的字符串。|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|检索与给定的属性可以接受的值相对应的字符串数组。|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|检索**VARIANT**包含由给定的 DISPID 标识属性的值。 与从检索此字符串名称关联的 DISPID 是`GetPredefinedStrings`。 ATL 实现返回**E_NOTIMPL**。|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|检索与给定属性相关联的属性页的 CLSID。|  
  
## <a name="remarks"></a>备注  
 [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432)接口允许客户端访问的对象的属性页中的信息。 类`IPerPropertyBrowsingImpl`提供默认实现此接口并实现**IUnknown**信息发送给转储设备在调试生成。  
  
> [!NOTE]
>  如果你使用 Microsoft Access 作为容器应用程序，你必须派生您的类从`IPerPropertyBrowsingImpl`。 否则，访问将不会加载你的控件。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
##  <a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString  
 检索用于描述给定的属性的字符串。  
  
```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IPerPropertyBrowsing::GetDisplayString](http://msdn.microsoft.com/library/windows/desktop/ms688734) Windows SDK 中。  
  
##  <a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings  
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
 请参阅[IPerPropertyBrowsing::GetPredefinedStrings](http://msdn.microsoft.com/library/windows/desktop/ms679724) Windows SDK 中。  
  
##  <a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue  
 检索**VARIANT**包含由给定的 DISPID 标识属性的值。 与从检索此字符串名称关联的 DISPID 是`GetPredefinedStrings`。  
  
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
  
 请参阅[IPerPropertyBrowsing::GetPredefinedValue](http://msdn.microsoft.com/library/windows/desktop/ms690401) Windows SDK 中。  
  
##  <a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage  
 检索与指定的属性相关联的属性页的 CLSID。  
  
```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```  
  
### <a name="remarks"></a>备注  
 ATL 使用对象的属性映射来获取此信息。  
  
 请参阅[IPerPropertyBrowsing::MapPropertyToPage](http://msdn.microsoft.com/library/windows/desktop/ms694476) Windows SDK 中。  
  
## <a name="see-also"></a>另请参阅  
 [IPropertyPageImpl 类](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl 类](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [类概述](../../atl/atl-class-overview.md)
