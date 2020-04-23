---
title: CMFCPreviewCtrlImpl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::CMFCPreviewCtrlImpl
- AFXWIN/CMFCPreviewCtrlImpl::Create
- AFXWIN/CMFCPreviewCtrlImpl::Destroy
- AFXWIN/CMFCPreviewCtrlImpl::Focus
- AFXWIN/CMFCPreviewCtrlImpl::GetDocument
- AFXWIN/CMFCPreviewCtrlImpl::Redraw
- AFXWIN/CMFCPreviewCtrlImpl::SetDocument
- AFXWIN/CMFCPreviewCtrlImpl::SetHost
- AFXWIN/CMFCPreviewCtrlImpl::SetPreviewVisuals
- AFXWIN/CMFCPreviewCtrlImpl::SetRect
- AFXWIN/CMFCPreviewCtrlImpl::DoPaint
- AFXWIN/CMFCPreviewCtrlImpl::m_clrBackColor
- AFXWIN/CMFCPreviewCtrlImpl::m_clrTextColor
- AFXWIN/CMFCPreviewCtrlImpl::m_font
- AFXWIN/CMFCPreviewCtrlImpl::m_pDocument
helpviewer_keywords:
- CMFCPreviewCtrlImpl [MFC], CMFCPreviewCtrlImpl
- CMFCPreviewCtrlImpl [MFC], Create
- CMFCPreviewCtrlImpl [MFC], Destroy
- CMFCPreviewCtrlImpl [MFC], Focus
- CMFCPreviewCtrlImpl [MFC], GetDocument
- CMFCPreviewCtrlImpl [MFC], Redraw
- CMFCPreviewCtrlImpl [MFC], SetDocument
- CMFCPreviewCtrlImpl [MFC], SetHost
- CMFCPreviewCtrlImpl [MFC], SetPreviewVisuals
- CMFCPreviewCtrlImpl [MFC], SetRect
- CMFCPreviewCtrlImpl [MFC], DoPaint
- CMFCPreviewCtrlImpl [MFC], m_clrBackColor
- CMFCPreviewCtrlImpl [MFC], m_clrTextColor
- CMFCPreviewCtrlImpl [MFC], m_font
- CMFCPreviewCtrlImpl [MFC], m_pDocument
ms.assetid: 06257fa0-54c9-478d-9d68-c9698c3f93ed
ms.openlocfilehash: 0c0a594a84b45ce7bf6f2c2fa5d1a547fa10eaa6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751850"
---
# <a name="cmfcpreviewctrlimpl-class"></a>CMFCPreviewCtrlImpl 类

此类实现放置在"丰富预览"的 Shell 提供的主机窗口中的窗口。

## <a name="syntax"></a>语法

```
class CMFCPreviewCtrlImpl : public CWnd;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC预览CtrlImpl：：_CMFC预览CtrlImpl](#dtor)|析构预览控件对象。|
|[CMFC 预览 Ctrlimpl：：CMFC 预览Ctrlimpl](#cmfcpreviewctrlimpl)|构造预览控件对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 预览 Ctrlimpl：：创建](#create)|已重载。 由"丰富预览"处理程序调用以创建 Windows 窗口。|
|[CMFC预览CtrlImpl：:D](#destroy)|当需要销毁此控件时，由富预览处理程序调用。|
|[CMFC预览CtrlImpl：：焦点](#focus)|为此控件设置输入焦点。|
|[CMFC预览Ctrlimpl：：获取文档](#getdocument)|返回连接到此预览控件的文档。|
|[CMFC 预览 Ctrlimpl：：重绘](#redraw)|告诉此控件重绘。|
|[CMFC 预览 Ctrlimpl：：设置文档](#setdocument)|由预览处理程序调用以创建文档实现和预览控件之间的关系。|
|[CMFC 预览 Ctrlimpl：：SetHost](#sethost)|为此控件设置新父级。|
|[CMFC 预览 CtrlImpl：：设置预览视觉对象](#setpreviewvisuals)|当需要设置富预览内容的可视对象时，由"丰富预览"处理程序调用。|
|[CMFC 预览 Ctrlimpl：：SetRect](#setrect)|为此控件设置一个新的边界矩形。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC预览CtrlImpl：:DoPaint](#dopaint)|由框架调用以呈现预览。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CMFC 预览CtrlImpl：：m_clrBackColor](#m_clrbackcolor)|预览窗口的背景颜色。|
|[CMFC 预览CtrlImpl：：m_clrTextColor](#m_clrtextcolor)|预览窗口的文本颜色。|
|[CMFC预览CtrlImpl：：m_font](#m_font)|用于在预览窗口中显示文本的字体。|
|[CMFC 预览CtrlImpl：：m_pDocument](#m_pdocument)|指向在控件中预览其内容的文档的指针。|

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFC预览CtrlImpl](../../mfc/reference/cmfcpreviewctrlimpl-class.md)

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="cmfcpreviewctrlimpl"></a>CMFC 预览 Ctrlimpl：：CMFC 预览Ctrlimpl

构造预览控件对象。

### <a name="syntax"></a>语法

CMFC预览CtrlImpl（）;

## <a name="cmfcpreviewctrlimplcreate"></a><a name="create"></a>CMFC 预览 Ctrlimpl：：创建

已重载。 由"丰富预览"处理程序调用以创建 Windows 窗口。

### <a name="syntax"></a>语法

```
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc
);
virtual BOOL Create(
   HWND hWndParent,
   const RECT* prc,
   CCreateContext* pContext
);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
用于富预览的 Shell 提供的主机窗口的句柄。

