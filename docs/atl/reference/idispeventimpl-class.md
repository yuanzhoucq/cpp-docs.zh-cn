---
title: IDispEventImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7809a61fe39a4b4b913531de29e03c3eb440c418
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="idispeventimpl-class"></a>IDispEventImpl 类
此类提供的实现`IDispatch`方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0, 
    class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```  
  
#### <a name="parameters"></a>参数  
 `nID`  
 源对象的唯一标识符。 当`IDispEventImpl`是基类的复合控件，此参数使用所需的包含控件的资源 ID。 在其他情况下，使用任意的正整数。  
  
 `T`  
 用户的类，该类派生自`IDispEventImpl`。  
  
 `pdiid`  
 指向此类实现的事件显示接口的 IID 的指针。 必须在由表示的类型库中定义此接口`plibid`， `wMajor`，和`wMinor`。  
  
 `plibid`  
 定义的调度接口的类型库的指针指向的`pdiid`。 如果 **& GUID_NULL**，将从外包事件的对象加载类型库。  
  
 `wMajor`  
 类型库的主版本。 默认值为 0。  
  
 `wMinor`  
 类型库的次版本。 默认值为 0。  
  
 `tihclass`  
 用于管理的类型信息的类`T`。 默认值是类型的类`CComTypeInfoHolder`; 但是，可以通过不提供类型的类重写此模板参数`CComTypeInfoHolder`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用于管理的类型信息的类。 默认情况下， `CComTypeInfoHolder`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|查找指定的调度标识符的函数索引。|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|将单个成员和一组可选的自变量名称映射到对应的一组整数 Dispid。|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|检索对象的类型信息。|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|检索的类型信息接口的数量。|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|检索的用户定义的类型的基本类型。|  
  
## <a name="remarks"></a>备注  
 `IDispEventImpl` 提供一种而无需实现事件显示接口的方式，提供在该接口上每个方法/事件的实现代码。 `IDispEventImpl` 提供的实现`IDispatch`方法。 只需提供你有兴趣处理的事件的实现。  
  
 `IDispEventImpl` 与你的类将事件路由到适当的处理程序函数中的事件接收器映射结合工作。 若要使用此类：  
  

 添加[SINK_ENTRY](composite-control-macros.md#sink_entry)或[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)宏为你想要处理的每个对象每个事件的事件接收器映射。 使用时`IDispEventImpl`为复合控件的基类，您可以调用[AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)建立，中断与事件源的连接的所有条目在事件都接收器映射。 在其他情况下，或者对于更好地控制，调用[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)建立源对象和基的类之间的连接。 调用[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)以断开的连接。  

  
 你必须从中派生`IDispEventImpl`(使用的唯一值`nID`) 为每个需要处理事件的对象。 通过与一个源对象对不同的源对象，然后告知取消通知，可以重用的基类，但可以由单个对象一次处理的源对象的最大数目限制数`IDispEventImpl`基类。  
  
 `IDispEventImpl` 提供与相同的功能[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)，但它会从类型库，而不是让它指向的指针作为提供获取接口的类型信息[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构。 使用`IDispEventSimpleImpl`时你不具有描述事件接口的类型库或想要避免与使用类型库关联的开销。  
  
> [!NOTE]
> `IDispEventImpl` 和`IDispEventSimpleImpl`提供其自己实现**iunknown:: Queryinterface**启用每个`IDispEventImpl`和`IDispEventSimpleImpl`基类，以同时仍然允许对中的类成员的直接访问充当一个单独的 COM 标识你主要的 COM 对象。  
  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值 HRESULT 或从事件处理程序方法; void任何其他返回值不受支持，而且其行为是不确定。  
  
 有关详细信息，请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId  
 查找指定的调度标识符的函数索引。  
  
```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```  
  
### <a name="parameters"></a>参数  
 `iid`  
 [in]对函数的 ID 的引用。  
  
 *dispidMember*  
 [in]函数的调度 ID。  
  
 `lcid`  
 [in]区域设置上下文的函数 id。  
  
 `info`  
 [in]结构，该值指示如何调用该函数。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames  
 将单个成员和一组可选的自变量名称映射到对应的一组整数 Dispid，可在后续调用[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
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
  
##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo  
 检索对象的类型信息，然后可以使用该信息获取接口的类型信息。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount  
 检索对象提供的类型信息接口的数量（0 或 1）。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) Windows SDK 中。  
  
##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType  
 检索的用户定义的类型的基本类型。  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>参数  
 `pTI`  
 [in]指向的指针[ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680)包含用户定义类型的接口。  
  
 *hrt*  
 [in]要检索的类型说明句柄。  
  
### <a name="return-value"></a>返回值  
 变量的类型。  
  
### <a name="remarks"></a>备注  
 请参阅[ITypeInfo::GetRefTypeInfo](http://msdn.microsoft.com/en-us/61d3b31d-6591-4e55-9e82-5246a168be00)。  
  
##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl  
 构造函数。 存储类模板参数的值`plibid`， `pdiid`， `wMajor`，和`wMinor`。  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>  IDispEventImpl::tihclass  
 此 typedef 是类模板参数的实例`tihclass`。  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>备注  
 默认情况下，类是`CComTypeInfoHolder`。 `CComTypeInfoHolder` 管理类的类型信息。  
  
## <a name="see-also"></a>请参阅  
 [_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](composite-control-macros.md#sink_entry)   
 [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [类概述](../../atl/atl-class-overview.md)