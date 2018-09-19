---
title: CAtlPreviewCtrlImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef1469c40de8aae06460f1874905c53e91a47ca1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079331"
---
# <a name="catlpreviewctrlimpl-class"></a>CAtlPreviewCtrlImpl 类

此类是 ATL 实现位于 shell 提供用于丰富预览的宿主窗口的窗口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl](#dtor)|Destructs 预览控件对象。|
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|构造一个预览控件对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::Create](#create)|由丰富的预览处理程序创建 Windows 窗口调用。|
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|需要销毁此控件时，由丰富的预览处理程序调用。|
|[CAtlPreviewCtrlImpl::Focus](#focus)|设置输入焦点设置到此控件。|
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|处理 WM_PAINT 消息。|
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|指示此控件重绘。|
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|设置此控件的新父级。|
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|由丰富的预览处理程序时调用它需要设置视觉对象的丰富的预览内容。|
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|设置此控件的新边框。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|由框架调用以呈现预览。|

### <a name="protected-constants"></a>受保护的常量

|name|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|用于在预览窗口中显示文本的字体。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|预览窗口的背景色。|
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|预览窗口的文本颜色。|  

## <a name="remarks"></a>备注

## <a name="inheritance-hierarchy"></a>继承层次结构

`TBase`

`ATL::CMessageMap`

`ATL::CWindowImplRoot<TBase>`

`ATL::CWindowImplBaseT<TBase,TWinTraits>`

[ATL::CWindowImpl\<CAtlPreviewCtrlImpl >](../../atl/reference/cwindowimpl-class.md)

`IPreviewCtrl`

`ATL::CAtlPreviewCtrlImpl`

## <a name="requirements"></a>要求

**标头：** atlpreviewctrlimpl.h

##  <a name="catlpreviewctrlimpl"></a>  CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl

构造一个预览控件对象。

```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```

### <a name="remarks"></a>备注

##  <a name="dtor"></a>  CAtlPreviewCtrlImpl:: ~ CAtlPreviewCtrlImpl

Destructs 预览控件对象。

```
virtual ~CAtlPreviewCtrlImpl(void);
```

### <a name="remarks"></a>备注

##  <a name="create"></a>  CAtlPreviewCtrlImpl::Create

由丰富的预览处理程序创建 Windows 窗口调用。

```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
用于丰富预览提供 shell 主机窗口的句柄。

*中华人民共和国*<br/>
指定的初始大小和窗口的位置。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="destroy"></a>  CAtlPreviewCtrlImpl::Destroy

需要销毁此控件时，由丰富的预览处理程序调用。

```
virtual void Destroy();
```

### <a name="remarks"></a>备注

##  <a name="dopaint"></a>  CAtlPreviewCtrlImpl::DoPaint

由框架调用以呈现预览。

```
virtual void DoPaint(HDC hdc);
```

### <a name="parameters"></a>参数

*hdc*<br/>
用于绘制的设备上下文句柄。

### <a name="remarks"></a>备注

##  <a name="focus"></a>  CAtlPreviewCtrlImpl::Focus

设置输入焦点设置到此控件。

```
virtual void Focus();
```

### <a name="remarks"></a>备注

##  <a name="m_clrback"></a>  CAtlPreviewCtrlImpl::m_clrBack

预览窗口的背景色。

```
COLORREF m_clrBack;
```

### <a name="remarks"></a>备注

##  <a name="m_clrtext"></a>  CAtlPreviewCtrlImpl::m_clrText

预览窗口的文本颜色。

```
COLORREF m_clrText;
```

### <a name="remarks"></a>备注

##  <a name="m_plf"></a>  CAtlPreviewCtrlImpl::m_plf

用于在预览窗口中显示文本的字体。

```
const LOGFONTW* m_plf;
```

### <a name="remarks"></a>备注

##  <a name="onpaint"></a>  CAtlPreviewCtrlImpl::OnPaint

处理 WM_PAINT 消息。

```
LRESULT OnPaint(  
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>参数

*nMsg*<br/>
将设置为 WM_PAINT。

*wParam*<br/>
未使用此参数。

*lParam*<br/>
未使用此参数。

*bHandled*<br/>
此函数返回时，它包含 TRUE。

### <a name="return-value"></a>返回值

始终返回 0。

### <a name="remarks"></a>备注

##  <a name="redraw"></a>  CAtlPreviewCtrlImpl::Redraw

指示此控件重绘。

```
virtual void Redraw();
```

### <a name="remarks"></a>备注

##  <a name="sethost"></a>  CAtlPreviewCtrlImpl::SetHost

设置此控件的新父级。

```
virtual void SetHost(HWND hWndParent);
```

### <a name="parameters"></a>参数

*hWndParent*<br/>
新的父窗口的句柄。

### <a name="remarks"></a>备注

##  <a name="setpreviewvisuals"></a>  CAtlPreviewCtrlImpl::SetPreviewVisuals

由丰富的预览处理程序时调用它需要设置视觉对象的丰富的预览内容。

```
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

##  <a name="setrect"></a>  CAtlPreviewCtrlImpl::SetRect

设置此控件的新边框。

```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```

### <a name="parameters"></a>参数

*中华人民共和国*<br/>
指定新的大小和预览控件的位置。

*bRedraw*<br/>
指定是否需要重新绘制控件。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)
