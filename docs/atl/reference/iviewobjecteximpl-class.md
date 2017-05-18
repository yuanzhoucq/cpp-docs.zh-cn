---
title: "IViewObjectExImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 2b585a056324507cc631e64e6dbe9d0ed610361d
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 类
此类实现**IUnknown**并提供的默认实现[IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)接口。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 您的类，派生自`IViewObjectExImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](#draw)|绘制控件拖到设备上下文的表示形式。|  
|[IViewObjectExImpl::Freeze](#freeze)|冻结一个控件的绘制的表示，因此它不会更改直到`Unfreeze`。 ATL 实现返回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetAdvise](#getadvise)|如果有一个，检索的控件上，现有的通知接收器连接。|  
|[IViewObjectExImpl::GetColorSet](#getcolorset)|返回由该控件用于绘图的逻辑调色板。 ATL 实现返回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetExtent](#getextent)|从控件类数据成员中检索以 himetric 为单位 （每个单元&0;.01 毫米） 的控件的显示大小[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。|  
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供从对象以用作用户调整其大小时的容器的大小调整提示。|  
|[IViewObjectExImpl::GetRect](#getrect)|返回描述请求的绘图方位的矩形。 ATL 实现返回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|返回的对象以及支持哪些绘制方面的信息不透明度。|  
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|检查指定的点是否为指定的矩形，并返回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)中的值`pHitResult`。|  
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|检查是否显示控件的矩形重叠的指定的位置的矩形中的任何位置，并返回**HITRESULT**中的值`pHitResult`。|  
|[IViewObjectExImpl::SetAdvise](#setadvise)|设置该控件和通知接收器之间的连接，所以接收器可以通知有关控件的视图中的更改。|  
|[IViewObjectExImpl::Unfreeze](#unfreeze)|取消冻结该控件的绘制的表示。 ATL 实现返回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>备注  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)接口可以使控件以将它直接显示，并可创建和管理通知接收器以通知容器中控件显示的更改。 **IViewObjectEx**接口扩展的控件之类的功能无闪烁绘图、 非矩形和透明控件和命中测试 （例如，如何关闭鼠标单击必须要考虑在控件上) 提供支持。 类`IViewObjectExImpl`提供这些接口的默认实现，并实现**IUnknown**中调试设备信息发送给转储生成。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlctl.h  
  
##  <a name="draw"></a>IViewObjectExImpl::Draw  
 绘制控件拖到设备上下文的表示形式。  
  
```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```  
  
### <a name="remarks"></a>备注  
 此方法调用**CComControl::OnDrawAdvanced**从而又会调用您的控件类`OnDraw`方法。 `OnDraw`方法自动添加到您的控件类，当使用 ATL 控件向导创建您的控件。 在此向导的默认`OnDraw`绘制一个矩形，有标签"ATL 3.0"。  
  
 请参阅[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="freeze"></a>IViewObjectExImpl::Freeze  
 冻结一个控件的绘制的表示，因此它不会更改直到`Unfreeze`。 ATL 实现返回**E_NOTIMPL**。  
  
```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObject::Freeze](http://msdn.microsoft.com/library/windows/desktop/ms688728)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getadvise"></a>IViewObjectExImpl::GetAdvise  
 如果有一个，检索的控件上，现有的通知接收器连接。  
  
```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```  
  
### <a name="remarks"></a>备注  
 在控件类数据成员中存储通知接收器[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。  
  
 请参阅[IViewObject::GetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692772)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet  
 返回由该控件用于绘图的逻辑调色板。 ATL 实现返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObject::GetColorSet](http://msdn.microsoft.com/library/windows/desktop/ms686553)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getextent"></a>IViewObjectExImpl::GetExtent  
 从控件类数据成员中检索以 himetric 为单位 （每个单元&0;.01 毫米） 的控件的显示大小[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。  
  
```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent  
 提供从对象以用作用户调整其大小时的容器的大小调整提示。  
  
```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```  
  
### <a name="remarks"></a>备注  
 如果`dwAspect`是`DVASPECT_CONTENT`和*-> dwExtentMode pExtentInfo*是**DVEXTENT_CONTENT**，设置 *`psizel`绑定到控件类数据成员[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否则，将返回错误`HRESULT`。  
  
 请参阅[IViewObjectEx::GetNaturalExtent](http://msdn.microsoft.com/library/windows/desktop/ms683718)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getrect"></a>IViewObjectExImpl::GetRect  
 返回描述请求的绘图方位的矩形。 ATL 实现返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObjectEx::GetRect](http://msdn.microsoft.com/library/windows/desktop/ms695246)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus  
 返回的对象以及支持哪些绘制方面的信息不透明度。  
  
```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>备注  
 默认情况下，ATL 设置`pdwStatus`以指示该控件支持**VIEWSTATUS_OPAQUE** (可能的值是在[VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)枚举)。  
  
 请参阅[IViewObjectEx::GetViewStatus](http://msdn.microsoft.com/library/windows/desktop/ms693371)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint  
 检查指定的点是否为指定的矩形，并返回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)中的值`pHitResult`。  
  
```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>备注  
 值可以是**HITRESULT_HIT**或**HITRESULT_OUTSIDE**。  
  
 如果`dwAspect`等于[DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318)，该方法返回`S_OK`。 否则，该方法返回**E_FAIL**。  
  
 请参阅[IViewObjectEx::QueryHitPoint](http://msdn.microsoft.com/library/windows/desktop/ms691209)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect  
 检查是否显示控件的矩形重叠的指定的位置的矩形中的任何位置，并返回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)中的值`pHitResult`。  
  
```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>备注  
 值可以是**HITRESULT_HIT**或**HITRESULT_OUTSIDE**。  
  
 如果`dwAspect`等于[DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318)，该方法返回`S_OK`。 否则，该方法返回**E_FAIL**。  
  
 请参阅[IViewObjectEx::QueryHitRect](http://msdn.microsoft.com/library/windows/desktop/ms693797)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise  
 设置该控件和通知接收器之间的连接，所以接收器可以通知有关控件的视图中的更改。  
  
```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```  
  
### <a name="remarks"></a>备注  

 将指针与[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)通知接收器上的接口存储在控件类数据成员中[CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。  

  
 请参阅[IViewObject::SetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms683950)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="unfreeze"></a>IViewObjectExImpl::Unfreeze  
 取消冻结该控件的绘制的表示。 ATL 实现返回**E_NOTIMPL**。  
  
```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObject::Unfreeze](http://msdn.microsoft.com/library/windows/desktop/ms686641)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 实现此方法以关闭与此对象关联的句柄。  
  
```
HRESULT CloseHandle(HANDLE hHandle);
```  
  
### <a name="parameters"></a>参数  
 *hHandle*  
 要关闭句柄。  
  
### <a name="return-value"></a>返回值  
 在成功或失败的错误 HRESULT 返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 传递给此方法的句柄是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities #&135;](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 实现此方法时要执行的代码与此对象关联的句柄将被发送信号。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>参数  
 `dwParam`  
 对 user 参数。  
  
 `hObject`  
 已发送信号的句柄。  
  
### <a name="return-value"></a>返回值  
 在成功或失败的错误 HRESULT 返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 句柄和 DWORD/指针传递给此方法是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities #&136;](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 控件接口](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [教程](../../atl/active-template-library-atl-tutorial.md)   
 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
 [类概述](../../atl/atl-class-overview.md)

