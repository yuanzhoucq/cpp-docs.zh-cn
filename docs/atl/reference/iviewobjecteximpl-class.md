---
title: IViewObjectExImpl 类
ms.date: 11/04/2016
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
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 3aead41f317d175eac9dcb094aa2070d82dc6185
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495500"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 类

此类实现`IUnknown`并提供[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)接口的默认实现。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IViewObjectExImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|在设备上下文中绘制控件的表示形式。|
|[IViewObjectExImpl::Freeze](#freeze)|冻结控件的绘制表示形式，以便在之前`Unfreeze`不会发生更改。 ATL 实现返回 E_NOTIMPL。|
|[IViewObjectExImpl::GetAdvise](#getadvise)|检索控件上的现有通知接收器连接（如果有）。|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|返回控件用于绘制的逻辑调色板。 ATL 实现返回 E_NOTIMPL。|
|[IViewObjectExImpl::GetExtent](#getextent)|从控件类数据成员[CComControlBase：： m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)按 HIMETRIC 单位（0.01 毫米/单位）检索控件的显示大小。|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供容器的大小调整提示，供对象在用户调整其大小时使用。|
|[IViewObjectExImpl::GetRect](#getrect)|返回描述所请求的绘图方位的矩形。 ATL 实现返回 E_NOTIMPL。|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|返回有关对象的不透明度和所支持的绘图方位的信息。|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|检查指定的点是否在指定的矩形中，并返回`pHitResult`中的 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 值。|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|检查控件的显示矩形是否与指定位置矩形中的任何点重叠，并返回中`pHitResult`的 HITRESULT 值。|
|[IViewObjectExImpl::SetAdvise](#setadvise)|设置控件和通知接收器之间的连接，以便可以通知接收器控件视图中的更改。|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Unfreezes 控件绘制的表示形式。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

使用[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)接口，控件可以直接显示自身，以及创建和管理建议接收器，以通知容器控件显示中的更改。 `IViewObjectEx`接口提供对扩展控制功能的支持，例如无闪烁的绘图、非矩形和透明的控件，以及命中测试（例如，必须在控件上考虑如何关闭鼠标单击）。 类`IViewObjectExImpl`提供这些接口的默认实现，并通过`IUnknown`在调试版本中将信息发送到转储设备来实现。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>要求

**标头：** atlctl

##  <a name="draw"></a>IViewObjectExImpl：:D raw

在设备上下文中绘制控件的表示形式。

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

此方法调用`CComControl::OnDrawAdvanced` ，进而调用控件类的`OnDraw`方法。 使用`OnDraw` ATL 控件向导创建控件时，会自动将一个方法添加到控件类中。 向导的默认值`OnDraw`绘制一个带有 "ATL 3.0" 标签的矩形。

请参阅 Windows SDK 中的[IViewObject：:D raw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) 。

##  <a name="freeze"></a>IViewObjectExImpl：：冻结

冻结控件的绘制表示形式，以便在之前`Unfreeze`不会发生更改。 ATL 实现返回 E_NOTIMPL。

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IViewObject：：冻结](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze)。

##  <a name="getadvise"></a>IViewObjectExImpl::GetAdvise

检索控件上的现有通知接收器连接（如果有）。

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>备注

通知接收器存储在 control 类数据成员[CComControlBase：： m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)中。

请参阅 Windows SDK 中的[IViewObject：： GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) 。

##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

返回控件用于绘制的逻辑调色板。 ATL 实现返回 E_NOTIMPL。

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

请参阅 Windows SDK 中的[IViewObject：： GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) 。

##  <a name="getextent"></a>IViewObjectExImpl::GetExtent

从控件类数据成员[CComControlBase：： m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)按 HIMETRIC 单位（0.01 毫米/单位）检索控件的显示大小。

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IViewObject2：： GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) 。

##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

提供容器的大小调整提示，供对象在用户调整其大小时使用。

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

如果`dwAspect`为 DVASPECT_CONTENT， *pExtentInfo-> dwExtentMode*为 DVEXTENT_CONTENT，则将`psizel` * 设置为控件类的数据成员[CComControlBase：： m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否则，将返回错误 HRESULT。

请参阅 Windows SDK 中的[IViewObjectEx：： GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) 。

##  <a name="getrect"></a>IViewObjectExImpl::GetRect

返回描述所请求的绘图方位的矩形。 ATL 实现返回 E_NOTIMPL。

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IViewObjectEx：： GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) 。

##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

返回有关对象的不透明度和所支持的绘图方位的信息。

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>备注

默认情况下，ATL `pdwStatus`设置为指示该控件支持 VIEWSTATUS_OPAQUE （可能值在[VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus)枚举中）。

请参阅 Windows SDK 中的[IViewObjectEx：： GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) 。

##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint

检查指定的点是否在指定的矩形中，并返回`pHitResult`中的 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 值。

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>备注

该值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`等于[DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)，则该方法返回 S_OK。 否则，此方法将返回 E_FAIL。

请参阅 Windows SDK 中的[IViewObjectEx：： QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) 。

##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

检查控件的显示矩形是否与指定位置矩形中的任何点重叠，并返回`pHitResult`中的 [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) 值。

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>备注

该值可以是 HITRESULT_HIT 或 HITRESULT_OUTSIDE。

如果`dwAspect`等于[DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect)，则该方法返回 S_OK。 否则，此方法将返回 E_FAIL。

请参阅 Windows SDK 中的[IViewObjectEx：： QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) 。

##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise

设置控件和通知接收器之间的连接，以便可以通知接收器控件视图中的更改。

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>备注

指向通知接收器上的[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口的指针存储在 control 类数据成员[CComControlBase：： m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)中。

请参阅 Windows SDK 中的[IViewObject：： SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) 。

##  <a name="unfreeze"></a>IViewObjectExImpl：：解冻

Unfreezes 控件绘制的表示形式。 ATL 实现返回 E_NOTIMPL。

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IViewObject：：解冻](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze)。

##  <a name="closehandle"></a>IWorkerThreadClient：： CloseHandle

实现此方法可关闭与此对象关联的句柄。

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>参数

*hHandle*<br/>
要关闭的句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，否则返回错误 HRESULT。

### <a name="remarks"></a>备注

传递给此方法的句柄以前通过调用[CWorkerThread：： AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)与此对象相关联。

### <a name="example"></a>示例

下面的代码演示的`IWorkerThreadClient::CloseHandle`简单实现。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>IWorkerThreadClient：： Execute

实现此方法以在与此对象关联的句柄变为已终止时执行代码。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>参数

*dwParam*<br/>
User 参数。

*hObject*<br/>
已发出信号的句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK，否则返回错误 HRESULT。

### <a name="remarks"></a>备注

传递给此方法的句柄和 DWORD/指针以前通过调用[CWorkerThread：： AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)与此对象相关联。

### <a name="example"></a>示例

下面的代码演示的`IWorkerThreadClient::Execute`简单实现。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控件接口](/windows/win32/com/activex-controls-interfaces)<br/>
[教程](../../atl/active-template-library-atl-tutorial.md)<br/>
[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)<br/>
[类概述](../../atl/atl-class-overview.md)
