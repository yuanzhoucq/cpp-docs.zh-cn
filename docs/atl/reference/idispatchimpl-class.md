---
title: IDispatchImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fddf556eba07264f6ea0b01edea3e3d1e8a3a7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="idispatchimpl-class"></a>IDispatchImpl 类
提供的默认实现`IDispatch`双重接口的一部分。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
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
 指向 IID 的`T`。  
  
 [in] `plibid`  
 指向包含接口的信息的类型库的 LIBID 的指针。 默认情况下，传递服务器级类型库。  
  
 [in] `wMajor`  
 类型库的主版本。 默认情况下，值为 1。  
  
 [in] `wMinor`  
 类型库的次版本。 默认情况下，值为 0。  
  
 [in] `tihclass`  
 用于管理的类型信息的类`T`。 默认情况下，该值为 `CComTypeInfoHolder`。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|构造函数。 调用`AddRef`管理双重接口的类型信息的受保护的成员变量上。 析构函数调用 `Release`。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|将一组名称映射为对应的一组调度标识符。|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|检索双重接口的类型信息。|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|确定是否有可用于双重接口的类型信息。|  
|[IDispatchImpl::Invoke](#invoke)|提供对的方法和属性公开的双重接口访问。|  
  
## <a name="remarks"></a>备注  
 `IDispatchImpl` 提供的默认实现`IDispatch`对象任何双重接口的一部分。 双重接口派生自`IDispatch`并使用仅自动化兼容的类型。 调度接口，如双重接口支持早期绑定和后期绑定;但是，双重接口还支持 vtable 绑定。  
  
 下面的示例演示的典型实现`IDispatchImpl`。  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 默认情况下，`IDispatchImpl`类查找的类型信息`T`注册表中。 若要实现注销的接口，可以使用`IDispatchImpl`类而不使用预定义的版本号访问注册表。 如果你创建`IDispatchImpl`具有 0xFFFF 的值作为对象`wMajor`和的值为 0xFFFF `wMinor`、`IDispatchImpl`类从.dll 文件而不是注册表中检索类型库。  
  
 `IDispatchImpl` 包含类型的静态成员`CComTypeInfoHolder`管理双重接口的类型信息。 如果你有多个对象实现相同的双重接口，只有一个实例`CComTypeInfoHolder`使用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames  
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
 请参阅[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) Windows SDK 中。  
  
##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo  
 检索双重接口的类型信息。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) Windows SDK 中。  
  
##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount  
 确定是否有可用于双重接口的类型信息。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>备注  
 请参阅`IDispatch::GetTypeInfoCount`Windows SDK 中。  
  
##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl  
 构造函数。 调用`AddRef`管理双重接口的类型信息的受保护的成员变量上。 析构函数调用**版本**。  
  
```
IDispatchImpl();
```  
  
##  <a name="invoke"></a>  IDispatchImpl::Invoke  
 提供对的方法和属性公开的双重接口访问。  
  
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
 请参阅[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)
