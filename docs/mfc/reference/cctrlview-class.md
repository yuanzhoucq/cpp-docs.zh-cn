---
title: CCtrlView 类
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: 334f139b81afeb06d57cbd128abe9e413b1fd0e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507151"
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
|[CCtrlView::OnDraw](#ondraw)|由框架调用, 以使用指定的设备上下文进行绘制。|
|[CCtrlView::PreCreateWindow](#precreatewindow)|在创建附加到此 `CCtrlView` 对象的 Windows 窗口之前调用。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|包含视图类的默认样式。|
|[CCtrlView::m_strClass](#m_strclass)|包含视图类的 Windows 类名称。|

## <a name="remarks"></a>备注

类`CCtrlView`及其派生项、 [CEditView](../../mfc/reference/ceditview-class.md)、 [CListView](../../mfc/reference/clistview-class.md)、 [CTreeView](../../mfc/reference/ctreeview-class.md)和[CRichEditView](../../mfc/reference/cricheditview-class.md), 使文档视图体系结构适应 windows 95/98 和 windows NT 版本3.51 支持的新公共控件和更高版本。 有关文档视图体系结构的详细信息, 请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cctrlview"></a>CCtrlView:: CCtrlView

构造 `CCtrlView` 对象。

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>参数

*lpszClass*<br/>
视图类的 Windows 类名称。

*dwStyle*<br/>
视图类的样式。

### <a name="remarks"></a>备注

创建新的框架窗口或拆分窗口时, 框架会调用构造函数。 重写[CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)可以在附加文档后初始化视图。 调用[CWnd:: Create](../../mfc/reference/cwnd-class.md#create)或[CWnd:: CreateEx](../../mfc/reference/cwnd-class.md#createex)创建 Windows 对象。

##  <a name="m_strclass"></a>CCtrlView:: m_strClass

包含视图类的 Windows 类名称。

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>CCtrlView:: m_dwDefaultStyle

包含视图类的默认样式。

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>备注

此样式在创建窗口时应用。

##  <a name="ondraw"></a>  CCtrlView::OnDraw

由框架调用, 以使用指定的设备上下文`CCtrlView`绘制对象的内容。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向发生绘制的设备上下文的指针。

### <a name="remarks"></a>备注

`OnDraw`通常称为屏幕显示, 传递*pDC*指定的屏幕设备上下文。

##  <a name="precreatewindow"></a>CCtrlView::P reCreateWindow

在创建附加到此 `CWnd` 对象的 Windows 窗口之前调用。

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>参数

*cs*<br/>
[CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)结构。

### <a name="return-value"></a>返回值

如果应继续创建窗口, 则为非零值;0表示创建失败。

### <a name="remarks"></a>备注

切勿直接调用此函数。

此函数的默认实现将检查 NULL 窗口类名称并替换为适当的默认值。 重写此成员函数以在`CREATESTRUCT`创建窗口之前修改结构。

派生自`CCtrlView`的每个类都将其自己的功能`PreCreateWindow`添加到其重写。 按照设计, 不会记录`PreCreateWindow`这些派生的。 若要确定适用于每个类和样式之间相互依赖关系的样式, 可以检查应用程序的基类的 MFC 源代码。 如果选择重写`PreCreateWindow`, 则可以通过使用从 MFC 源代码收集的信息来确定应用程序的基类中使用的样式是否提供所需的功能。

有关更改窗口样式的详细信息, 请参阅[更改 MFC 创建的窗口的样式](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>请参阅

[CView 类](../../mfc/reference/cview-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CTreeView 类](../../mfc/reference/ctreeview-class.md)<br/>
[CListView 类](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView 类](../../mfc/reference/cricheditview-class.md)
