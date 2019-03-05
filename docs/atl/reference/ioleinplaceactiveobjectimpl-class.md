---
title: IOleInPlaceActiveObjectImpl Class
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
ms.openlocfilehash: fd0bcb7bb20967128ef3b3cc62722c3b68e728d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285043"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl Class

此类提供方法，可帮助在就地控件与其容器之间的通信。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IOleInPlaceActiveObjectImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|使上下文相关帮助。 ATL 实现返回 E_NOTIMPL。|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|启用无模式对话框。 ATL 实现返回 S_OK。|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|获取窗口句柄。|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|激活或停用容器文件窗口时通知控件。 ATL 实现返回 S_OK。|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|激活或停用容器的顶级框架窗口时通知控件。 ATL 实现返回|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|通知控件需要调整其边框的大小。 ATL 实现返回 S_OK。|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|处理来自容器的菜单快捷键消息。 ATL 实现返回 E_NOTIMPL。|

## <a name="remarks"></a>备注

[IOleInPlaceActiveObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceactiveobject)界面可帮助在就地控件与其容器之间的通信; 例如，通信活动状态的控件和容器，并通知控件其需要重新调整大小本身。 类`IOleInPlaceActiveObjectImpl`提供的默认实现`IOleInPlaceActiveObject`，并支持`IUnknown`信息发送给转储调试中的设备生成。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

使上下文相关帮助。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) Windows SDK 中。

##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless

启用无模式对话框。

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) Windows SDK 中。

##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow

容器调用此函数可获取该控件的窗口句柄。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>备注

某些容器不会使用已无窗口，即使它是当前窗口的控件。 在 ATL 的实现中，如果`CComControl::m_bWasOnceWindowless`数据成员为 TRUE 时，该函数将返回 E_FAIL。 否则为如果\* *phwnd*不为 NULL，`GetWindow`分配*phwnd*到控件类数据成员`m_hWnd`，并返回 S_OK。

请参阅[IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) Windows SDK 中。

##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate

激活或停用容器文件窗口时通知控件。

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) Windows SDK 中。

##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

激活或停用容器的顶级框架窗口时通知控件。

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[ioleinplaceactiveobject:: Onframewindowactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) Windows SDK 中。

##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder

通知控件需要调整其边框的大小。

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>返回值

返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) Windows SDK 中。

##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator

处理来自容器的菜单快捷键消息。

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>返回值

此方法支持下列返回值：

如果消息已成功转换，则为 S_OK。

如果不转换该消息，S_FALSE。

### <a name="remarks"></a>备注

请参阅[:: Translateaccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) Windows SDK 中。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控件接口](/windows/desktop/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
