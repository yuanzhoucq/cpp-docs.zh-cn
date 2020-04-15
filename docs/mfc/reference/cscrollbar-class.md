---
title: CScrollBar 类
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: 761d7e9db650c6d95e916c85bd7456d9b1c647c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318524"
---
# <a name="cscrollbar-class"></a>CScrollBar 类

提供 Windows 滚动条控件功能。

## <a name="syntax"></a>语法

```
class CScrollBar : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CScrollBar：CScrollBar](#cscrollbar)|构造 `CScrollBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CScrollBar：创建](#create)|创建 Windows 滚动条并将其附加到`CScrollBar`对象。|
|[CScrollBar：：启用滚动条](#enablescrollbar)|启用或禁用滚动条的一个或两个箭头。|
|[CScrollBar：：获取ScrollBarInfo](#getscrollbarinfo)|使用`SCROLLBARINFO`结构检索有关滚动条的信息。|
|[CScrollBar：：获取滚动信息](#getscrollinfo)|检索有关滚动条的信息。|
|[CScrollBar：获取滚动限制](#getscrolllimit)|检索滚动条的限制|
|[CScrollBar：获取滚动位置](#getscrollpos)|检索滚动框的当前位置。|
|[CScrollBar：：获取滚动范围](#getscrollrange)|检索给定滚动条的当前最小和最大滚动条位置。|
|[CScrollBar：：设置Scrollinfo](#setscrollinfo)|设置有关滚动条的信息。|
|[CScrollBar：：设置滚动位置](#setscrollpos)|设置滚动框的当前位置。|
|[CScrollBar：：设置滚动范围](#setscrollrange)|设置给定滚动条的最小和最大位置值。|
|[CScrollBar：：显示滚动栏](#showscrollbar)|显示或隐藏滚动条。|

## <a name="remarks"></a>备注

通过两个步骤创建滚动条控件。 首先，调用构造`CScrollBar`函数构造`CScrollBar`对象，然后调用[Create](#create)成员函数以创建 Windows 滚动条控件并将其附加到`CScrollBar`对象。

如果在对话框中创建`CScrollBar`对象（通过对话框资源），则当用户关闭对话框时，`CScrollBar`将自动销毁 。

如果在窗口中创建`CScrollBar`对象，则可能需要销毁它。

如果在堆栈上`CScrollBar`创建对象，则会自动销毁该对象。 如果使用**新**函数在`CScrollBar`堆上创建对象，**则必须在用户**终止 Windows 滚动栏时调用删除对象以销毁该对象。

如果在`CScrollBar`对象中分配任何内存，请重写`CScrollBar`析构函数以释放分配。

有关使用`CScrollBar`的相关信息，请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar：创建

创建 Windows 滚动条并将其附加到`CScrollBar`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定滚动条的样式。 将[滚动条样式](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles)的任意组合应用于滚动条。

*矩形*<br/>
指定滚动条的大小和位置。 可以是`RECT`结构或`CRect`对象。

*pparentwnd*<br/>
指定滚动条的父窗口（通常是`CDialog`对象）。 值不得为 NULL。

*nID*<br/>
滚动条的控制 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

分两步`CScrollBar`构造对象。 首先，调用构造函数，该构造函数构造`CScrollBar`对象;然后调用`Create`，它创建并初始化关联的 Windows 滚动条并将其附加到`CScrollBar`对象。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于滚动条：

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_GROUP组控件

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar：CScrollBar

构造 `CScrollBar` 对象。

```
CScrollBar();
```

### <a name="remarks"></a>备注

构造对象后，调用`Create`成员函数创建和初始化 Windows 滚动条。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar：：启用滚动条

启用或禁用滚动条的一个或两个箭头。

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>参数

*nArrowFlags*<br/>
指定滚动箭头是启用还是禁用，以及启用或禁用哪些箭头。 此参数可以是以下值之一：

- ESB_ENABLE_BOTH 启用滚动条的两个箭头。

- ESB_DISABLE_LTUP禁用水平滚动条的左箭头或垂直滚动条的向上箭头。

- ESB_DISABLE_RTDN禁用水平滚动条的右箭头或垂直滚动条的向下箭头。

- ESB_DISABLE_BOTH禁用滚动条的两个箭头。

### <a name="return-value"></a>返回值

如果箭头已启用或禁用（如指定）则为非零;否则 0，表示箭头已处于请求状态或发生错误。

### <a name="example"></a>示例

  请参阅[CScrollBar 的示例：：设置滚动范围](#setscrollrange)。

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar：：获取ScrollBarInfo

检索 `SCROLLBARINFO` 结构维护的有关滚动条的信息。

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>参数

*pScrollInfo*<br/>
指向[SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)结构的指针。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟[SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo)消息的功能，如 Windows SDK 中所述。

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar：：获取滚动信息

检索 `SCROLLINFO` 结构维护的有关滚动条的信息。

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>参数

*lpScrollInfo*<br/>
指向[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)结构的指针。 有关此结构的详细信息，请参阅 Windows SDK。

*nMask*<br/>
指定要检索的滚动条参数。 典型的用法（SIF_ALL）指定SIF_PAGE、SIF_POS、SIF_TRACKPOS和SIF_RANGE的组合。 有关`SCROLLINFO`nMask 值的详细信息，请参阅。

### <a name="return-value"></a>返回值

如果消息检索了任何值，则返回为 TRUE。 否则，它是 FALSE。

### <a name="remarks"></a>备注

`GetScrollInfo`使应用程序能够使用 32 位滚动位置。

[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)结构包含有关滚动条的信息，包括最小和最大滚动位置、页面大小和滚动框（拇指）的位置。 有关更改`SCROLLINFO`结构默认值的详细信息，请参阅 Windows SDK 中的结构主题。

指示滚动条位置的 MFC Windows 消息处理程序[CWnd：：onHScroll]和[CWnd：：onVScroll，](../../mfc/reference/cwnd-class.md#onvscroll)仅提供 16 位位置数据。 `GetScrollInfo`并提供`SetScrollInfo`32 位滚动条位置数据。 因此，应用程序可以在处理任`GetScrollInfo`一或`CWnd::OnHScroll``CWnd::OnVScroll`获取 32 位滚动条位置数据时调用。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar：获取滚动限制

检索滚动条的最大滚动位置。

```
int GetScrollLimit();
```

### <a name="return-value"></a>返回值

指定滚动条的最大位置（如果成功）;否则 0。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar：获取滚动位置

检索滚动框的当前位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>返回值

指定滚动框的当前位置（如果成功）;否则 0。

### <a name="remarks"></a>备注

当前位置是一个相对值，取决于当前滚动范围。 例如，如果滚动范围为 100 到 200，并且滚动框位于条形图的中间，则当前位置为 150。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar：：获取滚动范围

将给定滚动条的当前最小和最大滚动条位置复制到*lpMinPos*和*lpMaxPos*指定的位置。

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>参数

*lpMinPos*<br/>
指向要接收最小位置的整数变量。

*lpMaxPos*<br/>
指向要接收最大位置的整数变量。

### <a name="remarks"></a>备注

滚动条控件的默认范围为空（两个值均为 0）。

### <a name="example"></a>示例

  请参阅[CWnd 的示例：onHScroll](../../mfc/reference/cwnd-class.md#onhscroll)。

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar：：设置Scrollinfo

设置`SCROLLINFO`结构维护有关滚动条的信息。

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*lpScrollInfo*<br/>
指向[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)结构的指针。

*bredraw*<br/>
指定是否应重绘滚动条以反映新信息。 如果*bRedraw*为 TRUE，则重绘滚动条。 如果是 FALSE，则不重绘。 默认情况下，滚动条将重绘。

### <a name="return-value"></a>返回值

如果成功，则返回为 TRUE。 否则，它是 FALSE。

### <a name="remarks"></a>备注

您必须提供`SCROLLINFO`结构参数所需的值，包括标志值。

结构`SCROLLINFO`包含有关滚动条的信息，包括最小和最大滚动位置、页面大小和滚动框（拇指）的位置。 有关更改结构默认值的详细信息，请参阅 Windows SDK 中的[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)结构主题。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar：：设置滚动位置

将滚动框的当前位置设置为*nPos*指定的位置，如果指定，则重绘滚动条以反映新位置。

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定滚动框的新位置。 它必须在滚动范围内。

*bredraw*<br/>
指定是否应重绘滚动条以反映新位置。 如果*bRedraw*为 TRUE，则重绘滚动条。 如果是 FALSE，则不重绘。 默认情况下，滚动条将重绘。

### <a name="return-value"></a>返回值

指定滚动框的上一个位置（如果成功）;否则 0。

### <a name="remarks"></a>备注

每当滚动条通过后续调用另一个函数重新绘制时，将*bredraw*设置为 FALSE，以避免滚动条在短时间间隔内重绘两次。

### <a name="example"></a>示例

  请参阅[CScrollBar 的示例：：设置滚动范围](#setscrollrange)。

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar：：设置滚动范围

设置给定滚动条的最小和最大位置值。

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*nMinPos*<br/>
指定最小滚动位置。

*nMaxPos*<br/>
指定最大滚动位置。

*bredraw*<br/>
指定是否应重绘滚动条以反映更改。 如果 bRedraw 为 TRUE，则重绘滚动条;如果*bredraw*为 TRUE，则重新绘制滚动条。如果 FALSE，则不重绘。 默认情况下重绘它。

### <a name="remarks"></a>备注

将*nMinPos*和*nMaxPos*设置为 0 以隐藏标准滚动条。

在处理滚动条通知消息时，不要调用此功能来隐藏滚动条。

如果`SetScrollRange`调用后立即`SetScrollPos`调用成员函数，请将*bRedraw*设置为`SetScrollPos`0 以防止滚动条重绘两次。

*nMinPos*和*nMaxPos*指定的值之间的差异不得大于 32，767。 滚动条控件的默认范围为空 *（nMinPos*和*nMaxPos*均为 0）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar：：显示滚动栏

显示或隐藏滚动条。

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>参数

*b显示*<br/>
指定滚动条是显示还是隐藏。 如果此参数为 TRUE，将显示滚动条;如果此参数为 TRUE，则显示滚动条。否则，它是隐藏的。

### <a name="remarks"></a>备注

应用程序在处理滚动条通知消息时不应调用此函数来隐藏滚动条。

### <a name="example"></a>示例

  请参阅[CScrollBar 的示例：：创建](#create)。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[C按钮类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
