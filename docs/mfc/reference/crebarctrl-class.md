---
title: CReBarCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f1ed4193111fa97e7fb113a86c7600ba462f059
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067847"
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
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|构造 `CReBarCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|将 rebar 控件放置到拖放模式。|
|[CReBarCtrl::Create](#create)|创建 rebar 控件，并将其附加到`CReBarCtrl`对象。|
|[CReBarCtrl::CreateEx](#createex)|使用指定的 Windows 扩展样式创建 rebar 控件，并将其附加到`CReBarCtrl`对象。|
|[CReBarCtrl::DeleteBand](#deleteband)|从 rebar 控件中删除带区。|
|[CReBarCtrl::DragMove](#dragmove)|在调用后更新 rebar 控件中的拖动位置`BeginDrag`。|
|[CReBarCtrl::EndDrag](#enddrag)|Rebar 控件的拖放操作将终止。|
|[CReBarCtrl::GetBandBorders](#getbandborders)|检索外的边框。|
|[CReBarCtrl::GetBandCount](#getbandcount)|检索当前在 rebar 控件中的带区计数。|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|检索有关指定带区的 rebar 控件中的信息。|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|检索外的边距。|
|[CReBarCtrl::GetBarHeight](#getbarheight)|检索 rebar 控件的高度。|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|检索有关 rebar 控件和它使用的图像列表的信息。|
|[CReBarCtrl::GetBkColor](#getbkcolor)|检索 rebar 控件的默认背景色。|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|检索[要添加的配色](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)与 rebar 控件关联的结构。|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|检索 rebar 控件的`IDropTarget`接口指针。|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|获取当前的 rebar 控件的扩展的样式。|
|[CReBarCtrl::GetImageList](#getimagelist)|检索与 rebar 控件关联的图像列表。|
|[CReBarCtrl::GetPalette](#getpalette)|检索 rebar 控件的当前调色板。|
|[CReBarCtrl::GetRect](#getrect)|检索给定带区的 rebar 控件中的边界矩形。|
|[CReBarCtrl::GetRowCount](#getrowcount)|检索外 rebar 控件中的行的数。|
|[CReBarCtrl::GetRowHeight](#getrowheight)|检索在 rebar 控件中指定行的高度。|
|[CReBarCtrl::GetTextColor](#gettextcolor)|检索 rebar 控件的默认文本颜色。|
|[CReBarCtrl::GetToolTips](#gettooltips)|检索与 rebar 控件相关联的任何工具提示控件的句柄。|
|[CReBarCtrl::HitTest](#hittest)|确定此时存在 rebar 带区，rebar 带区的哪个部分将为在屏幕上给定点处。|
|[CReBarCtrl::IDToIndex](#idtoindex)|将外标识符 (ID) 转换为 rebar 控件中的带区索引。|
|[Crebarctrl:: Insertband](#insertband)|在 rebar 控件中插入新的带区。|
|[CReBarCtrl::MaximizeBand](#maximizeband)|调整到其最大大小的 rebar 控件中的带的大小。|
|[CReBarCtrl::MinimizeBand](#minimizeband)|调整到其最小大小的 rebar 控件中的带的大小。|
|[CReBarCtrl::MoveBand](#moveband)|将带区从一个索引移到另一个。|
|[CReBarCtrl::PushChevron](#pushchevron)|以编程方式将推送 v 形展开按钮。|
|[CReBarCtrl::RestoreBand](#restoreband)|调整到其理想大小 rebar 控件中的带区的大小。|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Rebar 控件中设置的现有外的特征。|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|设置当前的 rebar 控件中的指定停靠带区的宽度。|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|设置对 rebar 控件的特征。|
|[CReBarCtrl::SetBkColor](#setbkcolor)|设置 rebar 控件的默认背景色。|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Rebar 控件上设置按钮的颜色方案。|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|设置当前的 rebar 控件的扩展的样式。|
|[CReBarCtrl::SetImageList](#setimagelist)|设置 rebar 控件的图像列表。|
|[CReBarCtrl::SetOwner](#setowner)|设置 rebar 控件的所有者窗口。|
|[CReBarCtrl::SetPalette](#setpalette)|设置了 rebar 控件的当前调色板。|
|[CReBarCtrl::SetTextColor](#settextcolor)|设置 rebar 控件的默认文本颜色。|
|[CReBarCtrl::SetToolTips](#settooltips)|将工具提示控件与 rebar 控件相关联。|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|设置 rebar 控件的视觉样式。|
|[CReBarCtrl::ShowBand](#showband)|显示或隐藏 rebar 控件中的给定的带。|
|[CReBarCtrl::SizeToRect](#sizetorect)|适用于将 rebar 控件与指定的矩形。|

## <a name="remarks"></a>备注

Rebar 控件所驻留的应用程序将分配到 rebar 带区的 rebar 控件所包含的子窗口。 子窗口是通常为另一常见的控件。

Rebar 控件包含一个或多个带区。 每个带区可以包含一个手柄栏、 位图、 文本标签和子窗口的组合。 带区只能包含一个的每个这些项。

Rebar 控件可以指定的背景位图上显示的子窗口。 所有的 rebar 控件带区可进行调整，除了那些使用 RBBS_FIXEDSIZE 样式。 当重新定位或调整大小 rebar 控件带区，rebar 控件管理的大小和分配给该带区子窗口的位置。 若要调整大小或更改的控件中的带区的顺序，单击并拖动带区的手柄栏。

下图显示了具有三个带区的 rebar 控件：

- 一个带区 0 包含平面、 透明工具栏控件。

- 一个带区 1 包含这两个透明的标准和透明下拉按钮。

- 一个带区 2 包含组合框和四个标准按钮。

     ![Rebar 菜单示例](../../mfc/reference/media/vc4scc1.gif "vc4scc1")

## <a name="rebar-control"></a>Rebar 控件

Rebar 控件的支持：

- 图像列表。

- 消息处理。

- 自定义绘制功能。

- 各种除了标准的窗口样式的控件样式。 这些样式的列表，请参阅[Rebar 控件样式](/windows/desktop/Controls/rebar-control-styles)Windows SDK 中。

有关详细信息，请参阅[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag

实现 Win32 消息的行为[RB_BEGINDRAG](/windows/desktop/Controls/rb-begindrag)，如 Windows SDK 中所述。

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>参数

*uBand*<br/>
拖放操作将产生影响的带区的从零开始索引。

*dwPos*<br/>
包含起始的 DWORD 值鼠标坐标。 使用 LOWORD 中包含的水平坐标和 HIWORD 中包含的垂直坐标。 如果通过 (DWORD)-1，rebar 控件将使用上一次调用控件的线程的鼠标的位置`GetMessage`或`PeekMessage`。

##  <a name="create"></a>  CReBarCtrl::Create

创建 rebar 控件，并将其附加到`CReBarCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定应用于控件的 rebar 控件样式的组合。 请参阅[Rebar 控件样式](/windows/desktop/Controls/rebar-control-styles)Windows SDK for 支持样式的列表中。

