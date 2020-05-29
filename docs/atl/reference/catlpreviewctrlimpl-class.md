---
title: CAtlPreviewCtrlImpl 类
ms.date: 11/04/2016
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
ms.openlocfilehash: fd94d0d6fe43d80b45def3f747c7b7d558de31d4
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167872"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl 类

此类是窗口的 ATL 实现，它放置在 Shell 提供的宿主窗口上以用于丰富的预览。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： ~ CAtlPreviewCtrlImpl](#dtor)|Destructs 预览控件对象。|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|构造预览控件对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： Create](#create)|由丰富的预览处理程序调用以创建 Windows 窗口。|
|[CAtlPreviewCtrlImpl：:D estroy](#destroy)|当需要销毁此控件时，由丰富的预览处理程序调用。|
|[CAtlPreviewCtrlImpl：： Focus](#focus)|为此控件设置输入焦点。|
|[CAtlPreviewCtrlImpl：： OnPaint](#onpaint)|处理 WM_PAINT 消息。|
|[CAtlPreviewCtrlImpl：：重绘](#redraw)|通知此控件重绘。|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|为此控件设置新父代。|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|当需要设置丰富预览内容的视觉对象时，由丰富的预览处理程序调用。|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|为此控件设置新的边框。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：:D oPaint](#dopaint)|由框架调用以呈现预览。|

### <a name="protected-constants"></a>受保护常量

|名称|说明|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： m_plf](#m_plf)|用于在预览窗口中显示文本的字体。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CAtlPreviewCtrlImpl：： m_clrBack](#m_clrback)|预览窗口的背景色。|
|[CAtlPreviewCtrlImpl：： m_clrText](#m_clrtext)|预览窗口的文本颜色。|

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL：： CWindowImpl\<CAtlPreviewCtrlImpl>](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>要求

**标头：** atlpreviewctrlimpl

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="catlpreviewctrlimpl"></a>CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

构造预览控件对象。

```cpp
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplcatlpreviewctrlimpl"></a><a name="dtor"></a>CAtlPreviewCtrlImpl：： ~ CAtlPreviewCtrlImpl

Destructs 预览控件对象。

```cpp
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplcreate"></a><a name="create"></a>CAtlPreviewCtrlImpl：： Create

由丰富的预览处理程序调用以创建 Windows 窗口。

```cpp
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
Shell 为丰富预览提供的宿主窗口的句柄。

*中国*<br/>
指定窗口的初始大小和位置。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimpldestroy"></a><a name="destroy"></a>CAtlPreviewCtrlImpl：:D estroy

当需要销毁此控件时，由丰富的预览处理程序调用。

```cpp
virtual void Destroy();
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimpldopaint"></a><a name="dopaint"></a>CAtlPreviewCtrlImpl：:D oPaint

由框架调用以呈现预览。

```cpp
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>参数

*hdc*<br/>
用于绘制的设备上下文的句柄。

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplfocus"></a><a name="focus"></a>CAtlPreviewCtrlImpl：： Focus

为此控件设置输入焦点。

```cpp
virtual void Focus();
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplm_clrback"></a><a name="m_clrback"></a>CAtlPreviewCtrlImpl：： m_clrBack

预览窗口的背景色。

```cpp
COLORREF m_clrBack;
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplm_clrtext"></a><a name="m_clrtext"></a>CAtlPreviewCtrlImpl：： m_clrText

预览窗口的文本颜色。

```cpp
COLORREF m_clrText;
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplm_plf"></a><a name="m_plf"></a>CAtlPreviewCtrlImpl：： m_plf

用于在预览窗口中显示文本的字体。

```cpp
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplonpaint"></a><a name="onpaint"></a>CAtlPreviewCtrlImpl：： OnPaint

处理 WM_PAINT 消息。

```cpp
LRESULT OnPaint(
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>参数

*nMsg*<br/>
设置为 WM_PAINT。

*wParam*<br/>
未使用此参数。

*lParam*<br/>
未使用此参数。

*bHandled*<br/>
此函数返回时，它将包含 TRUE。

### <a name="return-value"></a>返回值

始终返回 0。

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplredraw"></a><a name="redraw"></a>CAtlPreviewCtrlImpl：：重绘

通知此控件重绘。

```cpp
virtual void Redraw();
```

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplsethost"></a><a name="sethost"></a>CAtlPreviewCtrlImpl::SetHost

为此控件设置新父代。

```cpp
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
新的父窗口的句柄。

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CAtlPreviewCtrlImpl::SetPreviewVisuals

当需要设置丰富预览内容的视觉对象时，由丰富的预览处理程序调用。

```cpp
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```

### <a name="parameters"></a>参数

*clrBack*<br/>
预览窗口的背景色。

*clrText*<br/>
预览窗口的文本颜色。

*plf*<br/>
用于在预览窗口中显示文本的字体。

### <a name="remarks"></a>备注

## <a name="catlpreviewctrlimplsetrect"></a><a name="setrect"></a>CAtlPreviewCtrlImpl::SetRect

为此控件设置新的边框。

```cpp
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>参数

*中国*<br/>
指定预览控件的新大小和位置。

*bRedraw*<br/>
指定是否应重绘控件。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
