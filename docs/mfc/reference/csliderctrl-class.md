---
title: CSliderCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 8fffdfc002b25fdcd72dcbbf53e7e6c321f55296
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502520"
---
# <a name="csliderctrl-class"></a>CSliderCtrl 类

提供 Windows 公共滑块控件的功能。

## <a name="syntax"></a>语法

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|构造 `CSliderCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|清除滑块控件中的当前选定内容。|
|[CSliderCtrl::ClearTics](#cleartics)|删除滑块控件中的当前刻度线。|
|[CSliderCtrl::Create](#create)|创建滑块控件，并将其附加到`CSliderCtrl`对象。|
|[CSliderCtrl::CreateEx](#createex)|创建具有指定 Windows 扩展样式的滑块控件，并将其附加到`CSliderCtrl`对象。|
|[CSliderCtrl::GetBuddy](#getbuddy)|检索位于给定位置的滑块控件合作者窗口的句柄。|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|检索滑块控件通道的大小。|
|[CSliderCtrl::GetLineSize](#getlinesize)|检索滑块控件的线条大小。|
|[CSliderCtrl::GetNumTics](#getnumtics)|检索滑块控件中的刻度线数。|
|[CSliderCtrl::GetPageSize](#getpagesize)|检索滑块控件的页面大小。|
|[CSliderCtrl::GetPos](#getpos)|检索滑块的当前位置。|
|[CSliderCtrl::GetRange](#getrange)|检索滑块的最小和最大位置。|
|[CSliderCtrl::GetRangeMax](#getrangemax)|检索滑块的最大位置。|
|[CSliderCtrl::GetRangeMin](#getrangemin)|检索滑块的最小位置。|
|[CSliderCtrl::GetSelection](#getselection)|检索当前选定内容的范围。|
|[CSliderCtrl::GetThumbLength](#getthumblength)|检索当前跟踪条控件中滑块的长度。|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|检索滑块控件的滚动块的大小。|
|[CSliderCtrl::GetTic](#gettic)|检索指定刻度线的位置。|
|[CSliderCtrl::GetTicArray](#getticarray)|检索滑块控件的刻度线位置的数组。|
|[CSliderCtrl::GetTicPos](#getticpos)|检索指定刻度线的位置（以工作区坐标表示）。|
|[CSliderCtrl::GetToolTips](#gettooltips)|检索分配给滑块控件的 tooltip 控件的句柄（如果有）。|
|[CSliderCtrl::SetBuddy](#setbuddy)|将窗口分配为滑块控件的合作者窗口。|
|[CSliderCtrl::SetLineSize](#setlinesize)|设置滑块控件的线条大小。|
|[CSliderCtrl::SetPageSize](#setpagesize)|设置滑块控件的页面大小。|
|[CSliderCtrl::SetPos](#setpos)|设置滑块的当前位置。|
|[CSliderCtrl::SetRange](#setrange)|设置滑块的最小和最大位置。|
|[CSliderCtrl::SetRangeMax](#setrangemax)|设置滑块的最大位置。|
|[CSliderCtrl::SetRangeMin](#setrangemin)|设置滑块的最小位置。|
|[CSliderCtrl::SetSelection](#setselection)|设置当前选定内容的范围。|
|[CSliderCtrl::SetThumbLength](#setthumblength)|设置当前 "跟踪条" 控件中滑块的长度。|
|[CSliderCtrl::SetTic](#settic)|设置指定刻度线的位置。|
|[CSliderCtrl::SetTicFreq](#setticfreq)|设置每个滑块控件增量的刻度线的频率。|
|[CSliderCtrl::SetTipSide](#settipside)|定位跟踪条控件使用的工具提示控件。|
|[CSliderCtrl::SetToolTips](#settooltips)|向滑块控件分配 tooltip 控件。|

## <a name="remarks"></a>备注

"滑块控件" （也称为 "跟踪条"）是包含滑块和可选刻度线的窗口。 当用户使用鼠标或方向键移动滑块时，控件将发送通知消息以指示更改。

当您希望用户选择一个离散值或位于一个范围中的一组连续值时，滑动控件很有用。 例如，您可能使用滑块控件允许用户通过将滑块移动到给定刻度线来设置重复速率。

此控件（因而`CSliderCtrl`类）仅适用于在 windows 95/98 和 windows NT 版本3.51 及更高版本下运行的程序。

当创建滑块时，滑块会按指定的增量移动。 例如，如果指定滑块的范围应为五，则滑块只能占据六个位置：滑块控件左侧的位置和范围中每个增量的一个位置。 通常，这些位置中的每个位置将用一个刻度线标识。

您可以使用构造函数和`Create`的成员`CSliderCtrl`函数创建滑块。 创建滑块控件后，可以使用中的`CSliderCtrl`成员函数来更改它的许多属性。 可进行的更改包括设置滑块的最小和最大位置、绘制刻度线、设置选择范围以及重新定位滑块。

有关使用`CSliderCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="clearsel"></a>CSliderCtrl：： ClearSel

