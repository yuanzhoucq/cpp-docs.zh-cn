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
ms.openlocfilehash: 1ab25ad26357abe9091d273637f3ae9f77457342
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230475"
---
# <a name="cscrollbar-class"></a>CScrollBar 类

提供 Windows 滚动条控件功能。

## <a name="syntax"></a>语法

```
class CScrollBar : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|构造 `CScrollBar` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CScrollBar：： Create](#create)|创建 Windows 滚动条并将其附加到 `CScrollBar` 对象。|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|启用或禁用滚动条的一个或两个箭头。|
|[CScrollBar：： GetScrollBarInfo](#getscrollbarinfo)|使用结构检索有关滚动条的信息 `SCROLLBARINFO` 。|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|检索有关滚动条的信息。|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|检索滚动条的限制|
|[CScrollBar::GetScrollPos](#getscrollpos)|检索滚动框的当前位置。|
|[CScrollBar::GetScrollRange](#getscrollrange)|检索给定滚动条的当前最小和最大滚动条位置。|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|设置有关滚动条的信息。|
|[CScrollBar::SetScrollPos](#setscrollpos)|设置滚动框的当前位置。|
|[CScrollBar::SetScrollRange](#setscrollrange)|设置给定滚动条的最小和最大位置值。|
|[CScrollBar：： ShowScrollBar](#showscrollbar)|显示或隐藏滚动条。|

## <a name="remarks"></a>备注

您可以通过两个步骤创建一个滚动条控件。 首先，调用构造函数 `CScrollBar` 来构造 `CScrollBar` 对象，然后调用[create](#create)成员函数以创建 Windows 滚动条控件，并将其附加到 `CScrollBar` 对象。

如果在 `CScrollBar` 对话框中创建对象（通过对话资源），则 `CScrollBar` 当用户关闭对话框时，将自动销毁。

如果在 `CScrollBar` 窗口中创建对象，则可能还需要销毁它。

如果在 `CScrollBar` 堆栈上创建对象，则该对象会自动销毁。 如果 `CScrollBar` 使用函数在堆上创建对象 **`new`** ，则必须对对象调用以在 **`delete`** 用户终止 Windows 滚动条时销毁该对象。

如果在对象中分配任何内存 `CScrollBar` ，请重写 `CScrollBar` 析构函数以释放分配。

有关使用的相关信息 `CScrollBar` ，请参阅[控件](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar：： Create

创建 Windows 滚动条并将其附加到 `CScrollBar` 对象。

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

*rect*<br/>
指定滚动条的大小和位置。 可以是 `RECT` 结构或 `CRect` 对象。

*pParentWnd*<br/>
指定滚动条的父窗口，通常为 `CDialog` 对象。 值不得为 NULL。

*nID*<br/>
滚动条的控件 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以通过 `CScrollBar` 两个步骤构造对象。 首先，调用构造对象的构造函数， `CScrollBar` 然后调用 `Create` ，它创建并初始化关联的 Windows 滚动条，并将其附加到 `CScrollBar` 对象。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于滚动条：

- 始终 WS_CHILD

- WS_VISIBLE 通常

- 很少 WS_DISABLED

- WS_GROUP 分组控件

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar

构造 `CScrollBar` 对象。

```
CScrollBar();
```

### <a name="remarks"></a>备注

构造对象后，调用 `Create` 成员函数以创建并初始化 Windows 滚动条。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

启用或禁用滚动条的一个或两个箭头。

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>参数

*nArrowFlags*<br/>
指定是启用还是禁用滚动箭头以及启用或禁用的箭头。 此参数可以是下列值之一：

- ESB_ENABLE_BOTH 启用滚动条的两个箭头。

- ESB_DISABLE_LTUP 禁用水平滚动条的左箭头或垂直滚动条的向上箭头。

- ESB_DISABLE_RTDN 禁用水平滚动条的向右箭头或垂直滚动条的向下箭头。

- ESB_DISABLE_BOTH 禁用滚动条的两个箭头。

### <a name="return-value"></a>返回值

如果按指定启用或禁用箭头，则为非零值;否则为0，指示箭头已经处于请求状态或发生错误。

### <a name="example"></a>示例

  请参阅[CScrollBar：： SetScrollRange](#setscrollrange)的示例。

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar：： GetScrollBarInfo

检索 `SCROLLBARINFO` 结构维护的有关滚动条的信息。

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>参数

*pScrollInfo*<br/>
指向[SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此成员函数模拟[SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo)消息的功能，如 Windows SDK 中所述。

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

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
指定要检索的滚动条参数。 典型用法 SIF_ALL，指定 SIF_PAGE、SIF_POS、SIF_TRACKPOS 和 SIF_RANGE 的组合。 `SCROLLINFO`有关 nMask 值的详细信息，请参阅。

### <a name="return-value"></a>返回值

如果消息检索到了任何值，则返回值为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

`GetScrollInfo`使应用程序能够使用32位滚动位置。

[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)结构包含滚动条的相关信息，包括最小和最大滚动位置、页面大小和滚动框（滚动块）的位置。 有关 `SCROLLINFO` 更改结构默认值的详细信息，请参阅 Windows SDK 中的结构主题。

指示滚动条位置的 MFC Windows 消息处理程序 [CWnd：： OnHScroll 和[CWnd：： OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll)仅提供16位的位置数据。 `GetScrollInfo`和 `SetScrollInfo` 提供32位的滚动条位置数据。 因此，应用程序可以 `GetScrollInfo` 在处理或时 `CWnd::OnHScroll` 调用 `CWnd::OnVScroll` 以获取32位滚动条位置数据。

### <a name="example"></a>示例

  请参阅[CWnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的示例。

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

检索滚动条的最大滚动位置。

```
int GetScrollLimit();
```

### <a name="return-value"></a>返回值

指定滚动条成功的最大位置;否则为0。

### <a name="example"></a>示例

  请参阅[CWnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的示例。

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

检索滚动框的当前位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>返回值

如果成功，则指定滚动框的当前位置;否则为0。

### <a name="remarks"></a>备注

当前位置是依赖于当前滚动范围的相对值。 例如，如果滚动范围为100到200，滚动框处于条形的中间，则当前位置为150。

### <a name="example"></a>示例

  请参阅[CWnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的示例。

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

将给定滚动条的当前最小和最大滚动条位置复制到*lpMinPos*和*lpMaxPos*指定的位置。

```cpp
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

