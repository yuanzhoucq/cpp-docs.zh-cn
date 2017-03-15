---
title: "IDispEventImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
caps.latest.revision: 22
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
ms.openlocfilehash: 235955f8573ae7e430be3de2a96efdd7496d15de
ms.lasthandoff: 02/24/2017

---
# <a name="idispeventimpl-class"></a>IDispEventImpl 类
此类提供的实现`IDispatch`方法。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
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
 源对象的唯一标识符。 当`IDispEventImpl`类的基类的复合控件，为此参数使用所需的所包含控件的资源 ID。 在其他情况下，使用任意的正整数。  
  
 `T`  
 用户的类，该类派生自`IDispEventImpl`。  
  
 `pdiid`  
 此类实现的事件调度接口的 IID 指向的指针。 此接口必须由表示的类型库中定义`plibid`， `wMajor`，和`wMinor`。  
  
 `plibid`  
 对类型库，它定义调度接口指针指向的`pdiid`。 如果**& GUID_NULL**，将从采购事件的对象加载类型库。  
  
 `wMajor`  
 类型库的主要版本。 默认值为 0。  
  
 `wMinor`  
 类型库的次要版本。 默认值为 0。  
  
 `tihclass`  
 用于管理的类型信息的类`T`。 默认值为类型的类`CComTypeInfoHolder`; 但是，可以通过以外提供一种类型的类中替代此模板参数`CComTypeInfoHolder`。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|用于管理的类型信息的类。 默认情况下， `CComTypeInfoHolder`。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|查找函数索引为指定的调度标识符。|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|将单个成员和一组可选的参数名称映射到对应的一组整数 Dispid。|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|检索对象的类型信息。|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|检索类型信息接口的数量。|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|检索的用户定义的类型的基本类型。|  
  
## <a name="remarks"></a>备注  
 `IDispEventImpl`提供了而无需实现事件调度接口方法，用于提供在该接口上每个方法/事件的实现代码。 `IDispEventImpl`提供的实现`IDispatch`方法。 只需提供有关您感兴趣处理的事件的实现。  
  
 `IDispEventImpl`配合使用[事件接收器映射](http://msdn.microsoft.com/library/32542b3d-ac43-4139-8ac4-41c48481744f)在您的类事件路由到相应的处理程序函数。 若要使用此类︰  
  

 添加[SINK_ENTRY](http://msdn.microsoft.com/library/33a5fff6-5248-47c0-8cf4-8bdf760e86e5)或[SINK_ENTRY_EX](http://msdn.microsoft.com/library/e1d14342-838f-4791-ac2f-5dae2801c1ac)宏到想要处理的每个对象每个事件的事件接收器映射。 当使用`IDispEventImpl`为复合控件的基类的类，您可以调用[AtlAdviseSinkMap](http://msdn.microsoft.com/library/0757a6af-3de3-4179-8b4f-ccd137d919b4)建立并断开与事件源的连接的所有项在事件都接收器映射。 在其他情况下，或者对于更好地控制，调用[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)之间建立连接的源对象和类的基类。 调用[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)断开连接。  

  
 你必须从中派生`IDispEventImpl`(使用的值是唯一`nID`) 为每个对象，您需要处理的事件。 通过对一个源对象对不同的源对象，然后告知取消通知，可以重用类的基类，但可以一次处理由单个对象的源对象的最大数目限制数`IDispEventImpl`基类。  
  
 `IDispEventImpl`提供与相同的功能[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)，只是它从类型库，而无需则提供该数据作为指针来获取接口的类型信息[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)结构。 使用`IDispEventSimpleImpl`时您不具有一个类型库描述事件接口或不想以避免与使用类型库相关的开销。  
  
> [!NOTE]
> `IDispEventImpl`和`IDispEventSimpleImpl`提供其自己的实现**iunknown:: Queryinterface**启用每个`IDispEventImpl`和`IDispEventSimpleImpl`基类，以作为单独的 COM 标识，同时仍然允许对类成员的直接访问主要的 COM 对象中。  
  
 CE ATL 实现 ActiveX 事件接收器仅支持返回类型的值的 HRESULT 或从你的事件处理程序方法; void任何其他返回值是不受支持，而且其行为是不确定。  
  
 有关详细信息，请参阅[支持 IDispEventImpl](../../atl/supporting-idispeventimpl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcom.h  
  
##  <a name="a-namegetfuncinfofromida--idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId  
 查找函数索引为指定的调度标识符。  
  
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
 [in]结构，该值指示该函数的调用方式。  
  
### <a name="return-value"></a>返回值  
 标准 `HRESULT` 值。  
  
##  <a name="a-namegetidsofnamesa--idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames  
 将单个成员和一组可选的参数名称映射到对应的一组整数 Dispid，可以在后续调用使用[idispatch:: Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d)。  
  
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
  
##  <a name="a-namegettypeinfoa--idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo  
 检索对象的类型信息，然后可以使用该信息获取接口的类型信息。  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettypeinfocounta--idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount  
 检索对象提供的类型信息接口的数量（0 或 1）。  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetuserdefinedtypea--idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType  
 检索的用户定义的类型的基本类型。  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>参数  
 `pTI`  
 [in]一个指向[ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680)包含用户定义类型的接口。  
  
 *hrt*  
 [in]要检索的类型说明句柄。  
  
### <a name="return-value"></a>返回值  
 变量的类型。  
  
### <a name="remarks"></a>备注  
 请参阅[ITypeInfo::GetRefTypeInfo](http://msdn.microsoft.com/en-us/61d3b31d-6591-4e55-9e82-5246a168be00)。  
  
##  <a name="a-nameidispeventimpla--idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl  
 构造函数。 存储类模板参数的值`plibid`， `pdiid`， `wMajor`，和`wMinor`。  
  
```
IDispEventImpl();
```  
  
##  <a name="a-nametihclassa--idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl::tihclass  
 此 typedef 是类模板参数实例`tihclass`。  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>备注  
 默认情况下，此类是`CComTypeInfoHolder`。 `CComTypeInfoHolder`管理类的类型信息。  
  
## <a name="see-also"></a>另请参阅  
 [_ATL_FUNC_INFO 结构](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl 类](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl 类](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](http://msdn.microsoft.com/library/33a5fff6-5248-47c0-8cf4-8bdf760e86e5)   
 [SINK_ENTRY_EX](http://msdn.microsoft.com/library/e1d14342-838f-4791-ac2f-5dae2801c1ac)   
 [SINK_ENTRY_INFO](http://msdn.microsoft.com/library/1a0ae260-2c82-4926-a537-db01e5f206a7)   
 [类概述](../../atl/atl-class-overview.md)
