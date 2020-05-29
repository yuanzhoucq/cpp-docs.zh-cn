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
ms.openlocfilehash: 930322f1803eba7709505018c77ecea3f816dd15
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750635"
---
# <a name="crebarctrl-class"></a>CReBarCtrl 类

封装 Rebar 控件的功能，此控件是一个子窗口容器。

## <a name="syntax"></a>语法

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CReBarCtrl：CRebarCtrl](#crebarctrl)|构造 `CReBarCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CReBarCtrl：：开始拖动](#begindrag)|将钢筋控件置于拖放模式。|
|[CReBarCtrl：：创建](#create)|创建钢筋控件并将其附加到`CReBarCtrl`对象。|
|[CReBarCtrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建钢筋控件，并将其附加到`CReBarCtrl`对象。|
|[CReBarCtrl：:DeleteBand](#deleteband)|从钢筋控件中删除带。|
|[CReBarCtrl：:D拉格移动](#dragmove)|调用 后，在钢筋控件中更新拖动位置`BeginDrag`。|
|[CReBarCtrl：：结束拖动](#enddrag)|终止钢筋控件的拖放操作。|
|[CReBarCtrl：：获取班德边界](#getbandborders)|检索波段的边界。|
|[CReBarCtrl：：GetBandCount](#getbandcount)|检索钢筋控件中当前波段的计数。|
|[CReBarCtrl：：获取班德信息](#getbandinfo)|检索钢筋控件中指定频段的信息。|
|[CReBarCtrl：：获取带边距](#getbandmargins)|检索波段的边距。|
|[CReBarCtrl：：获取巴尔高度](#getbarheight)|检索钢筋控件的高度。|
|[CReBarCtrl：：获取巴信息](#getbarinfo)|检索有关钢筋控件及其使用的图像列表的信息。|
|[CReBarCtrl：GetBkColor](#getbkcolor)|检索钢筋控件的默认背景颜色。|
|[CReBarCtrl：获取颜色方案](#getcolorscheme)|检索与钢筋控件关联的[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构。|
|[CReBarCtrl：：获取DropTarget](#getdroptarget)|检索钢筋控件的`IDropTarget`接口指针。|
|[CReBarCtrl：：获取扩展样式](#getextendedstyle)|获取当前钢筋控件的扩展样式。|
|[CReBarCtrl：获取图像列表](#getimagelist)|检索与钢筋控件关联的图像列表。|
|[CReBarCtrl：：获取调色板](#getpalette)|检索钢筋控件的当前调色板。|
|[CReBarCtrl：：获取雷ct](#getrect)|检索钢筋控件中给定波段的边界矩形。|
|[CReBarCtrl：：获取罗计数](#getrowcount)|检索钢筋控件中的波段行数。|
|[CReBarCtrl：：获取罗高](#getrowheight)|检索钢筋控件中指定行的高度。|
|[CReBarCtrl：：获取文本颜色](#gettextcolor)|检索钢筋控件的默认文本颜色。|
|[CReBarCtrl：获取工具提示](#gettooltips)|检索与钢筋控件关联的任何工具尖端控件的句柄。|
|[CReBarCtrl：hitTest](#hittest)|确定钢筋带的哪个部分位于屏幕上的给定点，如果此时存在钢筋带。|
|[CReBarCtrl：：IDTOIndex](#idtoindex)|将带标识符 （ID） 转换为钢筋控件中的波段索引。|
|[CReBarCtrl：：插入带](#insertband)|在钢筋控件中插入新频段。|
|[CReBarCtrl：：最大化乐队](#maximizeband)|将钢筋控件中的频带调整到其最大大小。|
|[CReBarCtrl：：最小化带](#minimizeband)|将钢筋控件中的频带调整到其最小大小。|
|[CReBarCtrl：：移动带](#moveband)|将波段从一个索引移动到另一个索引。|
|[CReBarCtrl：:P乌什·雪佛龙](#pushchevron)|以编程方式推送 V 形。|
|[CReBarCtrl：：恢复乐队](#restoreband)|将钢筋控件中的频带调整到其理想大小。|
|[CReBarCtrl：：SetBandinfo](#setbandinfo)|设置钢筋控件中现有频段的特征。|
|[CReBarCtrl：：设置带宽度](#setbandwidth)|设置当前钢筋控件中指定停靠带的宽度。|
|[CReBarCtrl：：SetBarinfo](#setbarinfo)|设置钢筋控件的特征。|
|[CReBarCtrl：setBkColor](#setbkcolor)|设置钢筋控件的默认背景颜色。|
|[CReBarCtrl：：设置颜色方案](#setcolorscheme)|设置钢筋控件上的按钮的配色方案。|
|[CReBarCtrl：：设置扩展样式](#setextendedstyle)|设置当前钢筋控件的扩展样式。|
|[CReBarCtrl：：设置图像列表](#setimagelist)|设置钢筋控件的图像列表。|
|[CReBarCtrl：：SetOwner](#setowner)|设置钢筋控件的所有者窗口。|
|[CReBarCtrl：：设置调色板](#setpalette)|设置钢筋控件的当前调色板。|
|[CReBarCtrl：：设置文本颜色](#settextcolor)|设置钢筋控件的默认文本颜色。|
|[CReBarCtrl：：设置工具提示](#settooltips)|将工具尖端控件与钢筋控件关联。|
|[CReBarCtrl：：设置窗口主题](#setwindowtheme)|设置钢筋控件的可视样式。|
|[CReBarCtrl：：显示乐队](#showband)|在钢筋控件中显示或隐藏给定波段。|
|[CreBarctrl：大小托雷](#sizetorect)|将钢筋控件拟合到指定的矩形。|

## <a name="remarks"></a>备注

钢筋控件所在的应用程序将钢筋控件中包含的子窗口分配给钢筋带。 子窗口通常是另一个常见控件。

钢筋控件包含一个或多个波段。 每个波段可以包含夹持栏、位图、文本标签和子窗口的组合。 波段只能包含其中一个项目。

钢筋控件可以在指定的后台位图上显示子窗口。 所有钢筋控制带都可以调整大小，但使用RBBS_FIXEDSIZE样式的带除外。 重新定位或调整钢筋控制带的大小时，钢筋控件将管理分配给该频段的子窗口的大小和位置。 要调整控件中波段的大小或更改顺序，请单击并拖动带的夹持杆。

下图显示了具有三个波段的钢筋控件：

- 波段 0 包含一个扁平的、透明的工具栏控件。

- 波段 1 包含透明标准和透明下拉按钮。

- 波段 2 包含一个组合框和四个标准按钮。

   ![Rebar 菜单示例](../../mfc/reference/media/vc4scc1.gif "Rebar 菜单示例")

## <a name="rebar-control"></a>钢筋控制

钢筋控件支持：

- 图像列表。

- 消息处理。

- 自定义绘图功能。

- 除了标准窗口样式之外，还有多种控制样式。 有关这些样式的列表，请参阅 Windows SDK 中的[钢筋控件样式](/windows/win32/Controls/rebar-control-styles)。

有关详细信息，请参阅使用[CRebarCtrl](../../mfc/using-crebarctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a>CReBarCtrl：：开始拖动

实现 Win32 消息[RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag)的行为，如 Windows SDK 中所述。

```cpp
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
拖放操作将影响的波段的零基索引。

*德波普斯*<br/>
包含启动鼠标坐标的 DWORD 值。 水平坐标包含在 LOWORD 中，垂直坐标包含在 HIWORD 中。 如果通过 （DWORD）-1，钢筋控件将在上次调用`GetMessage`控件的线程时`PeekMessage`使用鼠标的位置。

## <a name="crebarctrlcreate"></a><a name="create"></a>CReBarCtrl：：创建

创建钢筋控件并将其附加到`CReBarCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定应用于控件的钢筋控件样式的组合。 有关支持的样式列表，请参阅 Windows SDK 中的[钢筋控制样式](/windows/win32/Controls/rebar-control-styles)。

*矩形*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，即钢筋控件的位置和大小。

*pparentwnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是钢筋控件的父窗口。 值不得为 NULL。

*nID*<br/>
指定钢筋控件的控制 ID。

### <a name="return-value"></a>返回值

如果对象已成功创建，则非零;否则 0。

### <a name="remarks"></a>备注

通过两个步骤创建钢筋控件：

1. 调用[CReBarCtrl](#crebarctrl)构造`CReBarCtrl`对象。

1. 调用此成员函数，该函数创建 Windows 钢筋控件并将其附加到`CReBarCtrl`对象。

调用`Create`时调用 ，将初始化公共控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a>CReBarCtrl：：创建Ex

创建控件（子窗口），并将其与`CReBarCtrl`对象关联。

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
指定要创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定应用于控件的钢筋控件样式的组合。 有关支持的样式列表，请参阅 Windows SDK 中的[钢筋控制样式](/windows/win32/Controls/rebar-control-styles)。

*矩形*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式，该样式由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a>CReBarCtrl：CRebarCtrl

创建一个 `CReBarCtrl` 对象。

```
CReBarCtrl();
```

### <a name="example"></a>示例

  请参阅[CReBarCtrl 的示例：：创建](#create)。

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a>CReBarCtrl：:DeleteBand

实现 Win32 消息[RB_DELETEBAND](/windows/win32/Controls/rb-deleteband)的行为，如 Windows SDK 中所述。

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
要删除的波段的从零开始索引。

### <a name="return-value"></a>返回值

如果频带成功删除，则非零;否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a>CReBarCtrl：:D拉格移动

实现 Win32 消息[的行为RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove)，如 Windows SDK 中所述。

```cpp
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>参数

*德波普斯*<br/>
包含新鼠标坐标的 DWORD 值。 水平坐标包含在 LOWORD 中，垂直坐标包含在 HIWORD 中。 如果通过 （DWORD）-1，钢筋控件将在上次调用`GetMessage`控件的线程时`PeekMessage`使用鼠标的位置。

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a>CReBarCtrl：：结束拖动

实现 Win32 消息[RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)的行为，如 Windows SDK 中所述。

```cpp
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a>CReBarCtrl：：获取班德边界

实现 Win32 消息[RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders)的行为，如 Windows SDK 中所述。

```cpp
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>参数

*乌班德*<br/>
将为其检索边框的带的零基索引。

*中国*<br/>
指向将接收波段边框的[RECT](/windows/win32/api/windef/ns-windef-rect)结构的指针。 如果钢筋控件具有RBS_BANDBORDERS样式，则此结构的每个成员将收到构成边框的带子侧的像素数。 如果钢筋控件没有RBS_BANDBORDERS样式，则只有此结构的左侧成员才会接收有效信息。 有关钢筋控件样式的说明，请参阅 Windows SDK 中的[钢筋控件样式](/windows/win32/Controls/rebar-control-styles)。

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a>CReBarCtrl：：GetBandCount

实现 Win32 消息[RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount)的行为，如 Windows SDK 中所述。

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>返回值

分配给控件的频段数。

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a>CReBarCtrl：：获取班德信息

实现 Win32 消息的行为[RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) Windows SDK 中所述。

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>参数

*乌班德*<br/>
将为其检索信息的波段的零基索引。

*普尔比*<br/>
指向[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的指针，用于接收波段信息。 您必须将`cbSize`此结构的成员设置为`sizeof(REBARBANDINFO)`，`fMask`并将成员设置为要检索的项目，然后再发送此消息。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a>CReBarCtrl：：获取带边距

检索波段的边距。

```cpp
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>参数

*pMargins*<br/>
指向将接收信息[的 MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins)结构的指针。

### <a name="remarks"></a>备注

此成员函数模拟[RB_GETBANDMARGINS](/windows/win32/Controls/rb-getbandmargins)消息的功能，如 Windows SDK 中所述。

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a>CReBarCtrl：：获取巴尔高度

检索钢筋的高度。

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>返回值

表示控件的高度（以像素为单位）的值。

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a>CReBarCtrl：：获取巴信息

实现 Win32 消息[RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo)的行为，如 Windows SDK 中所述。

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>参数

*普尔比*<br/>
指向将接收钢筋控制信息的[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)结构的指针。 在发送此消息之前，必须为此结构的*cbSize*成员设置到`sizeof(REBARINFO)`。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a>CReBarCtrl：GetBkColor

实现 Win32 消息[RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor)的行为，如 Windows SDK 中所述。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

表示当前默认背景颜色的 COLORREF 值。

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CReBarCtrl：获取颜色方案

检索钢筋控件的[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构。

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>参数

*lpcs*<br/>
指向[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构的指针，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

该`COLORSCHEME`结构包括按钮高光颜色和按钮阴影颜色。

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a>CReBarCtrl：：获取DropTarget

实现 Win32 消息[RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget)的行为，如 Windows SDK 中所述。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>返回值

指向[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口的指针。

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CReBarCtrl：：获取扩展样式

获取当前钢筋控件的扩展样式。

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>返回值

指示扩展样式的标志的位组合 （OR）。 可能的标志RBS_EX_SPLITTER和RBS_EX_TRANSPARENT。 有关详细信息，请参阅[CReBarCtrl：set 扩展样式](#setextendedstyle)方法的*dwMask*参数。

### <a name="remarks"></a>备注

此方法发送[RB_GETEXTENDEDSTYLE](/windows/win32/Controls/rb-dragmove)消息，这在 Windows SDK 中介绍。

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a>CReBarCtrl：获取图像列表

获取与`CImageList`钢筋控件关联的对象。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>返回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针。 如果未为控件设置图像列表，则返回 NULL。

### <a name="remarks"></a>备注

此成员函数使用存储在[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)结构中的大小和掩码信息，如 Windows SDK 中所述。

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a>CReBarCtrl：：获取调色板

检索钢筋控件的当前调色板。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>返回值

指向指定钢筋控件当前调色板的[CPalette](../../mfc/reference/cpalette-class.md)对象的指针。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CPalette`对象作为其返回值，而不是 HPALETTE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a>CReBarCtrl：：获取雷ct

实现 Win32 消息[RB_GETRECT](/windows/win32/Controls/rb-getrect)的行为，如 Windows SDK 中所述。

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>参数

*乌班德*<br/>
钢筋控件中带的零基索引。

*中国*<br/>
指向[RECT](/windows/win32/api/windef/ns-windef-rect)结构的指针，该结构将接收钢筋带的边界。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a>CReBarCtrl：：获取罗计数

实现 Win32 消息[RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount)的行为，如 Windows SDK 中所述。

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>返回值

表示控件中带行数的 UINT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a>CReBarCtrl：：获取罗高

实现 Win32 消息[RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight)的行为，如 Windows SDK 中所述。

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>参数

*uRow*<br/>
将检索其高度的波段的从零开始索引。

### <a name="return-value"></a>返回值

表示行高度（以像素为单位）的 UINT 值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a>CReBarCtrl：：获取文本颜色

实现 Win32 消息[RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor)的行为，如 Windows SDK 中所述。

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>返回值

表示当前默认文本颜色的 COLORREF 值。

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a>CReBarCtrl：获取工具提示

实现 Win32 消息[RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips)的行为，如 Windows SDK 中所述。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>返回值

指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针。

### <a name="remarks"></a>备注

请注意，的`GetToolTips`MFC 实现返回指向 的`CToolTipCtrl`指针，而不是 HWND。

## <a name="crebarctrlhittest"></a><a name="hittest"></a>CReBarCtrl：hitTest

实现 Win32 消息[RB_HITTEST](/windows/win32/Controls/rb-hittest)的行为，如 Windows SDK 中所述。

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>参数

*普尔巴特*<br/>
指向[RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo)结构的指针。 在发送消息之前，`pt`必须初始化此结构的成员到将在客户端坐标中测试的点。

### <a name="return-value"></a>返回值

给定点处的波段的零基索引，如果点没有钢筋带，则为 -1。

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a>CReBarCtrl：：IDTOIndex

实现 Win32 消息[RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex)的行为，如 Windows SDK 中所述。

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>参数

*乌班德*<br/>
指定频段的应用程序定义标识符，在插入频段时在`wID` [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的成员中传递。

### <a name="return-value"></a>返回值

零基波段索引（如果成功）或 -1 否则。 如果存在重复的波段索引，则返回第一个波段索引。

## <a name="crebarctrlinsertband"></a><a name="insertband"></a>CReBarCtrl：：插入带

实现 Win32 消息[RB_INSERTBAND](/windows/win32/Controls/rb-insertband)的行为，如 Windows SDK 中所述。

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>参数

*uIndex*<br/>
将插入波段的位置的零基索引。 如果将此参数设置为 -1，则控件将在最后一个位置添加新波段。

*普尔比*<br/>
指向[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的指针，用于定义要插入的频带。 在调用此函数之前，必须为此结构的`sizeof(REBARBANDINFO)`*cbSize*成员设置。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a>CReBarCtrl：：最大化乐队

将钢筋控件中的频带调整到其最大大小。

```cpp
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
要最大化的波段的零基索引。

### <a name="remarks"></a>备注

实现 Win32 消息[的行为，RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband)设置为`fIdeal`0，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a>CReBarCtrl：：最小化带

将钢筋控件中的频带调整到其最小大小。

```cpp
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
要最小化的波段的零基索引。

### <a name="remarks"></a>备注

实现 Win32 消息[的行为RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a>CReBarCtrl：：移动带

实现 Win32 消息[RB_MOVEBAND](/windows/win32/Controls/rb-moveband)的行为，如 Windows SDK 中所述。

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>参数

*u 从*<br/>
要移动的波段的零基索引。

*uTo*<br/>
新波段位置的零基索引。 此参数值绝不能大于带数减去 1。 要获取频段数，请致电[GetBandCount](#getbandcount)。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a>CReBarCtrl：:P乌什·雪佛龙

实现 Win32 消息[RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)的行为，如 Windows SDK 中所述。

```cpp
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
其雪佛龙将推送的带的零基指数。

*lAppValue*<br/>
应用程序定义了 32 位值。 请参阅 windows SDK 中[RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron)中的*lAppValue。*

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a>CReBarCtrl：：恢复乐队

将钢筋控件中的频带调整到其理想大小。

```cpp
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
要最大化的波段的零基索引。

### <a name="remarks"></a>备注

实现 Win32 消息[的行为RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband)设置为`fIdeal`1，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a>CReBarCtrl：：SetBandinfo

实现 Win32 消息[RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo)的行为，如 Windows SDK 中所述。

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
用于接收新设置的波段的从零为基础的索引。

*普尔比*<br/>
指向定义要插入的频带的[REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)结构的指针。 在发送此消息之前`cbSize`，必须为此结构的成员`sizeof(REBARBANDINFO)`设置到 。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a>CReBarCtrl：：设置带宽度

设置当前钢筋控件中指定停靠带的宽度。

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*乌班德*|[在]钢筋带的零基索引。|
|*cxWidth*|[在]钢筋带的新宽度，以像素为单位。|

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[RB_SETBANDWIDTH](/windows/win32/Controls/rb-setbandwidth)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于访问当前钢筋控件`m_rebar`的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>示例

以下代码示例将每个钢筋带设置为相同的宽度。

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a>CReBarCtrl：：SetBarinfo

实现 Win32 消息[RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo)的行为，如 Windows SDK 中所述。

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>参数

*普尔比*<br/>
指向包含要设置的信息的[REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo)结构的指针。 在发送此消息`sizeof(REBARINFO)`之前`cbSize`，必须为此结构的成员设置

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a>CReBarCtrl：setBkColor

实现 Win32 消息[RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)的行为，如 Windows SDK 中所述。

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*Clr*<br/>
表示新默认背景颜色的 COLORREF 值。

### <a name="return-value"></a>返回值

表示上一个默认背景颜色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

有关何时设置背景颜色以及如何设置默认值的详细信息，请参阅本主题。

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CReBarCtrl：：设置颜色方案

设置钢筋控件上的按钮的配色方案。

```cpp
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>参数

*lpcs*<br/>
指向[COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme)结构的指针，如 Windows SDK 中所述。

### <a name="remarks"></a>备注

该`COLORSCHEME`结构包括按钮高光颜色和按钮阴影颜色。

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CReBarCtrl：：设置扩展样式

设置当前钢筋控件的扩展样式。

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwMask*|[在]标志的位组合 （OR），用于指定*dwStyleEx*参数中应用哪些标志。 使用以下一个或多个值：<br /><br /> RBS_EX_SPLITTER：默认情况下，以水平模式显示底部的拆分器，在垂直模式下向右显示拆分器。<br /><br /> RBS_EX_TRANSPARENT：将[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)消息转发到父窗口。|
|*dwStyleEx*|[在]指定要应用的样式的标志的位组合 （OR）。 要设置样式，请指定*dwMask*参数中使用的相同标志。 要重置样式，请指定二进制零。|

### <a name="return-value"></a>返回值

上一个扩展样式。

### <a name="remarks"></a>备注

此方法发送[RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle)消息，这在 Windows SDK 中介绍。

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a>CReBarCtrl：：设置图像列表

将图像列表分配给钢筋控件。

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>参数

*pImageList*<br/>
指向[CImageList](../../mfc/reference/cimagelist-class.md)对象的指针，该对象包含要分配给钢筋控件的图像列表。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

## <a name="crebarctrlsetowner"></a><a name="setowner"></a>CReBarCtrl：：SetOwner

实现 Win32 消息[RB_SETPARENT](/windows/win32/Controls/rb-setparent)的行为，如 Windows SDK 中所述。

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向`CWnd`要设置为钢筋控件所有者的对象的指针。

### <a name="return-value"></a>返回值

指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是钢筋控件的当前所有者。

### <a name="remarks"></a>备注

请注意，此成员函数使用指向`CWnd`对象的对象，用于钢筋控件的当前和选定所有者，而不是对窗口的句柄。

> [!NOTE]
> 此成员函数不会更改创建控件时设置的实际父级;而是向指定的窗口发送通知消息。

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a>CReBarCtrl：：设置调色板

实现 Win32 消息[RB_SETPALETTE](/windows/win32/Controls/rb-setpalette)的行为，如 Windows SDK 中所述。

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>参数

*hPal*<br/>
指定钢筋控件将使用的新调色板的 HPALETTE。

### <a name="return-value"></a>返回值

指向指定钢筋控件上一个调色板的[CPalette](../../mfc/reference/cpalette-class.md)对象的指针。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CPalette`对象作为其返回值，而不是 HPALETTE。

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a>CReBarCtrl：：设置文本颜色

实现 Win32 消息[RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor)的行为，如 Windows SDK 中所述。

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*Clr*<br/>
表示对象中新文本颜色的`CReBarCtrl`COLORREF 值。

### <a name="return-value"></a>返回值

[COLORREF](/windows/win32/gdi/colorref)值表示与`CReBarCtrl`对象关联的上一个文本颜色。

### <a name="remarks"></a>备注

它用于支持钢筋控件中的文本颜色灵活性。

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a>CReBarCtrl：：设置工具提示

将工具尖端控件与钢筋控件关联。

```cpp
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>参数

*pToolTip*<br/>
指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针

### <a name="remarks"></a>备注

完成对象后，`CToolTipCtrl`必须销毁该对象。

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CReBarCtrl：：设置窗口主题

设置钢筋控件的可视样式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>参数

*pssSubApp名称*<br/>
指向 Unicode 字符串的指针，其中包含要设置的钢筋可视样式。

### <a name="return-value"></a>返回值

不使用返回值。

### <a name="remarks"></a>备注

此成员函数模拟[RB_SETWINDOWTHEME](/windows/win32/Controls/rb-setwindowtheme)消息的功能，如 Windows SDK 中所述。

## <a name="crebarctrlshowband"></a><a name="showband"></a>CReBarCtrl：：显示乐队

实现 Win32 消息[的行为RB_SHOWBAND](/windows/win32/Controls/rb-showband)，如 Windows SDK 中所述。

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>参数

*乌班德*<br/>
钢筋控件中带的零基索引。

*f显示*<br/>
指示带是应显示还是隐藏。 如果此值为 TRUE，则显示波段。 否则，将隐藏该波段。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a>CreBarctrl：大小托雷

实现 Win32 消息[RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect)的行为，如 Windows SDK 中所述。

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>参数

*矩形*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的引用，该对象指定钢筋控件应调整到的矩形。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

请注意，此成员函数使用`CRect`对象作为参数，而不是`RECT`结构。

## <a name="see-also"></a>请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
