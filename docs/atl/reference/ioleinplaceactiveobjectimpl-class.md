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
ms.openlocfilehash: b39ba2845a5483444dac53d1616654e902969c77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326589"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl 类

此类提供了协助就地控件与其容器之间通信的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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

|名称|说明|
|----------|-----------------|
|[IOleInPlace 主动对象impl：：上下文敏感帮助](#contextsensitivehelp)|启用上下文相关的帮助。 ATL 实现返回E_NOTIMPL。|
|[IOleInPlace 主动对象impl：：启用无模式](#enablemodeless)|启用无模式对话框。 ATL 实现返回S_OK。|
|[IOleinPlace 主动对象impl：：获取窗口](#getwindow)|获取窗口句柄。|
|[IOleinplace 主动对象impl：：在DocWindow激活](#ondocwindowactivate)|激活或停用容器的文档窗口时通知控件。 ATL 实现返回S_OK。|
|[IOleinPlace 主动对象impl：：在框架窗口激活](#onframewindowactivate)|激活或停用容器的顶层框架窗口时通知控件。 ATL 实现返回|
|[IOleInPlace 主动对象impl：：调整边框](#resizeborder)|通知控件需要调整其边框的大小。 ATL 实现返回S_OK。|
|[IOleInPlace主动对象impl：：翻译加速器](#translateaccelerator)|处理来自容器的菜单快捷键消息。 ATL 实现返回E_NOTIMPL。|

## <a name="remarks"></a>备注

[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)接口可帮助就地控件与其容器之间的通信;例如，通信控件和容器的活动状态，并通知控件需要调整自身大小。 类`IOleInPlaceActiveObjectImpl`通过在调试生成中向`IOleInPlaceActiveObject`转储设备`IUnknown`发送信息，提供 和 的默认实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlace 主动对象impl：：上下文敏感帮助

启用上下文相关的帮助。

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>返回值

返回 E_NOTIMPL。

### <a name="remarks"></a>备注

请参阅[IOleWindow：Windows](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) SDK 中的上下文敏感帮助。

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlace 主动对象impl：：启用无模式

启用无模式对话框。

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleInPlace 活动对象：：](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)在 Windows SDK 中启用无模式。

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>IOleinPlace 主动对象impl：：获取窗口

容器调用此函数以获取控件的窗口句柄。

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>备注

某些容器不适用于无窗口控件，即使它当前是窗口的。 在 ATL 的实现中`CComControl::m_bWasOnceWindowless`，如果数据成员为 TRUE，则函数返回E_FAIL。 否则，如果\**phwnd*不是`GetWindow`NULL，则将*phwnd*分配给控件类的数据`m_hWnd`成员并返回S_OK。

请参阅[IOleWindow：在](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow)Windows SDK 中获取窗口。

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>IOleinplace 主动对象impl：：在DocWindow激活

激活或停用容器的文档窗口时通知控件。

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleInPlace 活动对象：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)Windows SDK 中激活 OnDocWindow。

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>IOleinPlace 主动对象impl：：在框架窗口激活

激活或停用容器的顶层框架窗口时通知控件。

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleInPlace 活动对象：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)Windows SDK 中激活 FrameWindow。

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlace 主动对象impl：：调整边框

通知控件需要调整其边框的大小。

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>返回值

返回S_OK。

### <a name="remarks"></a>备注

请参阅[IOleInPlace 活动对象：：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)Windows SDK 中调整边框大小。

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlace主动对象impl：：翻译加速器

处理来自容器的菜单快捷键消息。

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>返回值

此方法支持下列返回值：

S_OK邮件是否已成功翻译。

如果未翻译邮件，S_FALSE。

### <a name="remarks"></a>备注

请参阅[IOleInPlace 活动对象：：在](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)Windows SDK 中翻译加速器。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制接口](/windows/win32/com/activex-controls-interfaces)<br/>
[类概述](../../atl/atl-class-overview.md)
