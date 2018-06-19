---
title: IDispEventSimpleImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89f565c1e32f1208fbb039321d26b9175596d57e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365989"
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 类
此类提供的实现`IDispatch`方法，而不从类型库中获取类型信息。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>参数  
 `nID`  
 源对象的唯一标识符。 当`IDispEventSimpleImpl`是基类的复合控件，此参数使用所需的包含控件的资源 ID。 在其他情况下，使用任意的正整数。  
  
 `T`  
 用户的类，该类派生自`IDispEventSimpleImpl`。  
  
 `pdiid`  
 指向此类实现的事件显示接口的 IID 的指针。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|建立与默认事件源的连接。|  
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|建立与事件源的连接。|  
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|断开与事件源的连接。|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|返回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|返回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|返回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::Invoke](#invoke)|调用的事件处理程序列出在事件接收器映射。|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|断开与默认事件源的连接。|  
  
## <a name="remarks"></a>备注  
 `IDispEventSimpleImpl` 提供一种而无需实现事件显示接口的方式，提供在该接口上每个方法/事件的实现代码。 `IDispEventSimpleImpl` 提供的实现`IDispatch`方法。 只需提供你有兴趣处理的事件的实现。  
  
 `IDispEventSimpleImpl` 与你的类将事件路由到适当的处理程序函数中的事件接收器映射结合工作。 若要使用此类：  
  
-   添加[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)宏为你想要处理的每个对象每个事件的事件接收器映射。  
  
-   通过将传递指向的指针提供每个事件的类型信息[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构作为参数传递给每个条目。 在 x86 平台，`_ATL_FUNC_INFO.cc`值必须 CC_CDECL 与调用 __stdcall 方法的回调函数。  
  
-   调用[DispEventAdvise](#dispeventadvise)建立源对象和基的类之间的连接。  
  
-   调用[DispEventUnadvise](#dispeventunadvise)以断开的连接。  
  
 你必须从中派生`IDispEventSimpleImpl`(使用的唯一值`nID`) 为每个需要处理事件的对象。 通过与一个源对象对不同的源对象，然后告知取消通知，可以重用的基类，但可以由单个对象一次处理的源对象的最大数目限制数`IDispEventSimpleImpl`基类。  
  
 **IDispEventSimplImpl**提供与相同的功能[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)，但它不获取从类型库的接口的类型信息。 向导生成代码仅基于`IDispEventImpl`，但你可以使用`IDispEventSimpleImpl`通过手动添加代码。 使用`IDispEventSimpleImpl`时，你不具有描述事件接口的类型库，或者想要避免与使用类型库关联的开销。  
  
> [!NOTE]
> `IDispEventImpl` 和`IDispEventSimpleImpl`提供其自己实现**iunknown:: Queryinterface**启用每个`IDispEventImpl`或`IDispEventSimpleImpl`基类，以同时仍然允许对中的类成员的直接访问充当一个单独的 COM 标识你主要的 COM 对象。  
  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值 HRESULT 或从事件处理程序方法; void任何其他返回值不受支持，而且其行为是不确定。  
  
 有关详细信息，请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlcom.h  
  
##  <a name="advise"></a>  IDispEventSimpleImpl::Advise  
 调用此方法以建立与所表示的事件源的连接*pUnk*。  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向的指针**IUnknown**事件源对象的接口。  
  
### <a name="return-value"></a>返回值  
 `S_OK` 或任何失败`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 一旦建立连接时，事件将触发从*pUnk*将路由到在你通过事件接收器映射的类中处理程序。  
  
> [!NOTE]
>  如果你的类派生自多个`IDispEventSimpleImpl`类，你将需要区分调用此方法的范围与特定基类你感兴趣的调用。  
  
 `Advise` 建立的连接与默认的事件源，它所获取的默认事件源的对象所确定的那样 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。  
  
##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise  
 调用此方法以建立与所表示的事件源的连接*pUnk*。  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向的指针**IUnknown**事件源对象的接口。  
  
 `piid`  
 指向 IID 的事件源对象的指针。  
  
### <a name="return-value"></a>返回值  
 `S_OK` 或任何失败`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 随后，事件触发从*pUnk*将路由到在你通过事件接收器映射的类中处理程序。  
  
> [!NOTE]
>  如果你的类派生自多个`IDispEventSimpleImpl`类，你将需要区分调用此方法的范围与特定基类你感兴趣的调用。  
  
 `DispEventAdvise` 建立与中指定的事件源的连接`pdiid`。  
  
##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise  
 断开与所表示的事件源的连接*pUnk*。  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向的指针**IUnknown**事件源对象的接口。  
  
 `piid`  
 指向 IID 的事件源对象的指针。  
  
### <a name="return-value"></a>返回值  
 `S_OK` 或任何失败`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 一旦连接已断开，事件将无法再路由到列出在事件接收器映射的处理程序函数。  
  
> [!NOTE]
>  如果你的类派生自多个`IDispEventSimpleImpl`类，你将需要区分调用此方法的范围与特定基类你感兴趣的调用。  
  
 `DispEventAdvise` 中断已建立与中指定的事件源的连接`pdiid`。  
  
##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames  
 此实现的**IDispatch::GetIDsOfNames**返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) Windows SDK 中。  
  
##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo  
 此实现的**IDispatch::GetTypeInfo**返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) Windows SDK 中。  
  
##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount  
 此实现的**IDispatch::GetTypeInfoCount**返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) Windows SDK 中。  
  
##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke  
 此实现的**idispatch:: Invoke**调用事件处理程序列出在事件接收器映射。  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise  
 断开与所表示的事件源的连接*pUnk*。  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向的指针**IUnknown**事件源对象的接口。  
  
### <a name="return-value"></a>返回值  
 `S_OK` 或任何失败`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 一旦连接已断开，事件将无法再路由到列出在事件接收器映射的处理程序函数。  
  
> [!NOTE]
>  如果你的类派生自多个`IDispEventSimpleImpl`类，你将需要区分调用此方法的范围与特定基类你感兴趣的调用。  
  
 `Unadvise` 中断已建立与中指定的默认事件源的连接`pdiid`。  
  
 **Unavise**与默认事件源的连接中断，它获取的默认事件源的对象所确定的那样 IID [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface)。  
  
## <a name="see-also"></a>请参阅  
 [_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl 类](../../atl/reference/idispeventimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [类概述](../../atl/atl-class-overview.md)
