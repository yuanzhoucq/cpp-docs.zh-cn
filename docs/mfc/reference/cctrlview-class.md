---
title: CCtrlView 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
dev_langs:
- C++
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84261c2f5b2c913d2096d2b8878886125f6c0243
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380122"
---
# <a name="cctrlview-class"></a>CCtrlView 类

使文档视图体系结构适应 Windows 98 和 Windows NT 版本 3.51 及更高版本所支持的公共控件。

## <a name="syntax"></a>语法

```
class CCtrlView : public CView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|构造 `CCtrlView` 对象。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CCtrlView::OnDraw](#ondraw)|由框架调用以绘制使用指定的设备上下文。|
|[CCtrlView::PreCreateWindow](#precreatewindow)|在创建附加到此 `CCtrlView` 对象的 Windows 窗口之前调用。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|包含视图类的默认样式。|
|[CCtrlView::m_strClass](#m_strclass)|包含视图类的 Windows 类名。|

## <a name="remarks"></a>备注

该类`CCtrlView`及其派生类， [CEditView](../../mfc/reference/ceditview-class.md)， [CListView](../../mfc/reference/clistview-class.md)， [CTreeView](../../mfc/reference/ctreeview-class.md)，并[CRichEditView](../../mfc/reference/cricheditview-class.md)，调整文档视图体系结构的新的公共控件支持 Windows 95/98 和 Windows NT 版本 3.51 及更高版本。 文档视图体系结构的详细信息，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cctrlview"></a>  CCtrlView::CCtrlView

构造 `CCtrlView` 对象。

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>参数

*lpszClass*<br/>
视图类的 Windows 类名。

*dwStyle*<br/>
视图类的样式。

### <a name="remarks"></a>备注

创建新的框架窗口或拆分窗口时，框架将调用构造函数。 重写[cview:: Oninitialupdate](../../mfc/reference/cview-class.md#oninitialupdate)初始化视图后附加文档。 调用[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)或[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)创建 Windows 对象。

##  <a name="m_strclass"></a>  CCtrlView::m_strClass

包含视图类的 Windows 类名。

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>  CCtrlView::m_dwDefaultStyle

包含视图类的默认样式。

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>备注

创建一个窗口时，应用此样式。

##  <a name="ondraw"></a>  CCtrlView::OnDraw

由框架调用以绘制的内容`CCtrlView`对象使用指定的设备上下文。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向在其中绘制出现的设备上下文的指针。

### <a name="remarks"></a>备注

`OnDraw` 通常用于屏幕显示，传递指定的屏幕设备上下文调用*pDC*。

##  <a name="precreatewindow"></a>  CCtrlView::PreCreateWindow

在创建附加到此 `CWnd` 对象的 Windows 窗口之前调用。

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>参数

*cs*<br/>
一个[CREATESTRUCT](https://msdn.microsoft.com/library/windows/desktop/ms632603)结构。

### <a name="return-value"></a>返回值

如果应继续窗口创建; 非零值0 以指示创建失败。

### <a name="remarks"></a>备注

永远不会直接调用此函数。

此函数的默认实现检查 NULL 窗口类名称，并将替换为相应的默认值。 重写此成员函数以修改`CREATESTRUCT`结构创建窗口之前。

每个类派生自`CCtrlView`将其自身的功能添加到其重写`PreCreateWindow`。 根据设计，这些派生的`PreCreateWindow`未记录。 若要确定适合于每个类和样式之间的相互依赖项的样式，可以检查应用程序的基类的 MFC 源代码。 如果您选择替代`PreCreateWindow`，可以确定应用程序的基类中所用的样式是否提供通过使用 MFC 源代码从收集的信息所需的功能。

更改窗口样式的详细信息，请参阅[更改 MFC 创建的窗口样式](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>请参阅

[CView 类](../../mfc/reference/cview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CTreeView 类](../../mfc/reference/ctreeview-class.md)<br/>
[CListView 类](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)
