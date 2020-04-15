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
ms.openlocfilehash: 24e1cb18f979d1144f15cf6ffedc6cace5f5361e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318216"
---
# <a name="csliderctrl-class"></a>CSliderCtrl 类

提供 Windows 公共滑块控件的功能。

## <a name="syntax"></a>语法

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSliderCtrl：：CSliderCtrl](#csliderctrl)|构造 `CSliderCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSliderCtrl：：清除塞尔](#clearsel)|清除滑块控件中的当前选择。|
|[CSliderCtrl：：清除](#cleartics)|从滑块控件中删除当前刻度线。|
|[CSliderCtrl：：创建](#create)|创建滑块控件并将其附加到`CSliderCtrl`对象。|
|[CSliderCtrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建滑块控件并将其附加到`CSliderCtrl`对象。|
|[CSliderCtrl：GetBuddy](#getbuddy)|将句柄检索到给定位置的滑块控件伙伴窗口。|
|[CSliderCtrl：：获取通道Rect](#getchannelrect)|检索滑块控件通道的大小。|
|[CSliderCtrl：：获取线尺寸](#getlinesize)|检索滑块控件的行大小。|
|[CSliderCtrl：getNumTics](#getnumtics)|检索滑块控件中的刻度线数。|
|[CSliderCtrl：：获取页面大小](#getpagesize)|检索滑块控件的页面大小。|
|[CSliderCtrl：GetPos](#getpos)|检索滑块的当前位置。|
|[CSliderCtrl：获取范围](#getrange)|检索滑块的最小和最大位置。|
|[CSliderCtrl：：获取山脉最大值](#getrangemax)|检索滑块的最大位置。|
|[CSliderCtrl：：获取兰格明](#getrangemin)|检索滑块的最小位置。|
|[CSliderCtrl：获取选择](#getselection)|检索当前选择的范围。|
|[CSliderCtrl：：获取拇指长度](#getthumblength)|检索当前轨道栏控件中的滑块长度。|
|[CSliderCtrl：：获取Thumbrect](#getthumbrect)|检索滑块控件的拇指的大小。|
|[CSliderCtrl：GetTic](#gettic)|检索指定刻度线的位置。|
|[CSliderCtrl：：获取蒂卡雷](#getticarray)|检索滑块控件的刻度线位置数组。|
|[CSliderCtrl：：获取蒂波](#getticpos)|在客户端坐标中检索指定刻度线的位置。|
|[CSliderCtrl：获取工具提示](#gettooltips)|检索分配给滑块控件的工具提示控件的句柄（如果有）。|
|[CSliderCtrl：：SetBuddy](#setbuddy)|将窗口指定为滑块控件的好友窗口。|
|[CSliderCtrl：：设置线大小](#setlinesize)|设置滑块控件的线大小。|
|[CSliderCtrl：：设置页面大小](#setpagesize)|设置滑块控件的页面大小。|
|[CSliderCtrl：：SetPos](#setpos)|设置滑块的当前位置。|
|[CSliderCtrl：：设置范围](#setrange)|设置滑块的最小和最大位置。|
|[CSliderCtrl：：SetRangeMax](#setrangemax)|设置滑块的最大位置。|
|[CSliderCtrl：：SetRangeMin](#setrangemin)|设置滑块的最小位置。|
|[CSliderCtrl：：设置选择](#setselection)|设置当前选择的范围。|
|[CSliderCtrl：：设置拇指长度](#setthumblength)|设置当前轨道栏控件中的滑块长度。|
|[CSliderCtrl：：SetTic](#settic)|设置指定刻度线的位置。|
|[CSliderCtrl：：SetTicFreq](#setticfreq)|设置每个滑块控件增量的刻度标记频率。|
|[CSliderCtrl：：SetTipside](#settipside)|定位轨道杆控件使用的工具提示控件。|
|[CSliderCtrl：：设置工具提示](#settooltips)|将工具提示控件分配给滑块控件。|

## <a name="remarks"></a>备注

"滑块控件"（也称为轨道栏）是包含滑块和可选刻度线的窗口。 当用户使用鼠标或方向键移动滑块时，控件会发送通知消息以指示更改。

当您希望用户选择一个离散值或位于一个范围中的一组连续值时，滑动控件很有用。 例如，您可能使用滑块控件允许用户通过将滑块移动到给定刻度线来设置重复速率。

此控件（因此该`CSliderCtrl`类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

滑块以创建滑块时指定的增量移动。 例如，如果指定滑块应具有 5 个范围，则滑块只能占据六个位置：滑块控件左侧的位置和范围中每个增量的一个位置。 通常，这些位置中的每个位置将用一个刻度线标识。

通过使用 构造函数和`Create``CSliderCtrl`的成员函数创建滑块。 创建滑块控件后，可以使用 中`CSliderCtrl`的成员函数来更改其许多属性。 可进行的更改包括设置滑块的最小和最大位置、绘制刻度线、设置选择范围以及重新定位滑块。

有关 使用`CSliderCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl：：清除塞尔

清除滑块控件中的当前选择。

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*bredraw*<br/>
重绘标志。 如果此参数为 TRUE，则在清除所选内容后重绘滑块;如果此参数为 TRUE，则在清除所选内容后重新绘制滑块。否则，不会重绘滑块。

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl：：清除

从滑块控件中删除当前刻度线。

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*bredraw*<br/>
重绘标志。 如果此参数为 TRUE，则在清除刻度线后重绘滑块;如果此参数为 TRUE，则在清除刻度线后重新绘制滑块。否则，不会重绘滑块。

## <a name="csliderctrlcreate"></a><a name="create"></a>CSliderCtrl：：创建

创建滑块控件并将其附加到`CSliderCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定滑块控件的样式。 将 Windows SDK 中描述的[滑块控件样式](/windows/win32/Controls/trackbar-control-styles)的任意组合应用于控件。

*矩形*<br/>
指定滑块控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pparentwnd*<br/>
指定滑块控件的父窗口（通常为`CDialog`。 值不得为 NULL。

*nID*<br/>
指定滑块控件的 ID。

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

在两个步骤`CSliderCtrl`中构造 一个。 首先调用构造函数，然后调用`Create`，这将创建滑块控件并将其附加到`CSliderCtrl`对象。

根据为*dwStyle*设置的值，滑块控件可以具有垂直或水平方向。 它可以有两侧，双方，或两者没有刻度线。 它还可用于指定连续值的范围。

要将扩展窗口样式应用于滑块控件，请调用[CreateEx](#createex) `Create`而不是 。

## <a name="csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl：：创建Ex

创建控件（子窗口），并将其与`CSliderCtrl`对象关联。

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
指定滑块控件的样式。 将 Windows SDK 中描述的[滑块控件样式](/windows/win32/Controls/trackbar-control-styles)的任意组合应用于控件。

*矩形*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式，该样式由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl：：CSliderCtrl

构造 `CSliderCtrl` 对象。

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl：GetBuddy

将句柄检索到给定位置的滑块控件伙伴窗口。

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>参数

*fLocation*<br/>
一个布尔值，指示要检索的两个好友窗口句柄之一。 可以是以下值之一：

- TRUE 检索滑块左侧好友的句柄。 如果滑块控件使用TBS_VERT样式，则消息将在滑块上方检索好友。

- FALSE 检索滑块右侧好友的句柄。 如果滑块控件使用TBS_VERT样式，则消息将检索滑块下方的好友。

### <a name="return-value"></a>返回值

指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象位于*fLocation*指定的位置的好友窗口，如果该位置不存在好友窗口，则指向 NULL。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy)的行为，如 Windows SDK 中所述。 有关滑块控件样式的说明，请参阅 Windows SDK 中的["跟踪栏控件样式](/windows/win32/Controls/trackbar-control-styles)"。

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl：：获取通道Rect

检索滑块控件通道的边界矩形的大小和位置。

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>参数

*利赫浦*<br/>
指向[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的指针，该对象在函数返回时包含通道边界矩形的大小和位置。

### <a name="remarks"></a>备注

通道是滑块移动的区域，在选择范围时包含高光。

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl：：获取线尺寸

检索滑块控件的行大小。

```
int GetLineSize() const;
```

### <a name="return-value"></a>返回值

滑块控件的线条大小。

### <a name="remarks"></a>备注

行大小会影响滑块为TB_LINEUP和TB_LINEDOWN通知移动的幅度。 行大小的默认设置为 1。

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl：getNumTics

检索滑块控件中的刻度线数。

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>返回值

滑块控件中的刻度线数。

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl：：获取页面大小

检索滑块控件的页面大小。

```
int GetPageSize() const;
```

### <a name="return-value"></a>返回值

滑块控件的页面大小。

### <a name="remarks"></a>备注

页面大小会影响滑块为TB_PAGEUP移动和TB_PAGEDOWN通知的移动量。

## <a name="csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl：GetPos

检索滑块控件中的滑块的当前位置。

```
int GetPos() const;
```

### <a name="return-value"></a>返回值

当前位置。

## <a name="csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl：获取范围

检索滑块控件中滑块的最大和最小位置。

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>参数

*nMin*<br/>
引用接收最小位置的整数。

*nMax*<br/>
对接收最大位置的整数的引用。

### <a name="remarks"></a>备注

此函数将值复制到*nMin*和*nMax*引用的整数中。

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl：：获取山脉最大值

检索滑块控件中滑块的最大位置。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>返回值

控件的最大位置。

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl：：获取兰格明

检索滑块控件中的滑块的最小位置。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>返回值

控件的最小位置。

## <a name="csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl：获取选择

在滑块控件中检索当前选择的起始位置和结束位置。

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>参数

*nMin*<br/>
引用接收当前选择的起始位置的整数。

*nMax*<br/>
引用接收当前所选内容的结束位置的整数。

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl：：获取拇指长度

检索当前轨道栏控件中的滑块长度。

```
int GetThumbLength() const;
```

### <a name="return-value"></a>返回值

滑块的长度（以像素为单位）。

### <a name="remarks"></a>备注

此方法发送[TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength)消息，这在 Windows SDK 中介绍。

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl：：获取Thumbrect

检索滑块（拇指）滑块（拇指）在滑块控件中的边界矩形的大小和位置。

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>参数

*利赫浦*<br/>
当函数返回时`CRect`，指向包含滑块边界矩形的对象的指针。

## <a name="csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl：GetTic

检索滑块控件中刻度线的位置。

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>参数

*nTic*<br/>
识别刻度线的零基索引。

### <a name="return-value"></a>返回值

指定的刻度线或 - 1 的位置（如果*nTic*未指定有效的索引）。

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl：：获取蒂卡雷

检索包含滑块控件的刻度线位置的数组的地址。

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>返回值

包含滑块控件的刻度线位置的数组的地址。

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl：：获取蒂波

检索滑块控件中刻度线当前的物理位置。

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>参数

*nTic*<br/>
识别刻度线的零基索引。

### <a name="return-value"></a>返回值

在客户端坐标中，如果*nTic*未指定有效的索引，则指定刻度线或 - 1 的物理位置。

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl：获取工具提示

检索分配给滑块控件的工具提示控件的句柄（如果有）。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>返回值

指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针，如果工具提示未使用，则为 NULL。 如果滑块控件不使用TBS_TOOLTIPS样式，则返回值为 NULL。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips)的行为，如 Windows SDK 中所述。 请注意，此成员函数将`CToolTipCtrl`对象而不是句柄返回到控件。

有关滑块控件样式的说明，请参阅 Windows SDK 中的["跟踪栏控件样式](/windows/win32/Controls/trackbar-control-styles)"。

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl：：SetBuddy

将窗口指定为滑块控件的好友窗口。

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>参数

*普恩德布迪*<br/>
指向对象的`CWnd`指针，该指针将设置为滑块控件的好友。

*fLocation*<br/>
指定显示好友窗口的位置的值。 此值可以为下列值之一：

- 如果轨道栏控件使用TBS_HORZ样式，好友将显示在轨道栏的左侧。 如果轨道栏使用TBS_VERT样式，好友将显示在轨道栏控件的上方。

- 如果轨道栏控件使用TBS_HORZ样式，好友将显示在轨道栏的右侧。 如果轨道栏使用TBS_VERT样式，好友将显示在轨道栏控件下方。

### <a name="return-value"></a>返回值

指向以前分配给该位置的滑块控件的[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)，如 Windows SDK 中所述。 请注意，此成员函数使用指向`CWnd`对象的指针，而不是对其返回值和参数的窗口句柄。

有关滑块控件样式的说明，请参阅 Windows SDK 中的["跟踪栏控件样式](/windows/win32/Controls/trackbar-control-styles)"。

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl：：设置线大小

设置滑块控件的线条大小。

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>参数

*nSize*<br/>
滑块控件的新线大小。

### <a name="return-value"></a>返回值

上一行大小。

### <a name="remarks"></a>备注

行大小会影响滑块为TB_LINEUP和TB_LINEDOWN通知移动的幅度。

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl：：设置页面大小

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

页面大小会影响滑块为TB_PAGEUP移动和TB_PAGEDOWN通知的移动量。

## <a name="csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl：：SetPos

设置滑块控件中的滑块的当前位置。

```
void SetPos(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
指定新的滑块位置。

## <a name="csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl：：设置范围

设置滑块控件中滑块的范围（最小位置和最大位置）。

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

*bredraw*<br/>
重绘标志。 如果此参数为 TRUE，则在设置范围后重绘滑块;如果此参数为 TRUE，则在设置范围后重新绘制滑块。否则，不会重绘滑块。

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl：：SetRangeMax

设置滑块控件中滑块的最大范围。

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*nMax*<br/>
滑块的最大位置。

*bredraw*<br/>
重绘标志。 如果此参数为 TRUE，则在设置范围后重绘滑块;如果此参数为 TRUE，则在设置范围后重新绘制滑块。否则，不会重绘滑块。

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl：：SetRangeMin

设置滑块控件中的滑块的最小范围。

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>参数

*nMin*<br/>
滑块的最小位置。

*bredraw*<br/>
重绘标志。 如果此参数为 TRUE，则在设置范围后重绘滑块;如果此参数为 TRUE，则在设置范围后重新绘制滑块。否则，不会重绘滑块。

## <a name="csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl：：设置选择

在滑块控件中设置当前选择的起始位置和结束位置。

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

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl：：设置拇指长度

设置当前轨道栏控件中的滑块长度。

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*n 长度*|[在]滑块的长度（以像素为单位）。|

### <a name="remarks"></a>备注

此方法要求将轨道栏控件设置为[TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles)样式。

此方法发送[TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于访问当前跟踪栏`m_sliderCtrl`控件的变量 。 该示例还定义了一个变量`thumbLength`，用于存储轨道栏控件的拇指组件的默认长度。 这些变量在下一个示例中使用。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>示例

以下代码示例将轨道栏控件的拇指组件设置为其默认长度的两倍。

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl：：SetTic

设置滑块控件中刻度线的位置。

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>参数

*nTic*<br/>
刻度线的位置。 此参数必须指定正值。

### <a name="return-value"></a>返回值

设置刻度线时非零;否则 0。

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl：：SetTicFreq

设置在滑块中显示刻度线的频率。

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>参数

*恩弗雷克*<br/>
刻度线的频率。

### <a name="remarks"></a>备注

例如，如果频率设置为 2，则滑块范围内的其他增量将显示一个刻度线。 频率的默认设置为 1（即，范围中的每个增量都与刻度线相关联）。

您必须使用TBS_AUTOTICKS样式创建控件才能使用此函数。 有关详细信息，请参阅[CSliderCtrl：：创建](#create)。

## <a name="csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl：：SetTipside

定位轨道杆控件使用的工具提示控件。

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>参数

*n位置*<br/>
表示要显示工具提示控件的位置的值。 有关可能值的列表，请参阅 win32 消息[TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside)，如 Windows SDK 中所述。

### <a name="return-value"></a>返回值

表示工具提示控件的上一位置的值。 返回值等于*nLocation*的可能值之一。

### <a name="remarks"></a>备注

此成员函数实现 win32 消息TBM_SETTIPSIDE的行为，如 Windows SDK 中所述。 使用TBS_TOOLTIPS样式显示工具提示的滑块控件。 有关滑块控件样式的说明，请参阅 Windows SDK 中的["跟踪栏控件样式](/windows/win32/Controls/trackbar-control-styles)"。

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl：：设置工具提示

将工具提示控件分配给滑块控件。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>参数

*pwndTip*<br/>
指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象的指针，其中包含要与滑块控件一起使用的工具提示。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips)的行为，如 Windows SDK 中所述。 使用TBS_TOOLTIPS样式创建滑块控件时，它会创建显示在滑块旁边的默认工具提示控件，显示滑块的当前位置。 有关滑块控件样式的说明，请参阅 Windows SDK 中的["跟踪栏控件样式](/windows/win32/Controls/trackbar-control-styles)"。

## <a name="see-also"></a>另请参阅

[MFC 样品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl 类](../../mfc/reference/cprogressctrl-class.md)