*中国*<br/>
指定窗口的初始大小和位置。

*pContext*<br/>
指向创建上下文的指针。

### <a name="return-value"></a>返回值

如果创建成功，则为 TRUE；否则为 FALSE。

## <a name="cmfcpreviewctrlimpldestroy"></a><a name="destroy"></a>CMFC预览CtrlImpl：:D

当需要销毁此控件时，由富预览处理程序调用。

### <a name="syntax"></a>语法

```
virtual void Destroy();
```

## <a name="cmfcpreviewctrlimpldopaint"></a><a name="dopaint"></a>CMFC预览CtrlImpl：:DoPaint

由框架调用以呈现预览。

### <a name="syntax"></a>语法

```
virtual void DoPaint(
   CPaintDC* pDC
);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向用于绘制的设备上下文的指针。

## <a name="cmfcpreviewctrlimplfocus"></a><a name="focus"></a>CMFC预览CtrlImpl：：焦点

为此控件设置输入焦点。

### <a name="syntax"></a>语法

```
virtual void Focus();
```

## <a name="cmfcpreviewctrlimplgetdocument"></a><a name="getdocument"></a>CMFC预览Ctrlimpl：：获取文档

返回连接到此预览控件的文档。

### <a name="syntax"></a>语法

```
ATL::IDocument* GetDocument();
```

### <a name="return-value"></a>返回值

指向文档的指针，其内容在控件中预览。

## <a name="cmfcpreviewctrlimplm_clrbackcolor"></a><a name="m_clrbackcolor"></a>CMFC 预览CtrlImpl：：m_clrBackColor

预览窗口的背景颜色。

### <a name="syntax"></a>语法

```
COLORREF m_clrBackColor;
```

## <a name="cmfcpreviewctrlimplm_clrtextcolor"></a><a name="m_clrtextcolor"></a>CMFC 预览CtrlImpl：：m_clrTextColor

预览窗口的文本颜色。

### <a name="syntax"></a>语法

```
COLORREF m_clrTextColor;
```

## <a name="cmfcpreviewctrlimplm_font--font-used-to-display-text-in-the-preview-window"></a><a name="m_font"></a>CMFC预览CtrlImpl：：m_font字体用于在预览窗口中显示文本。

### <a name="syntax"></a>语法

```
CFont m_font;
```

## <a name="cmfcpreviewctrlimplm_pdocument"></a><a name="m_pdocument"></a>CMFC 预览CtrlImpl：：m_pDocument

指向在控件中预览其内容的文档的指针。

### <a name="syntax"></a>语法

```
ATL::IDocument* m_pDocument;
```

## <a name="cmfcpreviewctrlimplredraw"></a><a name="redraw"></a>CMFC 预览 Ctrlimpl：：重绘

告诉此控件重绘。

### <a name="syntax"></a>语法

```
virtual void Redraw();
```

## <a name="cmfcpreviewctrlimplsetdocument"></a><a name="setdocument"></a>CMFC 预览 Ctrlimpl：：设置文档

由预览处理程序调用以创建文档实现和预览控件之间的关系。

### <a name="syntax"></a>语法

```cpp
void SetDocument(
   IDocument* pDocument
);
```

### <a name="parameters"></a>参数

*pDocument*<br/>
指向文档实现的指针。

## <a name="cmfcpreviewctrlimplsethost"></a><a name="sethost"></a>CMFC 预览 Ctrlimpl：：SetHost

为此控件设置新父级。

### <a name="syntax"></a>语法

```
virtual void SetHost(
   HWND hWndParent
);
```

### <a name="parameters"></a>参数

*hWnd 父母*<br/>
新父窗口的句柄。

## <a name="cmfcpreviewctrlimplsetpreviewvisuals"></a><a name="setpreviewvisuals"></a>CMFC 预览 CtrlImpl：：设置预览视觉对象

当需要设置富预览内容的可视对象时，由"丰富预览"处理程序调用。

### <a name="syntax"></a>语法

```
virtual void SetPreviewVisuals(
   COLORREF clrBack,
   COLORREF clrText,
   const LOGFONTW *plf
);
```

### <a name="parameters"></a>参数

*clrBack*<br/>
预览窗口的背景颜色。

*clrText*<br/>
预览窗口的文本颜色。

*plf*<br/>
用于在预览窗口中显示文本的字体。

## <a name="cmfcpreviewctrlimplsetrect"></a><a name="setrect"></a>CMFC 预览 Ctrlimpl：：SetRect

为此控件设置一个新的边界矩形。

### <a name="syntax"></a>语法

```
virtual void SetRect(
   const RECT* prc,
   BOOL bRedraw
);
```

### <a name="parameters"></a>参数

*中国*<br/>
指定预览控件的新大小和位置。

*bredraw*<br/>
指定是否应重绘控件。

### <a name="remarks"></a>备注

通常，在调整主机控件大小时，将设置一个新的边界矩形。

## <a name="cmfcpreviewctrlimplcmfcpreviewctrlimpl"></a><a name="dtor"></a>CMFC预览CtrlImpl：：_CMFC预览CtrlImpl

析构预览控件对象。

### <a name="syntax"></a>语法

```
virtual ~CMFCPreviewCtrlImpl();
```
