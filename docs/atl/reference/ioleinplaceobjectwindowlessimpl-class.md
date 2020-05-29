---
title: IOleInPlaceObjectWindowlessImpl 类
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: b0438692161f38445eb7cbed54edcc8a0ba8c0d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326581"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 类

此类实现`IUnknown`并提供了使无窗口控件能够接收窗口消息和参与拖放操作的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IOleInPlaceObjectWindowlessImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IOleInPlace 无窗口：：上下文敏感帮助](#contextsensitivehelp)|启用上下文相关的帮助。 ATL 实现返回E_NOTIMPL。|
|[IOleInPlace 无窗口：：获取删除目标](#getdroptarget)|为支持拖`IDropTarget`放的就地活动、无窗口对象提供接口。 ATL 实现返回E_NOTIMPL。|
|[IOleInPlace 无窗口：：获取窗口](#getwindow)|获取窗口句柄。|
|[IOleinplace 无窗口：：原位停用](#inplacedeactivate)|停用活动就地控件。|
|[IOleInPlace 无窗口：：在窗口消息](#onwindowmessage)|将消息从容器调度到处于活动位置的无窗口控件。|
|[IOleInPlace 无窗口：：重新激活和Undo](#reactivateandundo)|重新激活以前停用的控件。 ATL 实现返回E_NOTIMPL。|
|[IOleInPlace 无窗口：：设置对象重新对象](#setobjectrects)|指示就地控件的哪一部分可见。|
|[IOleInPlace 无窗口：：UIdede](#uideactivate)|停用并删除支持就地激活的用户界面。|

## <a name="remarks"></a>备注

[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)接口管理就地控件的重新激活和停用，并确定该控件应可见的数量。 [IOleInPlace 无窗口](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)接口使无窗口控件能够接收窗口消息并参与拖放操作。 类`IOleInPlaceObjectWindowlessImpl`通过在调试生成中向`IOleInPlaceObject`转储`IOleInPlaceObjectWindowless`设备发送`IUnknown`信息来提供 和 和 实现的默认实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlace 无窗口：：上下文敏感帮助

返回 E_NOTIMPL。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>备注

请参阅[IOleWindow：Windows](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) SDK 中的上下文敏感帮助。

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlace 无窗口：：获取删除目标

返回 E_NOTIMPL。

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>备注

请参阅[IOleInPlace 无窗口：：在](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget)Windows SDK 中获取DropTarget。

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlace 无窗口：：获取窗口

容器调用此函数以获取控件的窗口句柄。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>备注

某些容器不适用于无窗口控件，即使它当前是窗口的。 在 ATL 的实现中，如果控制类的数据成员`m_bWasOnceWindowless`为 TRUE，则函数返回E_FAIL。 否则，如果*phwnd*不是`GetWindow`NULL，则将\**phwnd*设置到控件`m_hWnd`类的数据成员并返回S_OK。

请参阅[IOleWindow：在](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow)Windows SDK 中获取窗口。

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleinplace 无窗口：：原位停用

容器调用以停用就地活动控件。

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>备注

此方法执行完全或部分停用，具体取决于控件的状态。 如有必要，将停用控件的用户界面，并销毁控件的窗口（如果有）。 将通知容器控件不再处于活动状态。 容器`IOleInPlaceUIWindow`用于协商菜单和边框空间的接口被释放。

请参阅[IOleInPlace 对象：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate)Windows SDK 中原地停用。

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlace 无窗口：：在窗口消息

将消息从容器调度到处于活动位置的无窗口控件。

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>备注

请参阅[IOleInPlace 无窗口：Windows](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) SDK 中的"窗口消息"。

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlace 无窗口：：重新激活和Undo

返回 E_NOTIMPL。

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>备注

请参阅[IOleInPlace 对象：：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo)Windows SDK 中重新激活并撤消。

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlace 无窗口：：设置对象重新对象

容器调用以通知控件其大小和/或位置已更改。

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>备注

更新控件`m_rcPos`的数据成员和控制显示。 仅显示与剪辑区域相交的控件部分。 如果控件的显示以前已剪切，但剪切已被删除，则可以调用此功能以重绘控件的完整视图。

请参阅[IOleInPlace 对象：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects)Windows SDK 中设置对象重新对象。

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlace 无窗口：：UIdede

停用并删除控件支持就地激活的用户界面。

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>备注

将控制类的数据成员`m_bUIActive`设置为 FALSE。 此函数的 ATL 实现始终返回S_OK。

请参阅[IOleInPlace 对象：：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate)Windows SDK 中激活 UI。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
