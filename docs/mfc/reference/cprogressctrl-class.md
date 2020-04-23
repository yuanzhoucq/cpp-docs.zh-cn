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
ms.openlocfilehash: c9e94e334318b32efcf8c9de681a78349ab12151
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751133"
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
|[CProgressCtrl：：CProgressCtrl](#cprogressctrl)|构造 `CProgressCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CProgressCtrl：：创建](#create)|创建进度条控件并将其附加到`CProgressCtrl`对象。|
|[CProgressCtrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建进度控件，并将其附加到`CProgressCtrl`对象。|
|[CProgressCtrl：：获取巴彩](#getbarcolor)|获取当前进度条控件的进度指示器栏的颜色。|
|[CProgressCtrl：：GetBkColor](#getbkcolor)|获取当前进度栏的背景颜色。|
|[CProgressCtrl：：获取Pos](#getpos)|获取进度条的当前位置。|
|[CProgressCtrl：获取范围](#getrange)|获取进度条控制范围的下限和上限。|
|[CProgressCtrl：：获取状态](#getstate)|获取当前进度条控件的状态。|
|[CProgressCtrl：获取步骤](#getstep)|检索当前进度条控件的进度条的步长增量。|
|[CProgressCtrl：：偏移波](#offsetpos)|按指定增量推进进度条控件的当前位置，然后重绘条形以反映新位置。|
|[CProgressCtrl：：设置栏颜色](#setbarcolor)|设置当前进度条控件中的进度指示器栏的颜色。|
|[CProgressCtrl：：SetBkColor](#setbkcolor)|设置进度栏的背景颜色。|
|[CProgressCtrl：：SetMarquee](#setmarquee)|为当前进度条控件打开或关闭选框模式。|
|[CProgressCtrl：：SetPos](#setpos)|设置进度条控件的当前位置，并重绘条形以反映新位置。|
|[CProgressCtrl：：设置范围](#setrange)|设置进度条控件的最小和最大范围，并重绘条形以反映新范围。|
|[CProgressCtrl：：设置状态](#setstate)|设置当前进度栏控件的状态。|
|[CProgressCtrl：：设置步骤](#setstep)|指定进度条控件的步长增量。|
|[CProgressCtrl：：步骤](#stepit)|按步长增量推进进度条控件的当前位置（请参阅[SetStep），](#setstep)然后重绘条形以反映新位置。|

## <a name="remarks"></a>备注

进度条控件是应用程序可用于指示长时间操作进度的窗口。 它由从左到右逐渐填充的矩形组成，系统在操作过程中突出显示颜色。

进度条控件具有范围和当前位置。 范围表示操作的总持续时间，当前位置表示应用程序在完成操作时所做的进度。 窗口过程使用范围和当前位置来确定进度条的百分比以填充高光颜色。 由于范围和当前位置值以已签名整数表示，因此当前仓位值的可能范围为 -2，147，483，648 到 2，147，483，647（含）。

有关 使用`CProgressCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cprogressctrlcprogressctrl"></a><a name="cprogressctrl"></a>CProgressCtrl：：CProgressCtrl

构造 `CProgressCtrl` 对象。

```
CProgressCtrl();
```

### <a name="remarks"></a>备注

构造`CProgressCtrl`对象后，调用`CProgressCtrl::Create`以创建进度条控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

## <a name="cprogressctrlcreate"></a><a name="create"></a>CProgressCtrl：：创建

创建进度条控件并将其附加到`CProgressCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定进度条控件的样式。 除了以下进度栏控件样式外，将 Windows SDK 中的["创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)"中描述的窗口样式的任意组合应用于控件：

- PBS_VERTICAL垂直显示进度信息，从上到下。 如果没有此标志，进度条控件将水平（从左到右）显示。

- PBS_SMOOTH 在进度条控件中显示逐渐、平滑的填充。 如果没有此标志，控件将填充块。

*矩形*<br/>
指定进度条控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。 由于控件必须是子窗口，因此指定的坐标相对于*pParentWnd*的工作区。

*pparentwnd*<br/>
指定进度条控件的父窗口，通常为`CDialog`。 值不得为 NULL。

*nID*<br/>
指定进度条控件的 ID。

### <a name="return-value"></a>返回值

如果对象已成功`CProgressCtrl`创建，则为 TRUE;如果对象已成功创建，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

分两步`CProgressCtrl`构造对象。 首先调用构造函数，该构造函数创建`CProgressCtrl`对象，然后调用`Create`，这将创建进度条控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

## <a name="cprogressctrlcreateex"></a><a name="createex"></a>CProgressCtrl：：创建Ex

创建控件（子窗口），并将其与`CProgressCtrl`对象关联。

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
指定进度条控件的样式。 应用 Windows SDK 中[创建窗口](/windows/win32/api/winuser/nf-winuser-createwindoww)中描述的窗口样式的任意组合。

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

## <a name="cprogressctrlgetbarcolor"></a><a name="getbarcolor"></a>CProgressCtrl：：获取巴彩

获取当前进度条控件的进度指示器栏的颜色。

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>返回值

当前进度条的颜色（表示为[COLORREF](/windows/win32/gdi/colorref)值）或CLR_DEFAULT如果进度指示器条颜色为默认颜色。

### <a name="remarks"></a>备注

此方法发送[PBM_GETBARCOLOR](/windows/win32/Controls/pbm-getbarcolor)消息，这在 Windows SDK 中介绍。

## <a name="cprogressctrlgetbkcolor"></a><a name="getbkcolor"></a>CProgressCtrl：：GetBkColor

获取当前进度栏的背景颜色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

当前进度条的背景颜色，表示为[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此方法发送[PBM_GETBKCOLOR](/windows/win32/Controls/pbm-getbkcolor)消息，这在 Windows SDK 中介绍。

## <a name="cprogressctrlgetpos"></a><a name="getpos"></a>CProgressCtrl：：获取Pos

检索进度条的当前位置。

```
int GetPos();
```

### <a name="return-value"></a>返回值

进度条控件的位置。

### <a name="remarks"></a>备注

进度条控件的位置不是屏幕上的物理位置，而是在[SetRange](#setrange)中指示的上下范围之间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

## <a name="cprogressctrlgetrange"></a><a name="getrange"></a>CProgressCtrl：获取范围

获取进度条控件的当前下限和上限或范围。

```cpp
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>参数

*n 更低*<br/>
对接收进度条控件下限的整数的引用。

*n 上*<br/>
对接收进度条控件上限的整数的引用。

### <a name="remarks"></a>备注

此函数分别将下限和上限的值复制到*nLower*和*nUpper*引用的整数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

## <a name="cprogressctrlgetstate"></a><a name="getstate"></a>CProgressCtrl：：获取状态

获取当前进度条控件的状态。

```
int GetState() const;
```

### <a name="return-value"></a>返回值

当前进度条控件的状态，这是以下值之一：

|“值”|状态|
|-----------|-----------|
|PBST_NORMAL|正在进行|
|PBST_ERROR|错误|
|PBST_PAUSED|已暂停|

### <a name="remarks"></a>备注

此方法发送[PBM_GETSTATE](/windows/win32/Controls/pbm-getstate)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

以下代码示例检索当前进度条控件的状态。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

## <a name="cprogressctrlgetstep"></a><a name="getstep"></a>CProgressCtrl：获取步骤

检索当前进度条控件的进度条的步长增量。

```
int GetStep() const;
```

### <a name="return-value"></a>返回值

进度条的步骤增量。

### <a name="remarks"></a>备注

步骤增量是调用[CProgressCtrl：：Step它](#stepit)增加进度条的当前位置的量。

此方法发送[PBM_GETSTEP](/windows/win32/Controls/pbm-getstep)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

以下代码示例检索当前进度条控件的步长增量。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

## <a name="cprogressctrloffsetpos"></a><a name="offsetpos"></a>CProgressCtrl：：偏移波

通过*nPos*指定的增量推进进度条控件的当前位置，然后重绘条形以反映新位置。

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
预付头寸的金额。

### <a name="return-value"></a>返回值

进度条控件的上一个位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

## <a name="cprogressctrlsetbarcolor"></a><a name="setbarcolor"></a>CProgressCtrl：：设置栏颜色

设置当前进度条控件中的进度指示器栏的颜色。

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*clrBar*|[在]指定进度指示器栏的新颜色的[COLORREF](/windows/win32/gdi/colorref)值。 指定CLR_DEFAULT使进度条使用其默认颜色。|

### <a name="return-value"></a>返回值

进度指示器栏的前一颜色（表示为[COLORREF](/windows/win32/gdi/colorref)值）或CLR_DEFAULT如果进度指示器栏的颜色为默认颜色。

### <a name="remarks"></a>备注

仅当 Windows Vista 主题无效时，该方法才会设置进度条颜色。 [theme](/windows/win32/Controls/visual-styles-overview) `SetBarColor`

此方法发送[PBM_SETBARCOLOR](/windows/win32/Controls/pbm-setbarcolor)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

以下代码示例将进度条的颜色更改为红色、绿色、蓝色或默认值。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

## <a name="cprogressctrlsetbkcolor"></a><a name="setbkcolor"></a>CProgressCtrl：：SetBkColor

设置进度栏的背景颜色。

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>参数

*clrNew*<br/>
指定新背景颜色的 COLORREF 值。 指定CLR_DEFAULT值以使用进度条的默认背景颜色。

### <a name="return-value"></a>返回值

[COLORREF](/windows/win32/gdi/colorref)值指示以前的背景颜色，如果背景颜色为默认颜色，则CLR_DEFAULT。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

## <a name="cprogressctrlsetmarquee"></a><a name="setmarquee"></a>CProgressCtrl：：SetMarquee

为当前进度条控件打开或关闭选框模式。

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*fMarqueeMode*|[在]TRUE 可打开选框模式，或 FALSE 关闭选框模式。|
|*n 间隔*|[在]选取框动画更新之间的时间（以毫秒为单位）。|

### <a name="return-value"></a>返回值

此方法始终返回 TRUE。

### <a name="remarks"></a>备注

启用选取框模式后，进度栏将设置动画，并像影院选框上的符号一样滚动。

此方法发送[PBM_SETMARQUEE](/windows/win32/Controls/pbm-setmarquee)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

以下代码示例启动并停止选取框滚动动画。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

## <a name="cprogressctrlsetpos"></a><a name="setpos"></a>CProgressCtrl：：SetPos

设置*nPos*指定的进度条控件的当前位置，并重绘条形以反映新位置。

```
int SetPos(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
进度条控件的新位置。

### <a name="return-value"></a>返回值

进度条控件的上一个位置。

### <a name="remarks"></a>备注

进度条控件的位置不是屏幕上的物理位置，而是在[SetRange](#setrange)中指示的上下范围之间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

## <a name="cprogressctrlsetrange"></a><a name="setrange"></a>CProgressCtrl：：设置范围

设置进度条控件范围的上限和下限，并重绘条形以反映新范围。

```cpp
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>参数

*n 更低*<br/>
指定范围的下限（默认值为零）。

*n 上*<br/>
指定范围的上限（默认值为 100）。

### <a name="remarks"></a>备注

成员函数`SetRange32`为进度控制设置 32 位范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

## <a name="cprogressctrlsetstate"></a><a name="setstate"></a>CProgressCtrl：：设置状态

设置当前进度栏控件的状态。

```
int SetState(int iState);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*i国家*|[在]要设置进度条的状态。 使用以下值之一：<br /><br /> - PBST_NORMAL - 正在进行中<br />- PBST_ERROR - 错误<br />- PBST_PAUSED - 暂停|

### <a name="return-value"></a>返回值

当前进度栏控件的前一个状态。

### <a name="remarks"></a>备注

此方法发送[PBM_SETSTATE](/windows/win32/Controls/pbm-setstate)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例将当前进度栏控件的状态设置为“已暂停”或“正在进行中”。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

## <a name="cprogressctrlsetstep"></a><a name="setstep"></a>CProgressCtrl：：设置步骤

指定进度条控件的步长增量。

```
int SetStep(int nStep);
```

### <a name="parameters"></a>参数

*n步步*<br/>
新步骤增量。

### <a name="return-value"></a>返回值

上一步增量。

### <a name="remarks"></a>备注

步骤增量是调用`CProgressCtrl::StepIt`增加进度条的当前位置的金额。

默认步骤增量为 10。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

## <a name="cprogressctrlstepit"></a><a name="stepit"></a>CProgressCtrl：：步骤

按步长增量推进进度条控件的当前位置，然后重绘条以反映新位置。

```
int StepIt();
```

### <a name="return-value"></a>返回值

进度条控件的上一个位置。

### <a name="remarks"></a>备注

步骤增量由`CProgressCtrl::SetStep`成员函数设置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
