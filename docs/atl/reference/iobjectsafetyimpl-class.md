---
title: "IObjectSafetyImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IObjectSafetyImpl
dev_langs:
- C++
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: cff5995555cd069855f9d7becb9eb8367e80c920
ms.lasthandoff: 02/24/2017

---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl 类
此类提供的默认实现`IObjectSafety`接口，以允许客户端用于检索和设置对象的安全级别。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class T,DWORD dwSupportedSafety>  
class IObjectSafetyImpl
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IObjectSafetyImpl`。  
  
 *dwSupportedSafety*  
 指定控件的支持的安全选项。 可以是以下值之一：  
  
- **INTERFACESAFE_FOR_UNTRUSTED_CALLER**通过所标识的接口[SetInterfaceSafetyOptions](#setinterfacesafetyoptions)参数`riid`应成为可安全执行脚本。  
  
- **INTERFACESAFE_FOR_UNTRUSTED_DATA**通过所标识的接口`SetInterfaceSafetyOptions`参数`riid`应可安全执行不受信任数据时进行初始化。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|检索支持该对象的安全选项，以及为该对象当前设置的安全选项。|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|使得该对象可安全执行初始化和脚本。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|存储对象的当前安全级别。|  
  
## <a name="remarks"></a>备注  
 类`IObjectSafetyImpl`提供的默认实现`IObjectSafety`。 `IObjectSafety`接口允许客户端用于检索和设置对象的安全级别。 例如，web 浏览器可以调用**IObjectSafety::SetInterfaceSafetyOptions**控件设为可安全初始化或可安全执行脚本。  
  
 请注意，使用[IMPLEMENTED_CATEGORY](http://msdn.microsoft.com/library/d898ef34-5684-4709-beb9-7114ddd96674)宏并使用**CATID_SafeForScripting**和**CATID_SafeForInitializing**组件类别提供了一种指定的组件安全。  
  
 **相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="a-namegetinterfacesafetyoptionsa--iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions  
 检索支持该对象的安全选项，以及为该对象当前设置的安全选项。  
  
```
HRESULT GetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```  
  
### <a name="remarks"></a>备注  
 实现将返回相应的值的任何接口的对象的实现支持**iunknown:: Queryinterface**。  
  
> [!IMPORTANT]
>  支持的任何对象`IObjectSafety`负责其自身的安全，并且它委托的任何对象。 程序员必须考虑从用户的上下文中运行代码时产生的帐户问题、 跨站点脚本和执行检查，适合区域。  
  
 请参阅[IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namemdwcurrentsafetya--iobjectsafetyimplmdwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety  
 存储对象的当前安全级别。  
  
```
DWORD m_dwCurrentSafety;
```  
  
##  <a name="a-namesetinterfacesafetyoptionsa--iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions  
 可使该对象可安全执行初始化或通过设置脚本编写[m_dwCurrentSafety](#m_dwcurrentsafety)为适当的值的成员。  
  
```
HRESULT SetInterfaceSafetyOptions(  
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```  
  
### <a name="remarks"></a>备注  
 实现返回**E_NOINTERFACE**的对象的实现不支持任何接口**iunknown:: Queryinterface**。  
  
> [!IMPORTANT]
>  支持的任何对象`IObjectSafety`负责其自身的安全，并且它委托的任何对象。 程序员必须考虑从用户的上下文中运行代码时产生的帐户问题、 跨站点脚本和执行检查，适合区域。  
  
 请参阅[IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [IObjectSafety 接口](https://msdn.microsoft.com/library/aa768224.aspx)   
 [类概述](../../atl/atl-class-overview.md)

