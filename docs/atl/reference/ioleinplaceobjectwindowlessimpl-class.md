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
ms.openlocfilehash: fdd660daae109ac2a656519131dd9869ceaeaf4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495747"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 类

此类实现`IUnknown`并提供使无窗口控件接收窗口消息和参与拖放操作的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IOleInPlaceObjectWindowlessImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|启用区分上下文的帮助。 ATL 实现返回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|提供支持拖放的就地活动的无窗口对象的接口。`IDropTarget` ATL 实现返回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|获取窗口句柄。|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|停用活动的就地控件。|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|将来自容器的消息调度到就地活动的无窗口控件。|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|重新激活以前停用的控件。 ATL 实现返回 E_NOTIMPL。|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|指示就地控件的哪些部分可见。|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|停用并删除支持就地激活的用户界面。|

## <a name="remarks"></a>备注

[IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)接口管理就地控件的重新激活和停用, 并确定控件应可见的程度。 [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)接口允许无窗口控件接收窗口消息, 并参与拖放操作。 类`IOleInPlaceObjectWindowlessImpl`提供`IOleInPlaceObject`和`IUnknown`的默认实现, 并通过在调试版本中将信息发送到转储设备来实现。 `IOleInPlaceObjectWindowless`

**相关文章**[Atl 教程](../../atl/active-template-library-atl-tutorial.md),[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

返回 E_NOTIMPL。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) 。

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

返回 E_NOTIMPL。

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) 。

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

容器调用此函数以获取控件的窗口句柄。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>备注

某些容器将不会使用无窗口的控件, 即使它当前处于窗口窗口也是如此。 在 ATL 的实现中, 如果控件类的数据成员`m_bWasOnceWindowless`为 TRUE, 则函数返回 E_FAIL。 否则, 如果*phwnd*不为 NULL, `GetWindow`则\*将*phwnd*设置为控件类的数据`m_hWnd`成员, 并返回 S_OK。

请参阅 Windows SDK 中的[IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) 。

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

由容器调用以停用就地活动控件。

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>备注

此方法执行完全或部分停用, 具体取决于控件的状态。 如有必要, 将停用该控件的用户界面, 并且销毁该控件的窗口 (如果有)。 将通知容器控件不再处于活动状态。 容器用来协商菜单和边框空间的接口已释放。`IOleInPlaceUIWindow`

请参阅 Windows SDK 中的[IOleInPlaceObject:: InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) 。

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

将来自容器的消息调度到就地活动的无窗口控件。

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) 。

##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

返回 E_NOTIMPL。

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceObject:: ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) 。

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

由容器调用以通知控件其大小和/或位置已更改。

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>备注

更新控件的`m_rcPos`数据成员和控件显示。 只显示与剪辑区域相交的控件部分。 如果以前剪切了控件的显示, 但剪辑已被移除, 则可调用此函数来重绘控件的完整视图。

请参阅 Windows SDK 中的[IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) 。

##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate

停用并删除控件的支持就地激活的用户界面。

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>备注

将控件类的数据成员`m_bUIActive`设置为 FALSE。 此函数的 ATL 实现始终返回 S_OK。

请参阅 Windows SDK 中的[IOleInPlaceObject:: UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) 。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
