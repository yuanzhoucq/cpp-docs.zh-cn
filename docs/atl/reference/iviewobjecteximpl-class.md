---
title: "IViewObjectExImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: abee30f798f6d6ee062b916d1aa23bcfc5c271cb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 类
此类实现**IUnknown**并提供的默认实现[IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)接口。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 你的类，派生自`IViewObjectExImpl`。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](#draw)|绘制控件拖到设备上下文的表示形式。|  
|[IViewObjectExImpl::Freeze](#freeze)|冻结控件的绘制的表示，因此它不会更改直到`Unfreeze`。 ATL 实现返回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetAdvise](#getadvise)|如果存在，请检索在控件上，现有的通知接收器连接。|  
|[IViewObjectExImpl::GetColorSet](#getcolorset)|返回由该控件用于绘图逻辑调色板。 ATL 实现返回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetExtent](#getextent)|从控件类数据成员中检索以 himetric 为单位 （每个单位 0.01 毫米） 的控件的显示大小[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。|  
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供从对象以用作用户调整其大小时的容器的大小调整提示。|  
|[IViewObjectExImpl::GetRect](#getrect)|返回描述请求的绘图方位矩形。 ATL 实现返回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|返回有关不透明度的对象，并且支持绘制方面的信息。|  
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|检查是否指定的点中指定的矩形，并返回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)中的值`pHitResult`。|  
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|检查是否控件的显示矩形重叠的指定的位置的矩形中的任何点，并返回**HITRESULT**中的值`pHitResult`。|  
|[IViewObjectExImpl::SetAdvise](#setadvise)|设置在控件和通知接收器之间的连接，以便可以中控件的视图的更改通知接收器。|  
|[IViewObjectExImpl::Unfreeze](#unfreeze)|取消冻结该控件的绘制的表示。 ATL 实现返回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>备注  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)接口可以使一个控件，以将它直接，显示用于创建和管理建议接收器通知控件显示中的更改的容器。 **IViewObjectEx**接口提供支持扩展的控件功能，如闪烁绘制、 非矩形的透明控件和命中测试 （例如，如何关闭鼠标单击必须视为上控制）。 类`IViewObjectExImpl`提供这些接口的默认实现，并实现**IUnknown**信息发送给转储设备在调试生成。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## <a name="requirements"></a>要求  
 **标头：** atlctl.h  
  
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
 此方法调用**CComControl::OnDrawAdvanced**从而又会调用你的控件类`OnDraw`方法。 `OnDraw`方法自动添加到你的控件类，当使用 ATL 控件向导创建你的控件。 向导的默认`OnDraw`用标签"ATL 3.0"绘制矩形。  
  
 请参阅[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655) Windows SDK 中。  
  
##  <a name="freeze"></a>IViewObjectExImpl::Freeze  
 冻结控件的绘制的表示，因此它不会更改直到`Unfreeze`。 ATL 实现返回**E_NOTIMPL**。  
  
```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObject::Freeze](http://msdn.microsoft.com/library/windows/desktop/ms688728) Windows SDK 中。  
  
##  <a name="getadvise"></a>IViewObjectExImpl::GetAdvise  
 如果存在，请检索在控件上，现有的通知接收器连接。  
  
```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```  
  
### <a name="remarks"></a>备注  
 在控件类数据成员中存储通知接收器[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。  
  
 请参阅[IViewObject::GetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692772) Windows SDK 中。  
  
##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet  
 返回由该控件用于绘图逻辑调色板。 ATL 实现返回**E_NOTIMPL**。  
  
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
 请参阅[IViewObject::GetColorSet](http://msdn.microsoft.com/library/windows/desktop/ms686553) Windows SDK 中。  
  
##  <a name="getextent"></a>IViewObjectExImpl::GetExtent  
 从控件类数据成员中检索以 himetric 为单位 （每个单位 0.01 毫米） 的控件的显示大小[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。  
  
```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) Windows SDK 中。  
  
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
 如果`dwAspect`是`DVASPECT_CONTENT`和*pExtentInfo-> dwExtentMode*是**DVEXTENT_CONTENT**，设置 *`psizel`到控件类的数据成员[CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否则，返回错误`HRESULT`。  
  
 请参阅[IViewObjectEx::GetNaturalExtent](http://msdn.microsoft.com/library/windows/desktop/ms683718) Windows SDK 中。  
  
##  <a name="getrect"></a>IViewObjectExImpl::GetRect  
 返回描述请求的绘图方位矩形。 ATL 实现返回**E_NOTIMPL**。  
  
```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObjectEx::GetRect](http://msdn.microsoft.com/library/windows/desktop/ms695246) Windows SDK 中。  
  
##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus  
 返回有关不透明度的对象，并且支持绘制方面的信息。  
  
```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>备注  
 默认情况下，ATL 设置`pdwStatus`以指示该控件支持**VIEWSTATUS_OPAQUE** (可能的值位于[VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)枚举)。  
  
 请参阅[IViewObjectEx::GetViewStatus](http://msdn.microsoft.com/library/windows/desktop/ms693371) Windows SDK 中。  
  
##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint  
 检查是否指定的点中指定的矩形，并返回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)中的值`pHitResult`。  
  
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
  
 请参阅[IViewObjectEx::QueryHitPoint](http://msdn.microsoft.com/library/windows/desktop/ms691209) Windows SDK 中。  
  
##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect  
 检查是否控件的显示矩形重叠的指定的位置的矩形中的任何点，并返回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)中的值`pHitResult`。  
  
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
  
 请参阅[IViewObjectEx::QueryHitRect](http://msdn.microsoft.com/library/windows/desktop/ms693797) Windows SDK 中。  
  
##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise  
 设置在控件和通知接收器之间的连接，以便可以中控件的视图的更改通知接收器。  
  
```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```  
  
### <a name="remarks"></a>备注  

 将指针与[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)在控件类数据成员中存储上通知接收器接口[CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。  

  
 请参阅[IViewObject::SetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms683950) Windows SDK 中。  
  
##  <a name="unfreeze"></a>IViewObjectExImpl::Unfreeze  
 取消冻结该控件的绘制的表示。 ATL 实现返回**E_NOTIMPL**。  
  
```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```  
  
### <a name="remarks"></a>备注  
 请参阅[IViewObject::Unfreeze](http://msdn.microsoft.com/library/windows/desktop/ms686641) Windows SDK 中。  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 实现此方法来关闭与此对象关联的句柄。  
  
```
HRESULT CloseHandle(HANDLE hHandle);
```  
  
### <a name="parameters"></a>参数  
 *hHandle*  
 要关闭的句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则失败的错误 HRESULT，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 传递给此方法的句柄已以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 实现此方法可执行代码时与此对象关联的句柄将被发送信号。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>参数  
 `dwParam`  
 用户参数中。  
  
 `hObject`  
 变为终止状态句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则失败的错误 HRESULT，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 以前通过调用与此对象关联的句柄和 DWORD/指针传递给此方法了[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>示例  
 下面的代码演示的简单实现`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CComControl 类](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 控件接口](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [教程](../../atl/active-template-library-atl-tutorial.md)   
 [创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
 [类概述](../../atl/atl-class-overview.md)