清除滑块控件中的当前选定内容。

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*bRedraw*<br/>
重绘标志。 如果此参数为 TRUE，则在清除选中内容后重绘滑块;否则，不会重新绘制滑块。

##  <a name="cleartics"></a>  CSliderCtrl::ClearTics

删除滑块控件中的当前刻度线。

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*bRedraw*<br/>
重绘标志。 如果此参数为 TRUE，则在清除刻度线后重绘滑块;否则，不会重新绘制滑块。

##  <a name="create"></a>CSliderCtrl：： Create

创建滑块控件，并将其附加到`CSliderCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定滑块控件的样式。 将 Windows SDK 中所述的[滑块控件样式](/windows/win32/Controls/trackbar-control-styles)的任意组合应用于控件。

*rect*<br/>
指定滑块控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pParentWnd*<br/>
指定滑块控件的父窗口，通常为`CDialog`。 它不能为 NULL。

*nID*<br/>
指定滑块控件的 ID。

### <a name="return-value"></a>返回值

如果初始化成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

可以通过`CSliderCtrl`两个步骤构造。 首先，调用构造函数，然后调用`Create`，它会创建滑块控件，并将其附加`CSliderCtrl`到对象。

根据为*dwStyle*设置的值，滑块控件可以具有垂直或水平方向。 它可以在两侧和两侧都有刻度线，或者两者都不存在。 它还可用于指定连续值的范围。

若要将扩展窗口样式应用于滑块控件， 请调用 [CreateEx](#createex) 而不是`Create`。

##  <a name="createex"></a>CSliderCtrl：： CreateEx

创建一个控件（子窗口）并将`CSliderCtrl`其与对象关联。

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
指定滑块控件的样式。 将 Windows SDK 中所述的[滑块控件样式](/windows/win32/Controls/trackbar-control-styles)的任意组合应用于控件。

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

##  <a name="csliderctrl"></a>CSliderCtrl：： CSliderCtrl

构造 `CSliderCtrl` 对象。

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>CSliderCtrl：： GetBuddy

检索位于给定位置的滑块控件合作者窗口的句柄。

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>参数

*fLocation*<br/>
一个布尔值，指示要检索的两个合作者窗口句柄中的哪一个。 可以是以下值之一：

- 如果为 TRUE，则检索滑块左侧的合作者的句柄。 如果滑块控件使用 TBS_VERT 样式，则该消息将检索滑块上方的合作者。

- 如果为 FALSE，则检索滑块右侧的合作者的句柄。 如果滑块控件使用 TBS_VERT 样式，则该消息将检索滑块下面的合作者。

### <a name="return-value"></a>返回值

指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是*fLocation*指定的位置处的合作者窗口; 如果该位置不存在合作者窗口，则为 NULL。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)的行为，如 Windows SDK 中所述。 有关 slider 控件样式的说明，请参阅 Windows SDK 中的[跟踪条控件样式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="getchannelrect"></a>CSliderCtrl：： GetChannelRect

检索滑块控件通道的边框的大小和位置。

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>参数

*lprc*<br/>
指向[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针，该对象包含当函数返回时通道边框的大小和位置。

### <a name="remarks"></a>备注

通道是滑块移动的区域，在选择范围时包含突出显示的区域。

##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize

检索滑块控件的线条大小。

```
int GetLineSize() const;
```

### <a name="return-value"></a>返回值

滑块控件的线条大小。

### <a name="remarks"></a>备注

行大小会影响 TB_LINEUP 和 TB_LINEDOWN 通知的滑块移动量。 行大小的默认设置为1。

##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics

检索滑块控件中的刻度线数。

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>返回值

滑块控件中的刻度线数。

##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize

检索滑块控件的页面大小。

```
int GetPageSize() const;
```

### <a name="return-value"></a>返回值

滑块控件的页面大小。

### <a name="remarks"></a>备注

页面大小会影响 TB_PAGEUP 和 TB_PAGEDOWN 通知的滑块移动量。

##  <a name="getpos"></a>CSliderCtrl：： GetPos

检索滑块控件中滑块的当前位置。

```
int GetPos() const;
```

### <a name="return-value"></a>返回值

当前位置。

##  <a name="getrange"></a>CSliderCtrl：： GetRange

检索滑块控件中滑块的最大和最小位置。

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>参数

*nMin*<br/>
对接收最小位置的整数的引用。

*nMax*<br/>
对接收最大位置的整数的引用。

### <a name="remarks"></a>备注

此函数将值复制到*nMin*和*n 每天*所引用的整数。

##  <a name="getrangemax"></a>CSliderCtrl：： GetRangeMax

检索滑块控件中滑块的最大位置。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>返回值

控件的最大位置。

##  <a name="getrangemin"></a>CSliderCtrl：： GetRangeMin

检索滑块控件中滑块的最小位置。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>返回值

控件的最小位置。

##  <a name="getselection"></a>CSliderCtrl：： GetSelection

检索滑块控件中当前所选内容的起始位置和结束位置。

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>参数

*nMin*<br/>
引用一个整数，该整数接收当前所选内容的起始位置。

*nMax*<br/>
引用一个整数，该整数接收当前所选内容的结束位置。

##  <a name="getthumblength"></a>CSliderCtrl：： GetThumbLength

检索当前跟踪条控件中滑块的长度。

```
int GetThumbLength() const;
```

### <a name="return-value"></a>返回值

滑块的长度（以像素为单位）。

### <a name="remarks"></a>备注

此方法发送[TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength)消息，如 Windows SDK 中所述。

##  <a name="getthumbrect"></a>CSliderCtrl：： GetThumbRect

检索滑块控件中滑块（滚动块）的边框的大小和位置。

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>参数

*lprc*<br/>
指向`CRect`对象的指针，该对象包含滑块在函数返回时的边框。

##  <a name="gettic"></a>CSliderCtrl：： GetTic

检索滑块控件中刻度线的位置。

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>参数

*nTic*<br/>
标识刻度线的从零开始的索引。

### <a name="return-value"></a>返回值

指定刻度线的位置; 如果*nTic*未指定有效的索引，则为-1。

##  <a name="getticarray"></a>CSliderCtrl：： GetTicArray

检索数组的地址，该数组包含滑块控件的刻度线的位置。

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>返回值

包含滑块控件的刻度线位置的数组的地址。

##  <a name="getticpos"></a>CSliderCtrl：： GetTicPos

检索滑块控件中刻度线的当前物理位置。

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>参数

*nTic*<br/>
标识刻度线的从零开始的索引。

### <a name="return-value"></a>返回值

指定刻度线的物理位置（以工作区坐标表示），如果*nTic*未指定有效的索引，则为-1。

##  <a name="gettooltips"></a>CSliderCtrl：： GetToolTips

检索分配给滑块控件的 tooltip 控件的句柄（如果有）。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>返回值

指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针; 如果不使用工具提示，则为 NULL。 如果滑块控件不使用 TBS_TOOLTIPS 样式，则返回值为 NULL。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)的行为，如 Windows SDK 中所述。 请注意，此成员函数将`CToolTipCtrl`返回一个对象，而不是控件的句柄。

有关 slider 控件样式的说明，请参阅 Windows SDK 中的[跟踪条控件样式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="setbuddy"></a>CSliderCtrl：： SetBuddy

将窗口分配为滑块控件的合作者窗口。

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>参数

*pWndBuddy*<br/>
指向`CWnd`对象的指针，该对象将被设置为滑块控件的合作者。

*fLocation*<br/>
指定显示合作者窗口的位置的值。 此值可以是下列值之一：

- 如果 "跟踪条" 控件使用 TBS_HORZ 样式，则合作者将显示在跟踪条的左侧。 如果跟踪条使用 TBS_VERT 样式，则合作者会出现在 "跟踪条" 控件的上方。

- FALSE 如果 "跟踪条" 控件使用 TBS_HORZ 样式，则合作者将显示在跟踪条的右侧。 如果跟踪条使用 TBS_VERT 样式，则合作者会出现在 "跟踪条" 控件下面。

### <a name="return-value"></a>返回值

指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象先前已分配给该位置的滑块控件。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)的行为，如 Windows SDK 中所述。 请注意，此成员函数使用指向`CWnd`对象的指针，而不是其返回值和参数的窗口句柄。

有关 slider 控件样式的说明，请参阅 Windows SDK 中的[跟踪条控件样式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize

设置滑块控件的线条大小。

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>参数

*nSize*<br/>
滑块控件的新行大小。

### <a name="return-value"></a>返回值

以前的行大小。

### <a name="remarks"></a>备注

行大小会影响 TB_LINEUP 和 TB_LINEDOWN 通知的滑块移动量。

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

设置滑块控件的页面大小。

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>参数

*nSize*<br/>
滑块控件的新页面大小。

### <a name="return-value"></a>返回值

上一页大小。

### <a name="remarks"></a>备注

页面大小会影响 TB_PAGEUP 和 TB_PAGEDOWN 通知的滑块移动量。

##  <a name="setpos"></a>CSliderCtrl：： SetPos

设置滑块控件中滑块的当前位置。

```
void SetPos(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定新的滑块位置。

##  <a name="setrange"></a>CSliderCtrl：： SetRange

为滑块控件中的滑块设置范围（最小和最大位置）。

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*nMin*<br/>
滑块的最小位置。

*nMax*<br/>
滑块的最大位置。

*bRedraw*<br/>
重绘标志。 如果此参数为 TRUE，则在设置范围后重绘滑块;否则，不会重新绘制滑块。

##  <a name="setrangemax"></a>CSliderCtrl：： SetRangeMax

为滑块控件中的滑块设置最大范围。

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*nMax*<br/>
滑块的最大位置。

*bRedraw*<br/>
重绘标志。 如果此参数为 TRUE，则在设置范围后重绘滑块;否则，不会重新绘制滑块。

##  <a name="setrangemin"></a>CSliderCtrl：： SetRangeMin

设置滑块控件中滑块的最小范围。

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*nMin*<br/>
滑块的最小位置。

*bRedraw*<br/>
重绘标志。 如果此参数为 TRUE，则在设置范围后重绘滑块;否则，不会重新绘制滑块。

##  <a name="setselection"></a>CSliderCtrl：： SetSelection

设置滑块控件中当前所选内容的起始位置和结束位置。

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>参数

*nMin*<br/>
滑块的起始位置。

*nMax*<br/>
滑块的结束位置。

##  <a name="setthumblength"></a>CSliderCtrl：： SetThumbLength

设置当前 "跟踪条" 控件中滑块的长度。

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*nLength*|中滑块的长度（以像素为单位）。|

### <a name="remarks"></a>备注

此方法要求将跟踪条控件设置为[TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles)样式。

此方法发送[TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength)消息，如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义用于访问当前`m_sliderCtrl`跟踪条控件的变量。 该示例还定义一个变量， `thumbLength`该变量用于存储跟踪条控件的 thumb 组件的默认长度。 下面的示例中使用了这些变量。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例将跟踪条控件的 thumb 组件设置为其默认长度的两倍。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>  CSliderCtrl::SetTic

设置滑块控件中刻度线的位置。

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>参数

*nTic*<br/>
刻度线的位置。 此参数必须指定一个正值。

### <a name="return-value"></a>返回值

如果设置了刻度线，则为非零值;否则为0。

##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq

设置在滑块中显示刻度线的频率。

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>参数

*nFreq*<br/>
刻度线的频率。

### <a name="remarks"></a>备注

例如，如果将 "频率" 设置为2，则会为滑块范围内的每个其他增量显示一个刻度线。 频率的默认设置为1（也就是说，范围中的每个增量都与刻度线相关联）。

必须使用 TBS_AUTOTICKS 样式创建控件才能使用此函数。 有关详细信息，请参阅[CSliderCtrl：： Create](#create)。

##  <a name="settipside"></a>CSliderCtrl：： SetTipSide

定位跟踪条控件使用的工具提示控件。

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>参数

*nLocation*<br/>
表示显示 tooltip 控件的位置的值。 有关可能值的列表，请参阅 Win32 消息[TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside)，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

一个值，该值表示 tooltip 控件的上一个位置。 返回值等于*n 位置*的可能值之一。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息 TBM_SETTIPSIDE 的行为，如 Windows SDK 中所述。 使用 TBS_TOOLTIPS 样式的滑块控件显示工具提示。 有关 slider 控件样式的说明，请参阅 Windows SDK 中的[跟踪条控件样式](/windows/win32/Controls/trackbar-control-styles)。

##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips

向滑块控件分配 tooltip 控件。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>参数

*pWndTip*<br/>
指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针，该对象包含用于滑块控件的工具提示。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)的行为，如 Windows SDK 中所述。 当使用 TBS_TOOLTIPS 样式创建滑块控件时，它会创建一个默认工具提示控件，该控件显示在滑块旁边，并显示滑块的当前位置。 有关 slider 控件样式的说明，请参阅 Windows SDK 中的[跟踪条控件样式](/windows/win32/Controls/trackbar-control-styles)。

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl 类](../../mfc/reference/cprogressctrl-class.md)