*rect*<br/>
对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它是位置和 rebar 控件的大小。

*pParentWnd*<br/>
一个指向[CWnd](../../mfc/reference/cwnd-class.md)是 rebar 控件的父窗口的对象。 它不能为 NULL。

*nID*<br/>
指定了 rebar 控件的控件 id。

### <a name="return-value"></a>返回值

如果成功，则创建对象时，非零值否则为 0。

### <a name="remarks"></a>备注

在两个步骤中创建 rebar 控件：

1. 调用[CReBarCtrl](#crebarctrl)构造`CReBarCtrl`对象。

1. 调用此成员函数，将创建 Windows rebar 控件并将其附加到`CReBarCtrl`对象。

当您调用`Create`，公共控件进行初始化。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

##  <a name="createex"></a>  CReBarCtrl::CreateEx

创建控件 （子窗口），并将其与`CReBarCtrl`对象。

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
指定要创建的控件的扩展的样式。 扩展 Windows 样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*dwStyle*<br/>
指定应用于控件的 rebar 控件样式的组合。 有关受支持的样式的列表，请参阅[Rebar 控件样式](/windows/desktop/Controls/rebar-control-styles)Windows SDK 中。

*rect*<br/>
对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口的工作区中创建的位置*pParentWnd*。

*pParentWnd*<br/>
指向控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[创建](#create)若要将应用扩展的 Windows 样式，指定的 Windows 扩展的样式加**WS_EX_**。

##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl

创建一个 `CReBarCtrl` 对象。

```
CReBarCtrl();
```

### <a name="example"></a>示例

  有关示例，请参阅[CReBarCtrl::Create](#create)。

##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand

实现 Win32 消息的行为[RB_DELETEBAND](/windows/desktop/Controls/rb-deleteband)，如 Windows SDK 中所述。

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要删除的带区的从零开始索引。

### <a name="return-value"></a>返回值

如果成功，则删除带区，非零值否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

##  <a name="dragmove"></a>  CReBarCtrl::DragMove

实现 Win32 消息的行为[RB_DRAGMOVE](/windows/desktop/Controls/rb-dragmove)，如 Windows SDK 中所述。

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>参数

*dwPos*<br/>
一个 DWORD 值，该值包含新的鼠标坐标。 使用 LOWORD 中包含的水平坐标和 HIWORD 中包含的垂直坐标。 如果通过 (DWORD)-1，rebar 控件将使用上一次调用控件的线程的鼠标的位置`GetMessage`或`PeekMessage`。

##  <a name="enddrag"></a>  CReBarCtrl::EndDrag

实现 Win32 消息的行为[RB_ENDDRAG](/windows/desktop/Controls/rb-enddrag)，如 Windows SDK 中所述。

```
void EndDrag();
```

##  <a name="getbandborders"></a>  CReBarCtrl::GetBandBorders

实现 Win32 消息的行为[RB_GETBANDBORDERS](/windows/desktop/Controls/rb-getbandborders)，如 Windows SDK 中所述。

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>参数

*uBand*<br/>
带区为其检索边框的从零开始索引。

*中华人民共和国*<br/>
一个指向[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它将接收外边框。 如果 rebar 控件具有 RBS_BANDBORDERS 样式，此结构的每个成员将收到像素的数，在相应的一端外，构成边框。 如果对 rebar 控件不具有 RBS_BANDBORDERS 样式，仅此结构的左侧的成员接收有效的信息。 Rebar 控件样式的说明，请参阅[Rebar 控件样式](/windows/desktop/Controls/rebar-control-styles)Windows SDK 中。

##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount

实现 Win32 消息的行为[RB_GETBANDCOUNT](/windows/desktop/Controls/rb-getbandcount)，如 Windows SDK 中所述。

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>返回值

分配给控件的带区的数目。

##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo

实现 Win32 消息的行为[RB_GETBANDINFO](/windows/desktop/Controls/rb-getbandinfo) Windows SDK 中所述。

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>参数

*uBand*<br/>
将为其检索信息的带区的从零开始索引。

*prbbi*<br/>
一个指向[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)结构，以接收带区信息。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`并设置`fMask`成员添加到你想要发送此消息之前检索的项。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins

检索外的边距。

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>参数

*pMargins*<br/>
一个指向[边距](/windows/desktop/api/uxtheme/ns-uxtheme-_margins)结构，它将接收的信息。

### <a name="remarks"></a>备注

此成员函数模拟的功能[RB_GETBANDMARGINS](/windows/desktop/Controls/rb-getbandmargins)消息，如 Windows SDK 中所述。

##  <a name="getbarheight"></a>  CReBarCtrl::GetBarHeight

检索 rebar 条的高度。

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>返回值

表示高度 （像素），该控件的值。

##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo

实现 Win32 消息的行为[RB_GETBARINFO](/windows/desktop/Controls/rb-getbarinfo)，如 Windows SDK 中所述。

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>参数

*prbi*<br/>
一个指向[REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo)将收到 rebar 控制信息的结构。 必须设置*cbSize*到此结构的成员`sizeof(REBARINFO)`之前发送此消息。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor

实现 Win32 消息的行为[RB_GETBKCOLOR](/windows/desktop/Controls/rb-getbkcolor)，如 Windows SDK 中所述。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

一个 COLORREF 值，该值表示当前的默认背景色。

##  <a name="getcolorscheme"></a>  CReBarCtrl::GetColorScheme

检索[要添加的配色](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)rebar 控件的结构。

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>参数

*lpc*<br/>
一个指向[要添加的配色](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)结构，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

`COLORSCHEME`结构包括按钮突出显示颜色和按钮阴影颜色。

##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget

实现 Win32 消息的行为[RB_GETDROPTARGET](/windows/desktop/Controls/rb-getdroptarget)，如 Windows SDK 中所述。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>返回值

一个指向[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)接口。

##  <a name="getextendedstyle"></a>  CReBarCtrl::GetExtendedStyle

获取当前的 rebar 控件的扩展的样式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>返回值

指示扩展的样式标志的按位组合 (OR)。 可能的标志是 RBS_EX_SPLITTER 和 RBS_EX_TRANSPARENT。 有关详细信息，请参阅*dwMask*的参数[CReBarCtrl::SetExtendedStyle](#setextendedstyle)方法。

### <a name="remarks"></a>备注

此方法将发送[RB_GETEXTENDEDSTYLE](/windows/desktop/Controls/rb-dragmove)消息，Windows SDK 中所述。

##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList

获取`CImageList`与 rebar 控件相关联的对象。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象。 如果为控件不设置任何图像列表，返回 NULL。

### <a name="remarks"></a>备注

此成员函数使用大小和掩码信息存储在[REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo)结构，如 Windows SDK 中所述。

##  <a name="getpalette"></a>  CReBarCtrl::GetPalette

检索 rebar 控件的当前调色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>返回值

一个指向[CPalette](../../mfc/reference/cpalette-class.md)对象，它指定了 rebar 控件的当前调色板。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CPalette`对象作为其返回值，而不是 HPALETTE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

##  <a name="getrect"></a>  CReBarCtrl::GetRect

实现 Win32 消息的行为[RB_GETRECT](/windows/desktop/Controls/rb-getrect)，如 Windows SDK 中所述。

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>参数

*uBand*<br/>
在 rebar 控件带区的从零开始索引。

*中华人民共和国*<br/>
一个指向[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它将接收 rebar 带区的边界。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount

实现 Win32 消息的行为[RB_GETROWCOUNT](/windows/desktop/Controls/rb-getrowcount)，如 Windows SDK 中所述。

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>返回值

一个 UINT 值，该值表示控件中的带外行数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

##  <a name="getrowheight"></a>  CReBarCtrl::GetRowHeight

实现 Win32 消息的行为[RB_GETROWHEIGHT](/windows/desktop/Controls/rb-getrowheight)，如 Windows SDK 中所述。

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>参数

*uRow*<br/>
将具有检索其高度的带区的从零开始索引。

### <a name="return-value"></a>返回值

一个 UINT 值，该值表示行高度，以像素为单位。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor

实现 Win32 消息的行为[RB_GETTEXTCOLOR](/windows/desktop/Controls/rb-gettextcolor)，如 Windows SDK 中所述。

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>返回值

一个 COLORREF 值，该值表示当前的默认文本颜色。

##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips

实现 Win32 消息的行为[RB_GETTOOLTIPS](/windows/desktop/Controls/rb-gettooltips)，如 Windows SDK 中所述。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>返回值

一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象。

### <a name="remarks"></a>备注

请注意，MFC 实现`GetToolTips`返回一个指向`CToolTipCtrl`，而不是 HWND。

##  <a name="hittest"></a>  CReBarCtrl::HitTest

实现 Win32 消息的行为[RB_HITTEST](/windows/desktop/Controls/rb-hittest)，如 Windows SDK 中所述。

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>参数

*prbht*<br/>
一个指向[RBHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_rb_hittestinfo)结构。 发送该消息前`pt`此结构的成员必须初始化为客户端坐标中，进行测试的点。

### <a name="return-value"></a>返回值

在给定的时间，则为-1 点处没有 rebar 带区是否带区从零开始的索引。

##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex

实现 Win32 消息的行为[RB_IDTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774496)，如 Windows SDK 中所述。

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>参数

*uBandID*<br/>
指定带区的应用程序定义的标识符中传递`wID`的成员[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)结构时插入带区。

### <a name="return-value"></a>返回值

如果成功，相应的索引从零开始的带外或否则为-1。 如果存在重复的带区索引，则返回第一个。

##  <a name="insertband"></a>  Crebarctrl:: Insertband

实现 Win32 消息的行为[RB_INSERTBAND](/windows/desktop/Controls/rb-insertband)，如 Windows SDK 中所述。

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>参数

*uIndex*<br/>
在此处插入带区的位置的从零开始索引。 如果将此参数设置为-1，该控件将在最后一个位置添加新的带区。

*prbbi*<br/>
一个指向[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)结构，它定义要插入的带区。 必须设置*cbSize*到此结构的成员`sizeof(REBARBANDINFO)`之前调用此函数。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

##  <a name="maximizeband"></a>  CReBarCtrl::MaximizeBand

调整到其最大大小的 rebar 控件中的带的大小。

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
若要最大化的带区的从零开始索引。

### <a name="remarks"></a>备注

实现 Win32 消息的行为[RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband)与`fIdeal`设置为 0，Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

##  <a name="minimizeband"></a>  CReBarCtrl::MinimizeBand

调整到其最小大小的 rebar 控件中的带的大小。

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
要最小化带区的从零开始索引。

### <a name="remarks"></a>备注

实现 Win32 消息的行为[RB_MINIMIZEBAND](/windows/desktop/Controls/rb-minimizeband)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

##  <a name="moveband"></a>  CReBarCtrl::MoveBand

实现 Win32 消息的行为[RB_MOVEBAND](/windows/desktop/Controls/rb-moveband)，如 Windows SDK 中所述。

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>参数

*uFrom*<br/>
要移动的带区的从零开始索引。

*uTo*<br/>
新外位置的从零开始索引。 永远不会，此参数值必须大于减一的带区的数目。 若要获取带区的数目，请调用[GetBandCount](#getbandcount)。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron

实现 Win32 消息的行为[RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron)，如 Windows SDK 中所述。

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>参数

*uBand*<br/>
带区的 v 形图标是要推送的从零开始索引。

*lAppValue*<br/>
应用程序定义的 32 位值。 请参阅*lAppValue*中[RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron) Windows SDK 中。

##  <a name="restoreband"></a>  CReBarCtrl::RestoreBand

调整到其理想大小 rebar 控件中的带区的大小。

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>参数

*uBand*<br/>
若要最大化的带区的从零开始索引。

### <a name="remarks"></a>备注

实现 Win32 消息的行为[RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband)与`fIdeal`设置为 1，Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

##  <a name="setbandinfo"></a>  CReBarCtrl::SetBandInfo

实现 Win32 消息的行为[RB_SETBANDINFO](/windows/desktop/Controls/rb-setbandinfo)，如 Windows SDK 中所述。

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>参数

*uBand*<br/>
若要接收新设置的带区的从零开始索引。

*prbbi*<br/>
指向[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)结构，它定义要插入的带区。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`之前发送此消息。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

##  <a name="setbandwidth"></a>  CReBarCtrl::SetBandWidth

设置当前的 rebar 控件中的指定停靠带区的宽度。

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*uBand*|[in]Rebar 带区从零开始索引。|
|*cxWidth*|[in]新的 rebar 带区，以像素为单位的宽度。|

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[RB_SETBANDWIDTH](/windows/desktop/Controls/rb-setbandwidth)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_rebar`，即用于访问当前的 rebar 控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>示例

下面的代码示例设置每个 rebar 带区是相同的宽度。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo

实现 Win32 消息的行为[RB_SETBARINFO](/windows/desktop/Controls/rb-setbarinfo)，如 Windows SDK 中所述。

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>参数

*prbi*<br/>
一个指向[REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo)结构，其中包含要设置的信息。 必须设置`cbSize`到此结构的成员`sizeof(REBARINFO)`发送此消息之前

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor

实现 Win32 消息的行为[RB_SETBKCOLOR](/windows/desktop/Controls/rb-setbkcolor)，如 Windows SDK 中所述。

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*clr*<br/>
COLORREF 值，该值表示新的默认背景色。

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/desktop/gdi/colorref)值，该值表示以前的默认背景色。

### <a name="remarks"></a>备注

请参阅本主题详细了解何时设置背景色，以及如何设置默认值。

##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme

Rebar 控件上设置按钮的颜色方案。

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>参数

*lpc*<br/>
一个指向[要添加的配色](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme)结构，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

`COLORSCHEME`结构包括按钮突出显示颜色和按钮阴影颜色。

##  <a name="setextendedstyle"></a>  CReBarCtrl::SetExtendedStyle

设置当前的 rebar 控件的扩展的样式。

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*dwMask*|[in]指定在哪些标志的标志的按位组合 (OR) *dwStyleEx*参数应用。 使用一个或多个以下值：<br /><br /> RBS_EX_SPLITTER： 默认情况下，显示与拆分器上底部在水平模式下和向右垂直模式。<br /><br /> RBS_EX_TRANSPARENT： 转发[WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd)向父窗口的消息。|
|*dwStyleEx*|[in]按位组合 (OR) 标志，用于指定要应用的样式。 若要设置样式，请指定中使用的相同标志*dwMask*参数。 若要重置样式，请指定二进制零。|

### <a name="return-value"></a>返回值

以前的扩展的样式。

### <a name="remarks"></a>备注

此方法将发送[RB_SETEXTENDEDSTYLE](/windows/desktop/Controls/rb-setextendedstyle)消息，Windows SDK 中所述。

##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList

将图像列表分配到 rebar 控件。

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象，其中包含要分配到 rebar 控件的图像列表。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="setowner"></a>  CReBarCtrl::SetOwner

实现 Win32 消息的行为[RB_SETPARENT](/windows/desktop/Controls/rb-setparent)，如 Windows SDK 中所述。

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
一个指向`CWnd`对象将设为 rebar 控件的所有者。

### <a name="return-value"></a>返回值

一个指向[CWnd](../../mfc/reference/cwnd-class.md) rebar 控件的当前所有者的对象。

### <a name="remarks"></a>备注

请注意，此成员函数使用指向`CWnd`rebar 控件的当前和所选所有者对象而不是句柄到 windows。

> [!NOTE]
>  此成员函数不会更改实际创建该控件; 时设置的父级而是会向您指定的窗口发送通知消息。

##  <a name="setpalette"></a>  CReBarCtrl::SetPalette

实现 Win32 消息的行为[RB_SETPALETTE](/windows/desktop/Controls/rb-setpalette)，如 Windows SDK 中所述。

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>参数

*hPal*<br/>
指定新的 rebar 控件将使用的调色板 HPALETTE。

### <a name="return-value"></a>返回值

一个指向[CPalette](../../mfc/reference/cpalette-class.md)对象，它指定了 rebar 控件的上一个面板。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CPalette`对象作为其返回值，而不是 HPALETTE。

##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor

实现 Win32 消息的行为[RB_SETTEXTCOLOR](/windows/desktop/Controls/rb-settextcolor)，如 Windows SDK 中所述。

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*clr*<br/>
COLORREF 值，该值表示新的文本颜色`CReBarCtrl`对象。

### <a name="return-value"></a>返回值

[COLORREF](/windows/desktop/gdi/colorref)与关联的值，该值表示前一种文本颜色`CReBarCtrl`对象。

### <a name="remarks"></a>备注

它旨在支持 rebar 控件中的文本颜色灵活性。

##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips

将工具提示控件与 rebar 控件相关联。

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>参数

*pToolTip*<br/>
一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象

### <a name="remarks"></a>备注

您必须销毁`CToolTipCtrl`对象都完成。

##  <a name="setwindowtheme"></a>  CReBarCtrl::SetWindowTheme

设置 rebar 控件的视觉样式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>参数

*pszSubAppName*<br/>
指向包含 rebar 视觉样式设置的 Unicode 字符串的指针。

### <a name="return-value"></a>返回值

不使用返回的值。

### <a name="remarks"></a>备注

此成员函数模拟的功能[RB_SETWINDOWTHEME](/windows/desktop/Controls/rb-setwindowtheme)消息，如 Windows SDK 中所述。

##  <a name="showband"></a>  CReBarCtrl::ShowBand

实现 Win32 消息的行为[RB_SHOWBAND](/windows/desktop/Controls/rb-showband)，如 Windows SDK 中所述。

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>参数

*uBand*<br/>
在 rebar 控件带区的从零开始索引。

*fShow*<br/>
指示是否应显示还是隐藏带区。 如果此值为 TRUE，将显示带区。 否则，将隐藏带区。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

##  <a name="sizetorect"></a>  CReBarCtrl::SizeToRect

实现 Win32 消息的行为[RB_SIZETORECT](/windows/desktop/Controls/rb-sizetorect)，如 Windows SDK 中所述。

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>参数

*rect*<br/>
对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)指定 rebar 控件的大小应调整为的矩形的对象。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CRect`对象作为参数，而非`RECT`结构。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

