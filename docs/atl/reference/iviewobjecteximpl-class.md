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
ms.openlocfilehash: 59c5657dcd892544f7e790b52325cb9ecba0dd56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326346"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 类

`IUnknown`此类实现并提供[IViewObject、IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject)[IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)接口的默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IViewObjectExImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IViewObjectEximpl：:D原始](#draw)|将控件的表示形式绘制到设备上下文中。|
|[IViewObjectEximpl：：冻结](#freeze)|冻结控件的绘制表示形式，使其直到 不会`Unfreeze`更改。 ATL 实现返回E_NOTIMPL。|
|[IViewObjectEximpl：：获取建议](#getadvise)|检索控件上的现有通知接收器连接（如果有）。|
|[IViewObjectEximpl：：获取颜色集](#getcolorset)|返回控件用于绘图的逻辑调色板。 ATL 实现返回E_NOTIMPL。|
|[IViewObjectEximpl：：获取范围](#getextent)|从控制类数据成员[CComControlBase：m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)检索控件的显示大小（以 HIMETRIC 单位（单位 0.01 毫米为单位）。|
|[IViewObjectEximpl：：获取自然范围](#getnaturalextent)|提供容器的大小调整提示，供对象在用户调整大小时使用。|
|[IViewObjectEximpl：：获取 Rect](#getrect)|返回描述请求的绘图方面的矩形。 ATL 实现返回E_NOTIMPL。|
|[IViewObjectEximpl：：获取查看状态](#getviewstatus)|返回有关对象的不一性以及支持哪些绘图方面的信息。|
|[IViewObjectEximpl：：查询HitPoint](#queryhitpoint)|检查指定点是否位于指定的矩形中，并在 中`pHitResult`返回[HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult)值。|
|[IViewObjectEximpl：：查询希特](#queryhitrect)|检查控件的显示矩形是否与指定位置矩形中的任何点重叠，并在 中`pHitResult`返回 HITRESULT 值。|
|[IViewObjectEximpl：：设置建议](#setadvise)|在控件和通知接收器之间设置连接，以便通知接收器有关控件视图中的更改。|
|[IViewObjectEximpl：：解冻](#unfreeze)|解冻控件的绘制表示形式。 ATL 实现返回E_NOTIMPL。|

## <a name="remarks"></a>备注

[IViewObject、IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)和[IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject) [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)接口使控件能够直接显示自身，并创建和管理建议接收器，以通知容器控件显示中的更改。 该`IViewObjectEx`接口支持扩展控制功能，如无闪烁绘图、非矩形和透明控件以及命中测试（例如，必须在控件上考虑鼠标单击的接近程度）。 类`IViewObjectExImpl`通过在调试版本中向转储设备发送信息来`IUnknown`提供这些接口和实现的默认实现。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectEximpl：:D原始

将控件的表示形式绘制到设备上下文中。

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

此方法调用`CComControl::OnDrawAdvanced`控件类`OnDraw`的方法，进而调用控件类的方法。 使用`OnDraw`ATL 控件向导创建控件时，方法将自动添加到控件类中。 向导的默认值`OnDraw`绘制一个带有"ATL 3.0"标签的矩形。

请参阅[IViewObject：:D原始](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)在 Windows SDK 中。

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectEximpl：：冻结

冻结控件的绘制表示形式，使其直到 不会`Unfreeze`更改。 ATL 实现返回E_NOTIMPL。

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>备注

请参阅[IViewObject：冻结](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze)在 Windows SDK 中。

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a>IViewObjectEximpl：：获取建议

检索控件上的现有通知接收器连接（如果有）。

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>备注

通知接收器存储在控制类数据成员[CComControlBase：m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。

请参阅[IViewObject：在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise)Windows SDK 中获取建议。

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>IViewObjectEximpl：：获取颜色集

返回控件用于绘图的逻辑调色板。 ATL 实现返回E_NOTIMPL。

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

请参阅[IViewObject：在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset)Windows SDK 中获取ColorSet。

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectEximpl：：获取范围

从控制类数据成员[CComControlBase：m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)检索控件的显示大小（以 HIMETRIC 单位（单位 0.01 毫米为单位）。

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>备注

请参阅[IViewObject2：：在](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent)Windows SDK 中获取范围。

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>IViewObjectEximpl：：获取自然范围

提供容器的大小调整提示，供对象在用户调整大小时使用。

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

如果`dwAspect`DVASPECT_CONTENT和*pAandinfo->dwAAndMode*是`psizel`DVEXTENT_CONTENT，则将 * 设置到控制类的数据成员[CComControlBase：：m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否则，返回错误 HRESULT。

请参阅[IViewObjectEx：在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent)Windows SDK 中获取自然范围。

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectEximpl：：获取 Rect

返回描述请求的绘图方面的矩形。 ATL 实现返回E_NOTIMPL。

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>备注

请参阅[IViewObjectEx：在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect)Windows SDK 中获取 Rect。

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>IViewObjectEximpl：：获取查看状态

返回有关对象的不一性以及支持哪些绘图方面的信息。

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>备注

默认情况下，ATL 设置`pdwStatus`以指示控件支持VIEWSTATUS_OPAQUE（可能的值位于["视图状态](/windows/win32/api/ocidl/ne-ocidl-viewstatus)枚举"中）。

请参阅[IViewObjectEx：在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus)Windows SDK 中获取查看状态。

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>IViewObjectEximpl：：查询HitPoint

检查指定点是否位于指定的矩形中，并在 中`pHitResult`返回[HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult)值。

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>备注

该值可以是HITRESULT_HIT，也可以是HITRESULT_OUTSIDE。

如果`dwAspect`等于[DVASPECT_CONTENT，](/windows/win32/api/wtypes/ne-wtypes-dvaspect)则该方法将返回S_OK。 否则，该方法将返回E_FAIL。

请参阅[IViewObjectEx：在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint)Windows SDK 中查询 HitPoint。

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectEximpl：：查询希特

检查控件的显示矩形是否与指定位置矩形中的任何点重叠，并在 中`pHitResult`返回[HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult)值。

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>备注

该值可以是HITRESULT_HIT，也可以是HITRESULT_OUTSIDE。

如果`dwAspect`等于[DVASPECT_CONTENT，](/windows/win32/api/wtypes/ne-wtypes-dvaspect)则该方法将返回S_OK。 否则，该方法将返回E_FAIL。

请参阅[IViewObjectEx：在](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect)Windows SDK 中查询Hitrect。

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a>IViewObjectEximpl：：设置建议

在控件和通知接收器之间设置连接，以便通知接收器有关控件视图中的更改。

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>备注

指向建议接收器上的[IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)接口的指针存储在控制类数据成员[CComControlBase：：m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。

请参阅[IViewObject：在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise)Windows SDK 中设置建议。

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectEximpl：：解冻

解冻控件的绘制表示形式。 ATL 实现返回E_NOTIMPL。

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>备注

请参阅[IViewObject：在](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze)Windows SDK 中解冻。

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThread客户端：：关闭句柄

实现此方法以关闭与此对象关联的句柄。

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>参数

*hHandle*<br/>
要关闭的句柄。

### <a name="return-value"></a>返回值

返回成功时S_OK，或失败时出现错误 HRESULT。

### <a name="remarks"></a>备注

传递给此方法的句柄以前通过调用[CWorkerThread：：addHandle](../../atl/reference/cworkerthread-class.md#addhandle)与此对象相关联。

### <a name="example"></a>示例

以下代码显示了`IWorkerThreadClient::CloseHandle`的简单实现。

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThread客户端：执行

实现此方法，当与此对象关联的句柄发出信号时执行代码。

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>参数

*德帕拉姆*<br/>
用户参数。

*hObject*<br/>
已发出信号的句柄。

### <a name="return-value"></a>返回值

返回成功时S_OK，或失败时出现错误 HRESULT。

### <a name="remarks"></a>备注

传递给此方法的句柄和 DWORD/指针以前通过调用[CWorkerThread：：addHandle](../../atl/reference/cworkerthread-class.md#addhandle)与此对象相关联。

### <a name="example"></a>示例

以下代码显示了`IWorkerThreadClient::Execute`的简单实现。

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制接口](/windows/win32/com/activex-controls-interfaces)<br/>
[教程](../../atl/active-template-library-atl-tutorial.md)<br/>
[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)<br/>
[类概述](../../atl/atl-class-overview.md)
