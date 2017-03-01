---
title: "IDispEventSimpleImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATL::IDispEventSimpleImpl
- ATL.IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
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
ms.openlocfilehash: 6b7bc2c64139726f84f1c19c7d6b40e8d68cdc18
ms.lasthandoff: 02/24/2017

---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl 类
此类提供的实现`IDispatch`方法，而不从类型库中获取类型信息。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>参数  
 `nID`  
 源对象的唯一标识符。 当`IDispEventSimpleImpl`类的基类的复合控件，为此参数使用所需的所包含控件的资源 ID。 在其他情况下，使用任意的正整数。  
  
 `T`  
 用户的类，该类派生自`IDispEventSimpleImpl`。  
  
 `pdiid`  
 此类实现的事件调度接口的 IID 指向的指针。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|建立与默认事件源的连接。|  
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|建立与事件源的连接。|  
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|断开与事件源的连接。|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|返回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|返回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|返回**E_NOTIMPL**。|  
|[IDispEventSimpleImpl::Invoke](#invoke)|调用事件处理程序列出在事件接收器映射。|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|断开与默认事件源的连接。|  
  
## <a name="remarks"></a>备注  
 `IDispEventSimpleImpl`提供了而无需实现事件调度接口方法，用于提供在该接口上每个方法/事件的实现代码。 `IDispEventSimpleImpl`提供的实现`IDispatch`方法。 只需提供有关您感兴趣处理的事件的实现。  
  
 `IDispEventSimpleImpl`配合使用[事件接收器映射](http://msdn.microsoft.com/library/32542b3d-ac43-4139-8ac4-41c48481744f)在您的类事件路由到相应的处理程序函数。 若要使用此类︰  
  
-   添加[SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)宏到想要处理的每个对象每个事件的事件接收器映射。  
  
-   通过将传递一个指向提供每个事件的类型信息[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)以参数形式向每个条目的结构。 在 x86 平台，`_ATL_FUNC_INFO.cc`值必须是 CC_CDECL 调用 __stdcall 方法的回调函数。  
  
-   调用[DispEventAdvise](#dispeventadvise)之间建立连接的源对象和类的基类。  
  
-   调用[DispEventUnadvise](#dispeventunadvise)断开连接。  
  
 你必须从中派生`IDispEventSimpleImpl`(使用的值是唯一`nID`) 为每个对象，您需要处理的事件。 通过对一个源对象对不同的源对象，然后告知取消通知，可以重用类的基类，但可以一次处理由单个对象的源对象的最大数目限制数`IDispEventSimpleImpl`基类。  
  
 **IDispEventSimplImpl**提供相同的功能[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)，只是它不会从类型库的接口的类型信息。 向导生成代码仅在基于`IDispEventImpl`，但您可以使用`IDispEventSimpleImpl`通过手动添加代码。 使用`IDispEventSimpleImpl`时您不具有一个类型库描述事件接口，或者想要避免与使用类型库相关联的系统开销。  
  
> [!NOTE]
> `IDispEventImpl`和`IDispEventSimpleImpl`提供其自己的实现**iunknown:: Queryinterface**启用每个`IDispEventImpl`或`IDispEventSimpleImpl`基类，以作为单独的 COM 标识，同时仍然允许对类成员的直接访问主要的 COM 对象中。  
  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或从你的事件处理程序方法; void任何其他返回值是不受支持，而且其行为是不确定。  
  
 有关详细信息，请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-nameadvisea--idispeventsimpleimpladvise"></a><a name="advise"></a>IDispEventSimpleImpl::Advise  
 调用此方法以建立与由事件源的连接*pUnk*。  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]一个指向**IUnknown**事件源对象的接口。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果出现任何故障或`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 一旦建立连接时，事件将触发从*pUnk*将路由到处理程序在您通过事件接收器映射的类。  
  
> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要通过作用域与特定基类您感兴趣的呼叫消除歧义调用此方法。  
  
 `Advise`建立的连接与默认的事件源，它将获取由该对象的默认事件源的 IID [AtlGetObjectSourceInterface](http://msdn.microsoft.com/library/a8528f45-fbfb-4e24-ad1a-1d69b2897155)。  
  
##  <a name="a-namedispeventadvisea--idispeventsimpleimpldispeventadvise"></a><a name="dispeventadvise"></a>IDispEventSimpleImpl::DispEventAdvise  
 调用此方法以建立与由事件源的连接*pUnk*。  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]一个指向**IUnknown**事件源对象的接口。  
  
 `piid`  
 指向 IID 事件源对象的指针。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果出现任何故障或`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 随后，事件触发从*pUnk*将路由到处理程序在您通过事件接收器映射的类。  
  
> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要通过作用域与特定基类您感兴趣的呼叫消除歧义调用此方法。  
  
 `DispEventAdvise`建立的连接中指定的事件源与`pdiid`。  
  
##  <a name="a-namedispeventunadvisea--idispeventsimpleimpldispeventunadvise"></a><a name="dispeventunadvise"></a>IDispEventSimpleImpl::DispEventUnadvise  
 断开与所表示的事件源的连接*pUnk*。  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]一个指向**IUnknown**事件源对象的接口。  
  
 `piid`  
 指向 IID 事件源对象的指针。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果出现任何故障或`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 断开该连接后，事件将不会再路由到事件接收器映射中列出的处理程序函数。  
  
> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要通过作用域与特定基类您感兴趣的呼叫消除歧义调用此方法。  
  
 `DispEventAdvise`将中断与中指定的事件源建立的连接`pdiid`。  
  
##  <a name="a-namegetidsofnamesa--idispeventsimpleimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventSimpleImpl::GetIDsOfNames  
 这种实现**IDispatch::GetIDsOfNames**返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfoa--idispeventsimpleimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventSimpleImpl::GetTypeInfo  
 这种实现**IDispatch::GetTypeInfo**返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegettypeinfocounta--idispeventsimpleimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventSimpleImpl::GetTypeInfoCount  
 这种实现**IDispatch::GetTypeInfoCount**返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameinvokea--idispeventsimpleimplinvoke"></a><a name="invoke"></a>IDispEventSimpleImpl::Invoke  
 这种实现**idispatch:: Invoke**调用事件处理程序列出在事件接收器映射。  
  
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
  
##  <a name="a-nameunadvisea--idispeventsimpleimplunadvise"></a><a name="unadvise"></a>IDispEventSimpleImpl::Unadvise  
 断开与所表示的事件源的连接*pUnk*。  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]一个指向**IUnknown**事件源对象的接口。  
  
### <a name="return-value"></a>返回值  
 `S_OK`如果出现任何故障或`HRESULT`值。  
  
### <a name="remarks"></a>备注  
 断开该连接后，事件将不会再路由到事件接收器映射中列出的处理程序函数。  
  
> [!NOTE]
>  如果您的类派生自多个`IDispEventSimpleImpl`类，您将需要通过作用域与特定基类您感兴趣的呼叫消除歧义调用此方法。  
  
 `Unadvise`将中断与中指定的默认事件源建立的连接`pdiid`。  
  
 **Unavise**与默认事件源的连接中断，它将获取由该对象的默认事件源的 IID [AtlGetObjectSourceInterface](http://msdn.microsoft.com/library/a8528f45-fbfb-4e24-ad1a-1d69b2897155)。  
  
## <a name="see-also"></a>另请参阅  
 [_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl 类](../../atl/reference/idispeventimpl-class.md)   
 [SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)   
 [类概述](../../atl/atl-class-overview.md)

