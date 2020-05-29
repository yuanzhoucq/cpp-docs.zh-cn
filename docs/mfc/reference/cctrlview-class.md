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
ms.openlocfilehash: f77f1c265920bd160da790647ef754c55e6dbda3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369359"
---
# <a name="cctrlview-class"></a>CCtrlView 类

使文档视图体系结构适应 Windows 98 和 Windows NT 版本 3.51 及更高版本所支持的公共控件。

## <a name="syntax"></a>语法

```
class CCtrlView : public CView
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CtrlView：CtrlView](#cctrlview)|构造 `CCtrlView` 对象。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CtrlView：在画上](#ondraw)|由框架调用，以便使用指定的设备上下文进行绘制。|
|[CtrlView：:P重新创建窗口](#precreatewindow)|在创建附加到此 `CCtrlView` 对象的 Windows 窗口之前调用。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CtrlView：m_dwDefaultStyle](#m_dwdefaultstyle)|包含视图类的默认样式。|
|[CtrlView：m_strClass](#m_strclass)|包含视图类的 Windows 类名称。|

## <a name="remarks"></a>备注

该类`CCtrlView`及其衍生工具 CEditView、CListView、CTreeView 和[CRichEditView](../../mfc/reference/cricheditview-class.md)使文档视图体系结构适应 Windows 95/98 和 Windows NT 版本 3.51 及更高版本支持的新通用控件。 [CEditView](../../mfc/reference/ceditview-class.md) [CListView](../../mfc/reference/clistview-class.md) [CTreeView](../../mfc/reference/ctreeview-class.md) 有关文档视图体系结构的详细信息，请参阅[文档/视图体系结构](../../mfc/document-view-architecture.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cctrlviewcctrlview"></a><a name="cctrlview"></a>CtrlView：CtrlView

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

创建新帧窗口或拆分窗口时，框架将调用构造函数。 覆盖[CView：：在附加](../../mfc/reference/cview-class.md#oninitialupdate)文档后初始化视图的"初始更新"。 调用[CWnd：：创建](../../mfc/reference/cwnd-class.md#create)或[CWnd：创建Ex](../../mfc/reference/cwnd-class.md#createex)以创建 Windows 对象。

## <a name="cctrlviewm_strclass"></a><a name="m_strclass"></a>CtrlView：m_strClass

包含视图类的 Windows 类名称。

```
CString m_strClass;
```

## <a name="cctrlviewm_dwdefaultstyle"></a><a name="m_dwdefaultstyle"></a>CtrlView：m_dwDefaultStyle

包含视图类的默认样式。

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>备注

创建窗口时应用此样式。

## <a name="cctrlviewondraw"></a><a name="ondraw"></a>CtrlView：在画上

由框架调用，以便使用指定的设备上下文绘制`CCtrlView`对象的内容。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向发生绘图的设备上下文的指针。

### <a name="remarks"></a>备注

`OnDraw`通常要求屏幕显示，传递*pDC*指定的屏幕设备上下文。

## <a name="cctrlviewprecreatewindow"></a><a name="precreatewindow"></a>CtrlView：:P重新创建窗口

在创建附加到此 `CWnd` 对象的 Windows 窗口之前调用。

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>参数

*cs*<br/>
[一个创造结构](/windows/win32/api/winuser/ns-winuser-createstructw)。

### <a name="return-value"></a>返回值

如果窗口创建应继续，则非零;0 表示创建失败。

### <a name="remarks"></a>备注

切勿直接调用此函数。

此函数的默认实现检查 NULL 窗口类名称，并替换适当的默认值。 重写此成员函数，在`CREATESTRUCT`创建窗口之前修改结构。

派生自 的每个`CCtrlView`类都会将自己的功能添加到其对`PreCreateWindow`的重写中。 根据设计，这些派生`PreCreateWindow`没有记录。 要确定适合每个类的样式和样式之间的相互依赖性，可以检查应用程序的基类的 MFC 源代码。 如果选择重写`PreCreateWindow`，则可以确定应用程序基类中使用的样式是否通过使用从 MFC 源代码收集的信息提供所需的功能。

有关更改窗口样式的详细信息，请参阅[更改 MFC 创建的窗口样式](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)。

## <a name="see-also"></a>另请参阅

[CView 类](../../mfc/reference/cview-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CTreeView 类](../../mfc/reference/ctreeview-class.md)<br/>
[CListView 类](../../mfc/reference/clistview-class.md)<br/>
[克里希编辑视图类](../../mfc/reference/cricheditview-class.md)
