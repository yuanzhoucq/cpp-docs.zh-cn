---
title: "IDispatchImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATL.IDispatchImpl
- ATL::IDispatchImpl
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
caps.latest.revision: 27
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: fff4cbc0a3f87b584f1a4211f4aad37228ed4da7
ms.lasthandoff: 02/24/2017

---
# <a name="idispatchimpl-class"></a>IDispatchImpl 类
提供的默认实现，`IDispatch`双重接口的一部分。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0, 
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```  
  
#### <a name="parameters"></a>参数  
 [in] `T`  
 双重接口。  
  
 [in] `piid`  
 指向的指针的 IID `T`。  
  
 [in] `plibid`  
 一个指向包含接口的信息的类型库的 LIBID。 默认情况下，传递服务器级类型库。  
  
 [in] `wMajor`  
 类型库的主要版本。 默认情况下，值为 1。  
  
 [in] `wMinor`  
 类型库的次要版本。 默认情况下，值为 0。  
  
 [in] `tihclass`  
 用于管理的类型信息的类`T`。 默认情况下，该值为 `CComTypeInfoHolder`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|构造函数。 调用`AddRef`管理双重接口的类型信息的受保护的成员变量上。 析构函数调用 `Release`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|将一组名称映射为对应的一组调度标识符。|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|检索双重接口的类型信息。|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|确定是否有可用于双重接口的类型信息。|  
|[IDispatchImpl::Invoke](#invoke)|提供访问权限的方法和属性公开的双重接口。|  
  
## <a name="remarks"></a>备注  
 `IDispatchImpl`提供的默认实现，`IDispatch`对象上的任何双重接口的一部分。 双重接口派生自`IDispatch`，并使用只有自动化兼容类型。 调度接口，如双重接口支持早期绑定和后期绑定;但是，双重接口还支持 vtable 绑定。  
  
 下面的示例演示的典型实现`IDispatchImpl`。  
  
 [!code-cpp[NVC_ATL_COM&#47;](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 默认情况下，`IDispatchImpl`类查找的类型信息`T`注册表中。 若要实现接口未注册时，可以使用`IDispatchImpl`类而不使用预定义的版本号来访问注册表。 如果您创建`IDispatchImpl`对象，它具有 0xFFFF 的值作为`wMajor`和 0xFFFF 的值作为`wMinor`、`IDispatchImpl`类从.dll 文件而不是注册表中检索类型库。  
  
 `IDispatchImpl`包含类型的静态成员`CComTypeInfoHolder`管理双重接口的类型信息。 如果您有多个对象实现相同的双重接口，只有一个实例`CComTypeInfoHolder`使用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-namegetidsofnamesa--idispatchimplgetidsofnames"></a><a name="getidsofnames"></a>IDispatchImpl::GetIDsOfNames  
 将一组名称映射为对应的一组调度标识符。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfoa--idispatchimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispatchImpl::GetTypeInfo  
 检索双重接口的类型信息。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfocounta--idispatchimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispatchImpl::GetTypeInfoCount  
 确定是否有可用于双重接口的类型信息。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>备注  
 See `IDispatch::GetTypeInfoCount` in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameidispatchimpla--idispatchimplidispatchimpl"></a><a name="idispatchimpl"></a>IDispatchImpl::IDispatchImpl  
 构造函数。 调用`AddRef`管理双重接口的类型信息的受保护的成员变量上。 析构函数调用**版本**。  
  
```
IDispatchImpl();
```  
  
##  <a name="a-nameinvokea--idispatchimplinvoke"></a><a name="invoke"></a>IDispatchImpl::Invoke  
 提供访问权限的方法和属性公开的双重接口。  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```  
  
### <a name="remarks"></a>备注  
 请参阅[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

