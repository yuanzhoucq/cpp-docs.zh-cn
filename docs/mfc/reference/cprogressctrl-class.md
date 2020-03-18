---
title: CProgressCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
ms.openlocfilehash: 9d63a1113e521eb73c99c47b335eb7ab00ccd753
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426863"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl 类

提供 Windows 公共进度栏控件的功能。

## <a name="syntax"></a>语法

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CProgressCtrl：： CProgressCtrl](#cprogressctrl)|构造 `CProgressCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CProgressCtrl：： Create](#create)|创建一个进度栏控件，并将其附加到 `CProgressCtrl` 的对象。|
|[CProgressCtrl：： CreateEx](#createex)|创建具有指定 Windows 扩展样式的进度控件，并将其附加到 `CProgressCtrl` 的对象。|
|[CProgressCtrl：： GetBarColor](#getbarcolor)|获取当前进度栏控件的进度指示器栏的颜色。|
|[CProgressCtrl：： GetBkColor](#getbkcolor)|获取当前进度栏的背景色。|
|[CProgressCtrl：： GetPos](#getpos)|获取进度栏的当前位置。|
|[CProgressCtrl：： GetRange](#getrange)|获取进度栏控件范围的下限和上限。|
|[CProgressCtrl：： GetState](#getstate)|获取当前进度栏控件的状态。|
|[CProgressCtrl：： GetStep](#getstep)|检索当前进度栏控件的进度栏的步长增量。|
|[CProgressCtrl：： OffsetPos](#offsetpos)|按指定增量前移进度栏控件的当前位置，并重绘该条形图以反映新位置。|
|[CProgressCtrl：： SetBarColor](#setbarcolor)|设置当前进度栏控件中的进度指示器栏的颜色。|
|[CProgressCtrl：： SetBkColor](#setbkcolor)|设置进度栏的背景色。|
|[CProgressCtrl：： SetMarquee](#setmarquee)|为当前进度栏控件打开或关闭选框模式。|
|[CProgressCtrl：： SetPos](#setpos)|设置进度栏控件的当前位置，并重绘该位置以反映新位置。|
|[CProgressCtrl：： SetRange](#setrange)|设置进度栏控件的最小和最大范围，并重绘该条形以反映新的范围。|
|[CProgressCtrl：： SetState](#setstate)|设置当前进度栏控件的状态。|
|[CProgressCtrl：： SetStep](#setstep)|指定进度栏控件的步长增量。|
|[CProgressCtrl：： StepIt](#stepit)|按步骤增量（请参阅[SetStep](#setstep)）向前移动进度栏控件的当前位置，并重绘该条形以反映新位置。|

## <a name="remarks"></a>备注

进度栏控件是一个窗口，应用程序可以使用它来指示长时间操作的进度。 它包含一个从左到右逐渐填充的矩形，在操作过程中，系统突出显示颜色。

进度栏控件具有一个范围和一个当前位置。 范围表示操作的总持续时间，当前位置表示应用程序完成操作所完成的进度。 窗口过程使用范围和当前位置确定要用突出显示颜色填充的进度栏的百分比。 因为范围和当前位置值表示为有符号整数，所以当前位置值的可能范围是从-2147483648 到2147483647（含）。

有关使用 `CProgressCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="cprogressctrl"></a>CProgressCtrl：： CProgressCtrl

构造 `CProgressCtrl` 对象。

```
CProgressCtrl();
```

### <a name="remarks"></a>备注

构造 `CProgressCtrl` 对象后，调用 `CProgressCtrl::Create` 以创建进度栏控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>CProgressCtrl：： Create

创建一个进度栏控件，并将其附加到 `CProgressCtrl` 的对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwStyle*<br/>
指定进度栏控件的样式。 除了下面的进度栏控件样式以外，还可将[Windows SDK 中的](/windows/win32/api/winuser/nf-winuser-createwindoww)所有窗口 stylesdescribed 组合应用到控件：

- PBS_VERTICAL 垂直显示进度信息，从上到下。 如果没有此标志，则进度栏控件水平显示，从左到右。

- PBS_SMOOTH 在进度栏控件中显示渐变的平滑填充。 如果没有此标志，控件将填充块。

*rect*<br/>
指定进度栏控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。 由于控件必须是子窗口，因此指定的坐标是相对于*pParentWnd*的工作区的。

*pParentWnd*<br/>
指定进度栏控件的父窗口，通常为 `CDialog`。 值不得为 NULL。

*nID*<br/>
指定进度栏控件的 ID。

### <a name="return-value"></a>返回值

如果成功创建 `CProgressCtrl` 对象，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

可以通过两个步骤构造一个 `CProgressCtrl` 对象。 首先，调用构造函数，该构造函数创建 `CProgressCtrl` 对象，然后调用 `Create`，这会创建进度栏控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>CProgressCtrl：： CreateEx

创建一个控件（子窗口）并将其与 `CProgressCtrl` 对象相关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>parameters

*dwExStyle*<br/>
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定进度栏控件的样式。 应用在[Windows SDK 中所](/windows/win32/api/winuser/nf-winuser-createwindoww)述的任何窗口样式组合。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用，该结构描述要创建的窗口的大小和位置（以*pParentWnd*的工作区坐标表示）。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用 `CreateEx` 而不是[Create](#create)来应用扩展的 windows 样式，该样式由 Windows 扩展样式指定的前言**WS_EX_** 开头。

##  <a name="getbarcolor"></a>CProgressCtrl：： GetBarColor

获取当前进度栏控件的进度指示器栏的颜色。

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>返回值

当前进度栏的颜色（表示为[COLORREF](/windows/win32/gdi/colorref)值）; 如果进度指示器栏颜色为默认颜色，则为 CLR_DEFAULT。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor)消息。

##  <a name="getbkcolor"></a>CProgressCtrl：： GetBkColor

获取当前进度栏的背景色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

当前进度栏的背景色，以[COLORREF](/windows/win32/gdi/colorref)值的形式表示。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor)消息。

##  <a name="getpos"></a>CProgressCtrl：： GetPos

检索进度栏的当前位置。

```
int GetPos();
```

### <a name="return-value"></a>返回值

进度栏控件的位置。

### <a name="remarks"></a>备注

进度栏控件的位置不是屏幕上的物理位置，而是介于[SetRange](#setrange)中指示的上限和下限之间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>CProgressCtrl：： GetRange

获取进度栏控件的当前下限或范围。

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>parameters

*nLower*<br/>
对接收进度栏控件下限的整数的引用。

*nUpper*<br/>
对接收进度栏控件上限的整数的引用。

### <a name="remarks"></a>备注

此函数将下限和上限的值复制到*nLower*和*nUpper*所引用的整数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>CProgressCtrl：： GetState

获取当前进度栏控件的状态。

```
int GetState() const;
```

### <a name="return-value"></a>返回值

当前进度栏控件的状态，它是以下值之一：

|值|状态|
|-----------|-----------|
|PBST_NORMAL|正在进行|
|PBST_ERROR|错误|
|PBST_PAUSED|已暂停|

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[PBM_GETSTATE](/windows/win32/Controls/pbm-getstate)消息。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例检索当前进度栏控件的状态。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>CProgressCtrl：： GetStep

检索当前进度栏控件的进度栏的步长增量。

```
int GetStep() const;
```

### <a name="return-value"></a>返回值

进度栏的步长增量。

### <a name="remarks"></a>备注

步长增量是对[CProgressCtrl：： StepIt](#stepit)的调用增加进度栏的当前位置时所依据的量。

此方法发送 Windows SDK 中描述的[PBM_GETSTEP](/windows/win32/Controls/pbm-getstep)消息。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例检索当前进度栏控件的步长增量。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>CProgressCtrl：： OffsetPos

将进度栏控件的当前位置前移*nPos*指定的增量，并重新绘制该条形图以反映新位置。

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>parameters

*nPos*<br/>
此位置的提升量。

### <a name="return-value"></a>返回值

进度栏控件的上一个位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>CProgressCtrl：： SetBarColor

设置当前进度栏控件中的进度指示器栏的颜色。

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*clrBar*|中指定进度指示器栏的新颜色的[COLORREF](/windows/win32/gdi/colorref)值。 指定 CLR_DEFAULT 会导致进度栏使用其默认颜色。|

### <a name="return-value"></a>返回值

进度指示器栏的上一种颜色，表示为[COLORREF](/windows/win32/gdi/colorref)值，或者，如果进度指示器栏的颜色为默认颜色，则为 CLR_DEFAULT。

### <a name="remarks"></a>备注

仅当 Windows Vista[主题](/windows/win32/Controls/visual-styles-overview)无效时，`SetBarColor` 方法才会设置进度栏颜色。

此方法发送 Windows SDK 中描述的[PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor)消息。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例将进度栏的颜色更改为红色、绿色、蓝色或默认值。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>CProgressCtrl：： SetBkColor

设置进度栏的背景色。

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>parameters

*clrNew*<br/>
指定新背景色的 COLORREF 值。 指定 CLR_DEFAULT 值以使用进度栏的默认背景色。

### <a name="return-value"></a>返回值

指示上一背景色的[COLORREF](/windows/win32/gdi/colorref)值; 如果背景色为默认颜色，则为 CLR_DEFAULT。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>CProgressCtrl：： SetMarquee

为当前进度栏控件打开或关闭选框模式。

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*fMarqueeMode*|中若要启用选框模式，则为 TRUE; 如果为 FALSE，则关闭选框模式。|
|*N 间隔*|中字幕动画更新之间的时间（以毫秒为单位）。|

### <a name="return-value"></a>返回值

此方法始终返回 TRUE。

### <a name="remarks"></a>备注

当选框模式处于开启状态时，进度栏会进行动画处理，并像在电影院天棚上一样滚动。

此方法发送 Windows SDK 中描述的[PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee)消息。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例启动和停止字幕滚动动画。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>CProgressCtrl：： SetPos

设置*nPos*指定的进度栏控件的当前位置，并重绘该条形以反映新位置。

```
int SetPos(int nPos);
```

### <a name="parameters"></a>parameters

*nPos*<br/>
进度栏控件的新位置。

### <a name="return-value"></a>返回值

进度栏控件的上一个位置。

### <a name="remarks"></a>备注

进度栏控件的位置不是屏幕上的物理位置，而是介于[SetRange](#setrange)中指示的上限和下限之间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>CProgressCtrl：： SetRange

设置进度栏控件范围的上限和下限，并重绘该条形以反映新的范围。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>parameters

*nLower*<br/>
指定范围的下限（默认值为零）。

*nUpper*<br/>
指定范围的上限（默认值为100）。

### <a name="remarks"></a>备注

成员函数 `SetRange32` 为进度控件设置32位范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>CProgressCtrl：： SetState

设置当前进度栏控件的状态。

```
int SetState(int iState);
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*iState*|中要设置进度栏的状态。 使用以下值之一：<br /><br /> -PBST_NORMAL-正在进行<br />-PBST_ERROR-错误<br />-PBST_PAUSED-已暂停|

### <a name="return-value"></a>返回值

当前进度栏控件的前一个状态。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[PBM_SETSTATE](/windows/win32/Controls/pbm-setstate)消息。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例将当前进度栏控件的状态设置为“已暂停”或“正在进行中”。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>CProgressCtrl：： SetStep

指定进度栏控件的步长增量。

```
int SetStep(int nStep);
```

### <a name="parameters"></a>parameters

*nStep*<br/>
新步骤增量。

### <a name="return-value"></a>返回值

上一步增量。

### <a name="remarks"></a>备注

步长增量是对 `CProgressCtrl::StepIt` 的调用增加进度栏的当前位置的量。

默认步骤增量为10。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>CProgressCtrl：： StepIt

通过步长增量，向前移动进度栏控件的当前位置，并重绘该条形以反映新位置。

```
int StepIt();
```

### <a name="return-value"></a>返回值

进度栏控件的上一个位置。

### <a name="remarks"></a>备注

步骤增量由 `CProgressCtrl::SetStep` 成员函数设置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