滚动条控件的默认范围为空（这两个值均为0）。

### <a name="example"></a>示例

  请参阅[CWnd：： OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)的示例。

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

设置 `SCROLLINFO` 结构维护的有关滚动条的信息。

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*lpScrollInfo*<br/>
指向[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)结构的指针。

*bRedraw*<br/>
指定是否应重绘滚动条以反映新的信息。 如果*bRedraw*为 TRUE，则将重绘滚动条。 如果该值为 FALSE，则不会重新绘制。 默认情况下，将重新绘制滚动条。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

必须提供结构参数所需的值 `SCROLLINFO` ，包括标志值。

该 `SCROLLINFO` 结构包含滚动条的相关信息，包括最小和最大滚动位置、页面大小和滚动框（滚动块）的位置。 有关更改结构默认值的详细信息，请参阅 Windows SDK 中的[SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo)结构主题。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

将滚动框的当前位置设置为*nPos*指定的位置，如果指定，则重绘滚动条以反映新位置。

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定滚动框的新位置。 它必须在滚动范围内。

*bRedraw*<br/>
指定是否应重绘滚动条以反映新位置。 如果*bRedraw*为 TRUE，则将重绘滚动条。 如果该值为 FALSE，则不会重新绘制。 默认情况下，将重新绘制滚动条。

### <a name="return-value"></a>返回值

如果成功，则指定滚动框的上一个位置。否则为0。

### <a name="remarks"></a>备注

每当对另一个函数的后续调用重绘滚动条时，将*bRedraw*设置为 FALSE，以避免滚动条在短时间间隔内重绘两次。

### <a name="example"></a>示例

  请参阅[CScrollBar：： SetScrollRange](#setscrollrange)的示例。

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

设置给定滚动条的最小和最大位置值。

```cpp
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

*bRedraw*<br/>
指定是否应重绘滚动条以反映更改。 如果*bRedraw*为 TRUE，则将重绘滚动条;如果为 FALSE，则不重新绘制。 默认情况下，将重绘此值。

### <a name="remarks"></a>备注

将*nMinPos*和*nMaxPos*设置为0，以隐藏标准滚动条。

不调用此函数可在处理滚动条通知消息时隐藏滚动条。

如果对 `SetScrollRange` 成员函数的调用立即调用 `SetScrollPos` ，请将*bRedraw*中的设置 `SetScrollPos` 为0，以防滚动条被两次重绘。

*NMinPos*和*nMaxPos*指定的值之间的差异不得大于32767。 滚动条控件的默认范围为空（ *nMinPos*和*nMaxPos*均为0）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar：： ShowScrollBar

显示或隐藏滚动条。

```cpp
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>参数

*bShow*<br/>
指定滚动条是显示还是隐藏。 如果此参数为 TRUE，则显示滚动条;否则为隐藏状态。

### <a name="remarks"></a>备注

在处理滚动条通知消息时，应用程序不应调用此函数隐藏滚动条。

### <a name="example"></a>示例

  请参阅[CScrollBar：： Create](#create)的示例。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CButton 类](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 类](../../mfc/reference/cedit-class.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[CStatic 类](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
