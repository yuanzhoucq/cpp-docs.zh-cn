---
title: "IProvideClassInfo2Impl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IProvideClassInfo2
- ATL.IProvideClassInfo2Impl
- IProvideClassInfo2Impl
- ATL::IProvideClassInfo2Impl
dev_langs:
- C++
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
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
ms.openlocfilehash: 0d3bed0f625e396b63ada19ded02ba9ad3b697b0
ms.lasthandoff: 02/24/2017

---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl 类
此类提供的默认实现[IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303)和[IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764)方法。  
  
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
 *pcoclsid*  
 指向 coclass' 标识符的指针。  
  
 *psrcid*  
 一个指向 coclass' 默认的传出调度接口的标识符。  
  
 `plibid`  
 一个指向包含接口的信息的类型库的 LIBID。 默认情况下，传递服务器级类型库。  
  
 `wMajor`  
 类型库的主要版本。 默认值为 1。  
  
 `wMinor`  
 类型库的次要版本。 默认值为 0。  
  
 `tihclass`  
 用于管理 coclass' 类型的信息的类。 默认值为 `CComTypeInfoHolder`。  
  
## <a name="members"></a>成员  
  
### <a name="constructors"></a>构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|检索**ITypeInfo**与 coclass' 的类型信息的指针。|  
|[IProvideClassInfo2Impl::GetGUID](#getguid)|检索对象的传出调度接口的 GUID。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::_tih](#_tih)|管理组件类的类型信息。|  
  
## <a name="remarks"></a>备注  
 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764)接口扩展[IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303)通过添加`GetGUID`方法。 此方法允许客户端检索对象的传出接口 IID 为其默认事件集。 类`IProvideClassInfo2Impl`提供的默认实现**IProvideClassInfo**和`IProvideClassInfo2`方法。  
  
 `IProvideClassInfo2Impl`包含类型的静态成员`CComTypeInfoHolder`管理组件类的类型信息。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-namegetclassinfoa--iprovideclassinfo2implgetclassinfo"></a><a name="getclassinfo"></a>IProvideClassInfo2Impl::GetClassInfo  
 检索`ITypeInfo`与 coclass' 的类型信息的指针。  
  
```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IProvideClassInfo::GetClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms690192)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetguida--iprovideclassinfo2implgetguid"></a><a name="getguid"></a>IProvideClassInfo2Impl::GetGUID  
 检索对象的传出调度接口的 GUID。  
  
```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IProvideClassInfo2::GetGUID](http://msdn.microsoft.com/library/windows/desktop/ms679721)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameiprovideclassinfo2impla--iprovideclassinfo2impliprovideclassinfo2impl"></a><a name="iprovideclassinfo2impl"></a>IProvideClassInfo2Impl::IProvideClassInfo2Impl  
 构造函数。  
  
```
IProvideClassInfo2Impl();
```  
  
### <a name="remarks"></a>备注  
 调用`AddRef`上[_tih](#_tih)成员。 析构函数调用**版本**。  
  
##  <a name="a-nametiha--iprovideclassinfo2impltih"></a><a name="_tih"></a>IProvideClassInfo2Impl::_tih  
 此静态数据成员是类模板参数的一个实例`tihclass`，它们的默认值是`CComTypeInfoHolder`。  
  
```
static  tihclass
    _tih;
```     
  
### <a name="remarks"></a>备注  
 `_tih`管理组件类的类型信息。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

