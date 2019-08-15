---
title: IOleInPlaceActiveObjectImpl 类
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: f52638c8a28652cc958ebb3d774319ab37a3c46d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495762"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl 类

此类提供用于协助就地控件与其容器之间的通信的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IOleInPlaceActiveObjectImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|启用区分上下文的帮助。 ATL 实现返回 E_NOTIMPL。|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|启用无模式对话框。 ATL 实现返回 S_OK。|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|获取窗口句柄。|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|当激活或停用容器的文档窗口时, 通知控件。 ATL 实现返回 S_OK。|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|当容器的顶级框架窗口被激活或停用时, 通知控件。 ATL 实现返回|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|通知控件它需要调整其边框的大小。 ATL 实现返回 S_OK。|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|处理菜单快捷键-容器中的关键消息。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)接口可帮助就地控件与其容器之间的通信;例如, 传达控件和容器的活动状态, 并通知控件它需要调整自身大小。 类`IOleInPlaceActiveObjectImpl`提供的默认`IOleInPlaceActiveObject`实现, 并通过`IUnknown`在调试版本中将信息发送到转储设备来支持。

**相关文章**[Atl 教程](../../atl/active-template-library-atl-tutorial.md),[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

启用区分上下文的帮助。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) 。

##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless

启用无模式对话框。

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) 。

##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow

容器调用此函数以获取控件的窗口句柄。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>备注

某些容器将不会使用无窗口的控件, 即使它当前处于窗口窗口也是如此。 在 ATL 的实现中, 如果`CComControl::m_bWasOnceWindowless`数据成员为 TRUE, 则函数返回 E_FAIL。 否则, 如果\* *phwnd*不为 NULL, `GetWindow`则会将*phwnd*分配到控件类的`m_hWnd`数据成员, 并返回 S_OK。

请参阅 Windows SDK 中的[IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) 。

##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate

当激活或停用容器的文档窗口时, 通知控件。

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) 。

##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

当容器的顶级框架窗口被激活或停用时, 通知控件。

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceActiveObject:: onframewindowactivate 调用](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)。

##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder

通知控件它需要调整其边框的大小。

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) 。

##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator

处理菜单快捷键-容器中的关键消息。

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>返回值

此方法支持下列返回值：

如果消息已成功转换, 则为 S_OK。

如果未转换消息, 则为 S_FALSE。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) 。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控件接口](/windows/win32/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
