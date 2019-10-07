---
title: CReBarCtrl 类
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 14befb819a30238abb5780b1bdcc6d74402e8976
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741186"
---
# <a name="crebarctrl-class"></a>CReBarCtrl 类

封装 Rebar 控件的功能，此控件是一个子窗口容器。

## <a name="syntax"></a>语法

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CReBarCtrl：： CReBarCtrl](#crebarctrl)|构造 `CReBarCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|将 rebar 控件置于拖放模式。|
|[CReBarCtrl::Create](#create)|创建 rebar 控件并将其附加到`CReBarCtrl`对象。|
|[CReBarCtrl::CreateEx](#createex)|创建具有指定 Windows 扩展样式的 rebar 控件，并将其附加到`CReBarCtrl`对象。|
|[CReBarCtrl::DeleteBand](#deleteband)|从 rebar 控件中删除带区。|
|[CReBarCtrl::DragMove](#dragmove)|调用后，更新 rebar 控件中的拖动位置`BeginDrag`。|
|[CReBarCtrl::EndDrag](#enddrag)|终止 rebar 控件的拖放操作。|
|[CReBarCtrl::GetBandBorders](#getbandborders)|检索带区的边框。|
|[CReBarCtrl::GetBandCount](#getbandcount)|检索当前在 rebar 控件中的带区的计数。|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|检索 rebar 控件中指定带区的相关信息。|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|检索带区的边距。|
|[CReBarCtrl::GetBarHeight](#getbarheight)|检索 rebar 控件的高度。|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|检索有关 rebar 控件及其使用的图像列表的信息。|
|[CReBarCtrl::GetBkColor](#getbkcolor)|检索 rebar 控件的默认背景色。|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|检索与 rebar 控件关联的[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构。|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|检索 rebar 控件的`IDropTarget`接口指针。|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|获取当前 rebar 控件的扩展样式。|
|[CReBarCtrl::GetImageList](#getimagelist)|检索与 rebar 控件关联的图像列表。|
|[CReBarCtrl::GetPalette](#getpalette)|检索 rebar 控件的当前调色板。|
|[CReBarCtrl::GetRect](#getrect)|检索 rebar 控件中给定带区的边框。|
|[CReBarCtrl::GetRowCount](#getrowcount)|检索 rebar 控件中带区的行数。|
|[CReBarCtrl::GetRowHeight](#getrowheight)|检索 rebar 控件中指定行的高度。|
|[CReBarCtrl::GetTextColor](#gettextcolor)|检索 rebar 控件的默认文本颜色。|
|[CReBarCtrl::GetToolTips](#gettooltips)|检索与 rebar 控件关联的任何工具提示控件的句柄。|
|[CReBarCtrl::HitTest](#hittest)|确定 rebar 带区的哪个部分位于屏幕上的给定点，前提是在该点存在 rebar 带区。|
|[CReBarCtrl::IDToIndex](#idtoindex)|将带区标识符（ID）转换为 rebar 控件中的带区索引。|
|[CReBarCtrl::InsertBand](#insertband)|在 rebar 控件中插入新带区。|
|[CReBarCtrl::MaximizeBand](#maximizeband)|将 rebar 控件中的带区调整到其最大大小。|
|[CReBarCtrl::MinimizeBand](#minimizeband)|将 rebar 控件中的带区大小调整到最小大小。|
|[CReBarCtrl::MoveBand](#moveband)|将带区从一个索引移动到另一个索引。|
|[CReBarCtrl::PushChevron](#pushchevron)|以编程方式推送 v 形。|
|[CReBarCtrl::RestoreBand](#restoreband)|将 rebar 控件中的带区调整为理想大小。|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|设置 rebar 控件中现有带区的特征。|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|设置当前 rebar 控件中指定的带区的宽度。|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|设置 rebar 控件的特征。|
|[CReBarCtrl::SetBkColor](#setbkcolor)|设置 rebar 控件的默认背景色。|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|为 rebar 控件上的按钮设置配色方案。|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|设置当前 rebar 控件的扩展样式。|
|[CReBarCtrl::SetImageList](#setimagelist)|设置 rebar 控件的图像列表。|
|[CReBarCtrl::SetOwner](#setowner)|设置 rebar 控件的所有者窗口。|
|[CReBarCtrl::SetPalette](#setpalette)|设置 rebar 控件的当前调色板。|
|[CReBarCtrl::SetTextColor](#settextcolor)|设置 rebar 控件的默认文本颜色。|
|[CReBarCtrl::SetToolTips](#settooltips)|将工具提示控件与 rebar 控件相关联。|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|设置 rebar 控件的视觉样式。|
|[CReBarCtrl::ShowBand](#showband)|显示或隐藏 rebar 控件中的给定带区。|
|[CReBarCtrl::SizeToRect](#sizetorect)|使 rebar 控件适合指定的矩形。|

## <a name="remarks"></a>备注

Rebar 控件所在的应用程序将 rebar 控件包含的子窗口分配给 rebar 带区。 子窗口通常是另一个常见的控件。

Rebar 控件包含一个或多个带区。 每个带区可包含手柄栏、位图、文本标签和子窗口的组合。 带区只能包含其中一项。

Rebar 控件可以通过指定的背景位图显示子窗口。 所有 rebar 控件带区都可以调整大小，但使用 RBBS_FIXEDSIZE 样式的控件区段除外。 当重新定位 rebar 控件带区或调整其大小时，rebar 控件管理分配到该带区的子窗口的大小和位置。 若要调整控件内带区的大小或更改其顺序，请单击并拖动带区的控制条。

下图显示了具有三个带区的 rebar 控件：

- 波段0包含一个平面透明工具栏控件。

- 带区1同时包含透明标准下拉按钮和透明下拉按钮。

- 波段2包含组合框和四个标准按钮。

   ![Rebar 菜单示例](../../mfc/reference/media/vc4scc1.gif "Rebar 菜单示例")

## <a name="rebar-control"></a>Rebar 控件

Rebar 控件支持：

- 图像列表。

- 消息处理。

- 自定义绘制功能。

- 除了标准窗口样式以外的各种控件样式。 有关这些样式的列表，请参阅 Windows SDK 中的[Rebar 控件样式](/windows/win32/Controls/rebar-control-styles)。

有关详细信息，请参阅[Using CReBarCtrl](../../mfc/using-crebarctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag

实现 Win32 消息[RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)的行为，如 Windows SDK 中所述。

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>参数

*uBand*<br/>
拖放操作将影响的带区的从零开始的索引。

*dwPos*<br/>
一个包含开始鼠标坐标的 DWORD 值。 水平坐标包含在 LOWORD 中，垂直坐标包含在 HIWORD 中。 如果传递（DWORD）-1，则 rebar 控件将使用鼠标在控件的线程最后一次调用`GetMessage`或`PeekMessage`时的位置。

##  <a name="create"></a>CReBarCtrl：： Create

创建 rebar 控件并将其附加到`CReBarCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定应用于控件的 rebar 控件样式的组合。 有关支持的样式的列表，请参阅 Windows SDK 中的[Rebar 控件样式](/windows/win32/Controls/rebar-control-styles)。

*rect*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用，它是 rebar 控件的位置和大小。

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是 rebar 控件的父窗口。 它不能为 NULL。

*nID*<br/>
指定 rebar 控件的控件 ID。

### <a name="return-value"></a>返回值

如果成功创建对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

通过两个步骤创建 rebar 控件：

1. 调用[CReBarCtrl](#crebarctrl)以构造`CReBarCtrl`对象。

1. 调用此成员函数，该函数创建 Windows rebar 控件并将其附加到`CReBarCtrl`对象。

调用`Create`时，将初始化公共控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

##  <a name="createex"></a>CReBarCtrl：： CreateEx

创建一个控件（子窗口）并将`CReBarCtrl`其与对象关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定应用于控件的 rebar 控件样式的组合。 有关支持的样式的列表，请参阅 Windows SDK 中的[Rebar 控件样式](/windows/win32/Controls/rebar-control-styles)。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用，该结构描述要创建的窗口的大小和位置（以*pParentWnd*的工作区坐标表示）。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[Create](#create)来应用扩展的 windows 样式，由 windows 扩展样式指定的**WS_EX_** 。

##  <a name="crebarctrl"></a>CReBarCtrl：： CReBarCtrl

创建一个 `CReBarCtrl` 对象。

```
CReBarCtrl();
```

### <a name="example"></a>示例

  请参阅[CReBarCtrl：： Create](#create)的示例。

##  <a name="deleteband"></a>CReBarCtrl：:D eleteBand

实现 Win32 消息[RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)的行为，如 Windows SDK 中所述。

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要删除的带区的从零开始的索引。

### <a name="return-value"></a>返回值

如果成功删除带区，则为非零;否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

##  <a name="dragmove"></a>  CReBarCtrl::DragMove

实现 Win32 消息[RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)的行为，如 Windows SDK 中所述。

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>参数

*dwPos*<br/>
一个包含新鼠标坐标的 DWORD 值。 水平坐标包含在 LOWORD 中，垂直坐标包含在 HIWORD 中。 如果传递（DWORD）-1，则 rebar 控件将使用鼠标在控件的线程最后一次调用`GetMessage`或`PeekMessage`时的位置。

##  <a name="enddrag"></a>CReBarCtrl：： EndDrag

实现 Win32 消息[RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)的行为，如 Windows SDK 中所述。

```
void EndDrag();
```

##  <a name="getbandborders"></a>CReBarCtrl：： GetBandBorders

实现 Win32 消息[RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)的行为，如 Windows SDK 中所述。

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>参数

*uBand*<br/>
要为其检索边框的带区的从零开始的索引。

*prc*<br/>
指向将接收带区边框的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针。 如果 rebar 控件具有 RBS_BANDBORDERS 样式，则此结构的每个成员将在带区的相应一侧接收构成边框的像素数。 如果 rebar 控件没有 RBS_BANDBORDERS 样式，则只有此结构的左侧成员才能接收有效信息。 有关 rebar 控件样式的说明，请参阅 Windows SDK 中的[Rebar 控件样式](/windows/win32/Controls/rebar-control-styles)。

##  <a name="getbandcount"></a>CReBarCtrl：： GetBandCount

实现 Win32 消息[RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)的行为，如 Windows SDK 中所述。

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>返回值

分配给控件的带区数。

##  <a name="getbandinfo"></a>CReBarCtrl：： GetBandInfo

按照 Windows SDK 中所述，实现 Win32 消息[RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo)的行为。

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>参数

*uBand*<br/>
要为其检索信息的带区的从零开始的索引。

*prbbi*<br/>
指向接收带区信息的[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的指针。 您必须将此`cbSize`结构的成员设置为`sizeof(REBARBANDINFO)` ，并将`fMask`成员设置为在发送此消息之前要检索的项。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="getbandmargins"></a>CReBarCtrl：： GetBandMargins

检索带区的边距。

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>参数

*pMargins*<br/>
指向将接收信息的[边距](/windows/win32/api/uxtheme/ns-uxtheme-margins)结构的指针。

### <a name="remarks"></a>备注

此成员函数模拟[RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins)消息的功能，如 Windows SDK 中所述。

##  <a name="getbarheight"></a>CReBarCtrl：： GetBarHeight

检索 rebar 栏的高度。

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>返回值

表示控件的高度（以像素为单位）的值。

##  <a name="getbarinfo"></a>CReBarCtrl：： GetBarInfo

实现 Win32 消息[RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)的行为，如 Windows SDK 中所述。

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>参数

*prbi*<br/>
指向将接收 rebar 控件信息的[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)结构的指针。 发送此消息前 ，必须将此结构的`sizeof(REBARINFO)` cbSize 成员设置为。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="getbkcolor"></a>CReBarCtrl：： GetBkColor

实现 Win32 消息[RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)的行为，如 Windows SDK 中所述。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

一个 COLORREF 值，该值表示当前的默认背景色。

##  <a name="getcolorscheme"></a>CReBarCtrl：： GetColorScheme

检索 rebar 控件的[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构。

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>参数

*lpcs*<br/>
指向[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构的指针，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

`COLORSCHEME`结构包括按钮突出显示颜色和按钮阴影颜色。

##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget

实现 Win32 消息[RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)的行为，如 Windows SDK 中所述。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>返回值

指向[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口的指针。

##  <a name="getextendedstyle"></a>CReBarCtrl：： GetExtendedStyle

获取当前 rebar 控件的扩展样式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>返回值

标志的按位组合（OR），指示扩展样式。 可能的标志为 RBS_EX_SPLITTER 和 RBS_EX_TRANSPARENT。 有关详细信息，请参阅[CReBarCtrl：： SetExtendedStyle](#setextendedstyle)方法的*dwMask*参数。

### <a name="remarks"></a>备注

此方法发送[RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove)消息，如 Windows SDK 中所述。

##  <a name="getimagelist"></a>CReBarCtrl：： GetImageList

获取与`CImageList` rebar 控件关联的对象。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。 如果没有为控件设置图像列表，则返回 NULL。

### <a name="remarks"></a>备注

此成员函数使用存储在[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)结构中的大小和掩码信息，如 Windows SDK 中所述。

##  <a name="getpalette"></a>CReBarCtrl：： GetPalette

检索 rebar 控件的当前调色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>返回值

指向[CPalette](../../mfc/reference/cpalette-class.md)对象的指针，该对象指定 rebar 控件的当前调色板。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CPalette`对象作为其返回值，而不是 HPALETTE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

##  <a name="getrect"></a>CReBarCtrl：： GetRect

实现 Win32 消息[RB_GETRECT](/windows/win32/Controls/rb-getrect)的行为，如 Windows SDK 中所述。

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>参数

*uBand*<br/>
Rebar 控件中带区的从零开始的索引。

*prc*<br/>
指向将接收 rebar 带区边界的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

##  <a name="getrowcount"></a>CReBarCtrl：： GetRowCount

实现 Win32 消息[RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)的行为，如 Windows SDK 中所述。

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>返回值

一个 UINT 值，表示控件中带区的行数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

##  <a name="getrowheight"></a>CReBarCtrl：： GetRowHeight

实现 Win32 消息[RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)的行为，如 Windows SDK 中所述。

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>参数

*uRow*<br/>
要检索其高度的带区的从零开始的索引。

### <a name="return-value"></a>返回值

表示行高的 UINT 值（以像素为单位）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

##  <a name="gettextcolor"></a>CReBarCtrl：： GetTextColor

实现 Win32 消息[RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)的行为，如 Windows SDK 中所述。

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>返回值

表示当前默认文本颜色的 COLORREF 值。

##  <a name="gettooltips"></a>CReBarCtrl：： GetToolTips

实现 Win32 消息[RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)的行为，如 Windows SDK 中所述。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>返回值

指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针。

### <a name="remarks"></a>备注

请注意，的`GetToolTips` MFC 实现返回指向的`CToolTipCtrl`指针，而不是 HWND。

##  <a name="hittest"></a>CReBarCtrl：： System.windows.media.visualtreehelper.hittest

实现 Win32 消息[RB_HITTEST](/windows/win32/Controls/rb-hittest)的行为，如 Windows SDK 中所述。

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>参数

*prbht*<br/>
指向[RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo)结构的指针。 在发送消息之前， `pt`必须在工作区坐标中将此结构的成员初始化为要测试的点。

### <a name="return-value"></a>返回值

在给定点处带区的从零开始的索引; 如果在该点上没有 rebar 带区，则为-1。

##  <a name="idtoindex"></a>CReBarCtrl：： IDToIndex

实现 Win32 消息[RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)的行为，如 Windows SDK 中所述。

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>参数

*uBandID*<br/>
指定带区的应用程序定义的标识符，在插入带`wID`区时传入[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的成员。

### <a name="return-value"></a>返回值

如果成功，则为从零开始的带索引; 否则为-1。 如果存在重复的带区索引，则返回第一个。

##  <a name="insertband"></a>CReBarCtrl：： InsertBand

实现 Win32 消息[RB_INSERTBAND](/windows/win32/Controls/rb-insertband)的行为，如 Windows SDK 中所述。

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>参数

*uIndex*<br/>
要插入带区的位置的从零开始的索引。 如果将此参数设置为-1，则控件将在最后一个位置添加新的带区。

*prbbi*<br/>
指向[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的指针，该结构定义要插入的带区。 在调用此函数之前，您必须将此`sizeof(REBARBANDINFO)`结构的 cbSize 成员设置为。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

##  <a name="maximizeband"></a>CReBarCtrl：： MaximizeBand

将 rebar 控件中的带区调整到其最大大小。

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要最大化的带区的从零开始的索引。

### <a name="remarks"></a>备注

实现 Win32 消息[RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband)的行为，并将`fIdeal`其设置为0，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

##  <a name="minimizeband"></a>CReBarCtrl：： MinimizeBand

将 rebar 控件中的带区大小调整到最小大小。

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要最小化的带区的从零开始的索引。

### <a name="remarks"></a>备注

实现 Win32 消息[RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

##  <a name="moveband"></a>CReBarCtrl：： MoveBand

实现 Win32 消息[RB_MOVEBAND](/windows/win32/Controls/rb-moveband)的行为，如 Windows SDK 中所述。

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>参数

*uFrom*<br/>
要移动的带区的从零开始的索引。

*U）*<br/>
新带区位置的从零开始的索引。 此参数值不能大于带区减1的值。 若要获取带区数量，请调用[GetBandCount](#getbandcount)。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="pushchevron"></a>CReBarCtrl：:P ushChevron

实现 Win32 消息[RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)的行为，如 Windows SDK 中所述。

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要推送其 v 形的带区的从零开始的索引。

*lAppValue*<br/>
应用程序定义的32位值。 请参阅 Windows SDK 的[RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)中的*lAppValue* 。

##  <a name="restoreband"></a>CReBarCtrl：： RestoreBand

将 rebar 控件中的带区调整为理想大小。

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要最大化的带区的从零开始的索引。

### <a name="remarks"></a>备注

实现 Win32 消息[RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband)的行为，并将`fIdeal`其设置为1，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

##  <a name="setbandinfo"></a>CReBarCtrl：： SetBandInfo

实现 Win32 消息[RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)的行为，如 Windows SDK 中所述。

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要接收新设置的带区的从零开始的索引。

*prbbi*<br/>
指向[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的指针，该结构定义要插入的带区。 发送此消息前`cbSize` ，必须将此结构`sizeof(REBARBANDINFO)`的成员设置为。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

##  <a name="setbandwidth"></a>CReBarCtrl：： SetBandWidth

设置当前 rebar 控件中指定的带区的宽度。

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*uBand*|中Rebar 带区的从零开始的索引。|
|*cxWidth*|中Rebar 带区的新宽度（以像素为单位）。|

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth)消息，如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义用于访问当前`m_rebar`rebar 控件的变量。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>示例

下面的代码示例将每个 rebar 带区设置为相同宽度。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

##  <a name="setbarinfo"></a>CReBarCtrl：： SetBarInfo

实现 Win32 消息[RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)的行为，如 Windows SDK 中所述。

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>参数

*prbi*<br/>
指向[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)结构的指针，该结构包含要设置的信息。 发送此消息前`cbSize` ，必须将此结构`sizeof(REBARINFO)`的成员设置为

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

##  <a name="setbkcolor"></a>CReBarCtrl：： SetBkColor

实现 Win32 消息[RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)的行为，如 Windows SDK 中所述。

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*clr*<br/>
COLORREF 值，它表示新的默认背景色。

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/win32/gdi/colorref)值，该值表示以前的默认背景色。

### <a name="remarks"></a>备注

请参阅此主题，了解有关何时设置背景颜色以及如何设置默认值的详细信息。

##  <a name="setcolorscheme"></a>CReBarCtrl：： SetColorScheme

为 rebar 控件上的按钮设置配色方案。

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>参数

*lpcs*<br/>
指向[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构的指针，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

`COLORSCHEME`结构包含按钮突出显示颜色和按钮阴影颜色。

##  <a name="setextendedstyle"></a>CReBarCtrl：： SetExtendedStyle

设置当前 rebar 控件的扩展样式。

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*dwMask*|中指定*dwStyleEx*参数中的哪些标志适用的标志的按位组合（OR）。 使用以下一个或多个值：<br /><br /> RBS_EX_SPLITTER:默认情况下，在水平模式下的底部显示拆分器，并在垂直模式下显示在右侧。<br /><br /> RBS_EX_TRANSPARENT:将[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)消息转发到父窗口。|
|*dwStyleEx*|中标志的按位组合（OR），指定要应用的样式。 若要设置样式，请指定在*dwMask*参数中使用的同一标志。 若要重置样式，请指定二进制零。|

### <a name="return-value"></a>返回值

以前的扩展样式。

### <a name="remarks"></a>备注

此方法发送[RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle)消息，如 Windows SDK 中所述。

##  <a name="setimagelist"></a>CReBarCtrl：： SetImageList

将图像列表分配给 rebar 控件。

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针，该对象包含要分配给 rebar 控件的图像列表。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="setowner"></a>  CReBarCtrl::SetOwner

实现 Win32 消息[RB_SETPARENT](/windows/win32/Controls/rb-setparent)的行为，如 Windows SDK 中所述。

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向要设置为`CWnd` rebar 控件所有者的对象的指针。

### <a name="return-value"></a>返回值

指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是 rebar 控件的当前所有者。

### <a name="remarks"></a>备注

请注意，此成员函数将指针`CWnd`同时用于 rebar 控件的当前和选定的所有者，而不是指向 windows 的句柄。

> [!NOTE]
>  此成员函数不会更改在创建控件时设置的实际父级;相反，它会将通知消息发送到您指定的窗口。

##  <a name="setpalette"></a>CReBarCtrl：： SetPalette

实现 Win32 消息[RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)的行为，如 Windows SDK 中所述。

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>参数

*hPal*<br/>
一个 HPALETTE，指定 rebar 控件将使用的新调色板。

### <a name="return-value"></a>返回值

指向指定 rebar 控件上一调色板的[CPalette](../../mfc/reference/cpalette-class.md)对象的指针。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CPalette`对象作为其返回值，而不是 HPALETTE。

##  <a name="settextcolor"></a>CReBarCtrl：： SetTextColor

实现 Win32 消息[RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)的行为，如 Windows SDK 中所述。

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*clr*<br/>
一个 COLORREF 值，该值表示`CReBarCtrl`对象中的新文本颜色。

### <a name="return-value"></a>返回值

表示与`CReBarCtrl`对象关联的上一个文本颜色的 [COLORREF](/windows/win32/gdi/colorref) 值。

### <a name="remarks"></a>备注

提供它是为了支持 rebar 控件中的文本颜色灵活性。

##  <a name="settooltips"></a>CReBarCtrl：： SetToolTips

将工具提示控件与 rebar 控件相关联。

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>参数

*pToolTip*<br/>
指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针

### <a name="remarks"></a>备注

完成后，必须`CToolTipCtrl`销毁对象。

##  <a name="setwindowtheme"></a>CReBarCtrl：： SetWindowTheme

设置 rebar 控件的视觉样式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>参数

*pszSubAppName*<br/>
指向包含要设置的 rebar 视觉样式的 Unicode 字符串的指针。

### <a name="return-value"></a>返回值

不使用返回值。

### <a name="remarks"></a>备注

此成员函数模拟[RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme)消息的功能，如 Windows SDK 中所述。

##  <a name="showband"></a>CReBarCtrl：： ShowBand

实现 Win32 消息[RB_SHOWBAND](/windows/win32/Controls/rb-showband)的行为，如 Windows SDK 中所述。

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>参数

*uBand*<br/>
Rebar 控件中带区的从零开始的索引。

*fShow*<br/>
指示是否应显示或隐藏带区。 如果此值为 TRUE，则将显示带区。 否则，将隐藏带区。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="sizetorect"></a>CReBarCtrl：： SizeToRect

实现 Win32 消息[RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)的行为，如 Windows SDK 中所述。

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>参数

*rect*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的引用，该对象指定要调整 rebar 控件大小的矩形。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CRect`对象作为参数，而不`RECT`是结构。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
