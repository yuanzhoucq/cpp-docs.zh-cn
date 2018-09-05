---
title: IViewObjectExImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d47c017a178d0a222780532b74db4135447f062
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760443"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 类

此类实现`IUnknown`并提供的默认实现[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject)， [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2)，并且[IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex)接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```

#### <a name="parameters"></a>参数

*T*  
您的类，派生自`IViewObjectExImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|绘制到设备上下文上的控件的表示形式。|
|[IViewObjectExImpl::Freeze](#freeze)|冻结控件绘制表示形式，因此它不会更改直到`Unfreeze`。 ATL 实现返回 E_NOTIMPL。|
|[IViewObjectExImpl::GetAdvise](#getadvise)|如果有一个，检索现有的通知接收器连接在控件上。|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|返回由该控件用于绘图的逻辑调色板。 ATL 实现返回 E_NOTIMPL。|
|[IViewObjectExImpl::GetExtent](#getextent)|检索以 HIMETRIC 为单位 （每个单位为 0.01 毫米） 的控件的显示大小从控件类数据成员[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供要使用，因为在用户调整它的对象的容器的大小调整提示。|
|[IViewObjectExImpl::GetRect](#getrect)|返回描述请求的绘图方位的矩形。 ATL 实现返回 E_NOTIMPL。|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|返回对象和支持的哪些绘图方位的信息不透明度。|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|如果指定的点在指定的矩形，并返回将检查[HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult)中的值`pHitResult`。|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|检查是否显示控件的矩形重叠指定的位置矩形中的任何点，并返回中的 HITRESULT 值`pHitResult`。|
|[IViewObjectExImpl::SetAdvise](#setadvise)|设置控件和通知接收器之间的连接，以便可以在控件的视图中的更改通知接收器。|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|取消冻结该控件的绘制表示形式。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject)， [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2)，并[IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex)接口可以使控件以显示本身直接，还可以创建和管理通知接收器通知容器中的控件显示的更改。 `IViewObjectEx`接口扩展的控件功能，如闪烁绘图、 非矩形的透明控件和命中测试 （例如，如何关闭鼠标单击必须要考虑在控件上) 提供支持。 类`IViewObjectExImpl`提供默认实现这些接口并实现`IUnknown`信息发送给转储调试中的设备生成。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

绘制到设备上下文上的控件的表示形式。

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

此方法调用`CComControl::OnDrawAdvanced`从而又会调用您的控件类的`OnDraw`方法。 `OnDraw`方法自动添加到你的控件类，当使用 ATL 控件向导创建您的控件。 向导的默认`OnDraw`用"ATL 3.0"的标签绘制矩形。

请参阅[iviewobject:: Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw) Windows SDK 中。

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

冻结控件绘制表示形式，因此它不会更改直到`Unfreeze`。 ATL 实现返回 E_NOTIMPL。

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>备注

请参阅[IViewObject::Freeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-freeze) Windows SDK 中。

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

如果有一个，检索现有的通知接收器连接在控件上。

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>备注

在控件类数据成员中存储的通知接收器[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。

请参阅[IViewObject::GetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getadvise) Windows SDK 中。

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

返回由该控件用于绘图的逻辑调色板。 ATL 实现返回 E_NOTIMPL。

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

请参阅[IViewObject::GetColorSet](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getcolorset) Windows SDK 中。

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

检索以 HIMETRIC 为单位 （每个单位为 0.01 毫米） 的控件的显示大小从控件类数据成员[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>备注

请参阅[IViewObject2::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-iviewobject2-getextent) Windows SDK 中。

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

提供要使用，因为在用户调整它的对象的容器的大小调整提示。

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

如果`dwAspect`是 DVASPECT_CONTENT 并*pExtentInfo-> dwExtentMode* DVEXTENT_CONTENT，设置 *`psizel`到控件类数据成员[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否则，返回的错误 HRESULT。

请参阅[IViewObjectEx::GetNaturalExtent](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) Windows SDK 中。

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

返回描述请求的绘图方位的矩形。 ATL 实现返回 E_NOTIMPL。

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>备注

请参阅[IViewObjectEx::GetRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getrect) Windows SDK 中。

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

返回对象和支持的哪些绘图方位的信息不透明度。

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>备注

默认情况下，设置 ATL`pdwStatus`以指示该控件支持 VIEWSTATUS_OPAQUE (在可能的值为[VIEWSTATUS](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus)枚举)。

请参阅[IViewObjectEx::GetViewStatus](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) Windows SDK 中。

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

如果指定的点在指定的矩形，并返回将检查[HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult)中的值`pHitResult`。

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>备注

值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`等于[DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect)，该方法将返回 S_OK。 否则，该方法返回 E_FAIL。

请参阅[IViewObjectEx::QueryHitPoint](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) Windows SDK 中。

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

检查是否显示控件的矩形重叠指定的位置矩形中的任何点，并返回[HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult)中的值`pHitResult`。

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>备注

值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`等于[DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect)，该方法将返回 S_OK。 否则，该方法返回 E_FAIL。

请参阅[IViewObjectEx::QueryHitRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) Windows SDK 中。

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

设置控件和通知接收器之间的连接，以便可以在控件的视图中的更改通知接收器。

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>备注

指向指针[IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink)通知接收器上的接口存储在控件类数据成员[CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。  

请参阅[IViewObject::SetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-setadvise) Windows SDK 中。

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

取消冻结该控件的绘制表示形式。 ATL 实现返回 E_NOTIMPL。

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>备注

请参阅[IViewObject::Unfreeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-unfreeze) Windows SDK 中。

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

实现此方法以关闭与此对象关联的句柄。

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>参数

*hHandle*  
要关闭句柄。

### <a name="return-value"></a>返回值

返回成功或失败时的错误 HRESULT，则为 S_OK。

### <a name="remarks"></a>备注

传递给此方法的句柄是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>示例

下面的代码演示的简单实现`IWorkerThreadClient::CloseHandle`。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

实现此方法以执行代码时与此对象关联的句柄发出信号。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>参数

*dwParam*  
User 参数中。

*hObject*  
已收到信号的句柄。

### <a name="return-value"></a>返回值

返回成功或失败时的错误 HRESULT，则为 S_OK。

### <a name="remarks"></a>备注

句柄和双字节/指针传递给此方法是以前通过调用与此对象关联[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

### <a name="example"></a>示例

下面的代码演示的简单实现`IWorkerThreadClient::Execute`。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)   
[ActiveX 控件接口](/windows/desktop/com/activex-controls-interfaces)   
[教程](../../atl/active-template-library-atl-tutorial.md)   
[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)   
[类概述](../../atl/atl-class-overview.md)
