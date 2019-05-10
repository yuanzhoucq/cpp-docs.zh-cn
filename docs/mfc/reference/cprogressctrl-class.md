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
ms.openlocfilehash: 15241485278f09d16c86fc7274f2fc1d85a7a2f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372402"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl 类

提供 Windows 公共进度栏控件的功能。

## <a name="syntax"></a>语法

```
class CProgressCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|构造 `CProgressCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CProgressCtrl::Create](#create)|创建进度栏控件，并将其附加到`CProgressCtrl`对象。|
|[CProgressCtrl::CreateEx](#createex)|使用指定的 Windows 扩展样式创建进度控件，并将其附加到`CProgressCtrl`对象。|
|[CProgressCtrl::GetBarColor](#getbarcolor)|获取当前进度栏控件进度指示符栏的颜色。|
|[CProgressCtrl::GetBkColor](#getbkcolor)|获取当前进度栏的背景色。|
|[CProgressCtrl::GetPos](#getpos)|获取进度栏的当前位置。|
|[CProgressCtrl::GetRange](#getrange)|获取进度栏控件的范围的下限和上限限制。|
|[CProgressCtrl::GetState](#getstate)|获取当前进度栏控件的状态。|
|[CProgressCtrl::GetStep](#getstep)|检索当前进度栏控件的进度栏的步骤增量。|
|[CProgressCtrl::OffsetPos](#offsetpos)|进度栏控件的当前位置提升以指定的增量并重绘条以反映新的位置。|
|[CProgressCtrl::SetBarColor](#setbarcolor)|设置当前进度栏控件中的进度指示符栏的颜色。|
|[CProgressCtrl::SetBkColor](#setbkcolor)|设置进度栏的背景色。|
|[CProgressCtrl::SetMarquee](#setmarquee)|关闭当前进度栏控件的字幕模式打开或关闭。|
|[CProgressCtrl::SetPos](#setpos)|设置当前进度栏控件位置并重新绘制条以反映新的位置。|
|[CProgressCtrl::SetRange](#setrange)|设置进度栏控件的最小值和最大范围并重新绘制条以反映新的范围。|
|[CProgressCtrl::SetState](#setstate)|设置当前进度栏控件的状态。|
|[CProgressCtrl::SetStep](#setstep)|指定进度栏控件的步骤增量。|
|[CProgressCtrl::StepIt](#stepit)|进度栏控件的当前位置提升步骤增量 (请参阅[SetStep](#setstep)) 并重新绘制条以反映新的位置。|

## <a name="remarks"></a>备注

进度栏控件是一个窗口，其中应用程序可以使用它来指示漫长操作的进度。 它包含一个矩形，逐渐填充来显示，从左到右，与系统突出显示颜色操作进度。

进度栏控件具有一个范围和当前的位置。 范围表示该操作的总持续时间和当前的位置表示应用程序已完成该操作方面的进度。 窗口过程使用的范围和当前的位置来确定的进度栏，以突出显示颜色填充百分比。 范围和当前的位置值表示为有符号整数，因为当前的位置值的可能范围是从-2,147,483,648 到 2,147,483,647 非独占。

有关使用的详细信息`CProgressCtrl`，请参阅[控件](../../mfc/controls-mfc.md)并[使用 CProgressCtrl](../../mfc/using-cprogressctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CProgressCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl

构造 `CProgressCtrl` 对象。

```
CProgressCtrl();
```

### <a name="remarks"></a>备注

构造后`CProgressCtrl`对象，请调用`CProgressCtrl::Create`创建进度栏控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]

##  <a name="create"></a>  CProgressCtrl::Create

创建进度栏控件，并将其附加到`CProgressCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定进度栏控件的样式。 应用窗口 stylesdescribed 中的任意组合[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)在 Windows SDK 中，除了以下进度栏控件样式，向控件：

- PBS_VERTICAL 显示垂直进度的信息，请从上到下。 如果没有此标志，进度栏控件可显示水平、 左到右。

- PBS_SMOOTH 显示逐步，平滑填充进度栏控件。 如果没有此标志，该控件将填充与块中。

*rect*<br/>
指定进度栏控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。 因为该控件必须是子窗口，指定的坐标是相对于客户端区域*pParentWnd*。

*pParentWnd*<br/>
通常指定进度栏控件的父窗口`CDialog`。 它不能为 NULL。

*nID*<br/>
指定进度栏控件的 id。

### <a name="return-value"></a>返回值

如果`CProgressCtrl`对象是已成功创建; 否则为 FALSE。

### <a name="remarks"></a>备注

构造`CProgressCtrl`两个步骤中的对象。 首先，调用构造函数中，这会创建`CProgressCtrl`对象，，然后调用`Create`，这将创建进度栏控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]

##  <a name="createex"></a>  CProgressCtrl::CreateEx

创建控件 （子窗口），并将其与`CProgressCtrl`对象。

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
指定进度栏控件的样式。 应用窗口样式中所述的任意组合[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) Windows SDK 中。

*rect*<br/>
对引用[RECT](/previous-versions/dd162897\(v=vs.85\))结构的结构描述的大小和窗口的工作区中创建的位置*pParentWnd*。

*pParentWnd*<br/>
指向控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是[创建](#create)若要将应用扩展的 Windows 样式，指定的 Windows 扩展的样式加**WS_EX_**。

##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor

获取当前进度栏控件进度指示符栏的颜色。

```
COLORREF GetBarColor() const;
```

### <a name="return-value"></a>返回值

当前进度栏的颜色表示为[COLORREF](/windows/desktop/gdi/colorref)值或 CLR_DEFAULT 如果进度指示器栏颜色为默认颜色。

### <a name="remarks"></a>备注

此方法将发送[PBM_GETBARCOLOR](/windows/desktop/Controls/pbm-getbarcolor)消息，Windows SDK 中所述。

##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor

获取当前进度栏的背景色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

表示为当前进度栏的背景色[COLORREF](/windows/desktop/gdi/colorref)值。

### <a name="remarks"></a>备注

此方法将发送[PBM_GETBKCOLOR](/windows/desktop/Controls/pbm-getbkcolor)消息，Windows SDK 中所述。

##  <a name="getpos"></a>  CProgressCtrl::GetPos

检索进度栏的当前位置。

```
int GetPos();
```

### <a name="return-value"></a>返回值

进度栏控件的位置。

### <a name="remarks"></a>备注

进度栏控件的位置不在屏幕上的物理位置，但而不是为之间上限和下限范围所示[SetRange](#setrange)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]

##  <a name="getrange"></a>  CProgressCtrl::GetRange

获取当前的下限和上限限制或范围，进度栏控件。

```
void GetRange(
    int& nLower,
    int& nUpper);
```

### <a name="parameters"></a>参数

*nLower*<br/>
对接收进度栏控件的下限的整数的引用。

*nUpper*<br/>
对接收进度栏控件的上限的整数的引用。

### <a name="remarks"></a>备注

此函数将下限和上限限制的值复制到引用的整数*nLower*并*nUpper*分别。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]

##  <a name="getstate"></a>  CProgressCtrl::GetState

获取当前进度栏控件的状态。

```
int GetState() const;
```

### <a name="return-value"></a>返回值

当前的进度栏控件，这是以下值之一的状态：

|“值”|状态|
|-----------|-----------|
|PBST_NORMAL|正在进行|
|PBST_ERROR|Error|
|PBST_PAUSED|已暂停|

### <a name="remarks"></a>备注

此方法将发送[PBM_GETSTATE](/windows/desktop/Controls/pbm-getstate)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例检索当前进度栏控件的状态。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]

##  <a name="getstep"></a>  CProgressCtrl::GetStep

检索当前进度栏控件的进度栏的步骤增量。

```
int GetStep() const;
```

### <a name="return-value"></a>返回值

进度栏的步骤增量。

### <a name="remarks"></a>备注

步骤增量是所根据的数量对的调用[CProgressCtrl::StepIt](#stepit)增加进度栏的当前位置。

此方法将发送[PBM_GETSTEP](/windows/desktop/Controls/pbm-getstep)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例检索当前进度栏控件的步骤增量。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]

##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos

进度栏控件的当前位置提升由指定的增量*nPos*并重新绘制条以反映新的位置。

```
int OffsetPos(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
若要提升位置的量。

### <a name="return-value"></a>返回值

进度栏控件的以前的位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]

##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor

设置当前进度栏控件中的进度指示符栏的颜色。

```
COLORREF SetBarColor(COLORREF clrBar);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*clrBar*|[in]一个[COLORREF](/windows/desktop/gdi/colorref)值，该值指定进度指示符栏的新颜色。 指定 CLR_DEFAULT 若要使进度条，以使用其默认颜色。|

### <a name="return-value"></a>返回值

前一种颜色的进度指示条，表示为[COLORREF](/windows/desktop/gdi/colorref)值或 CLR_DEFAULT 如果进度指示符栏的颜色为默认颜色。

### <a name="remarks"></a>备注

`SetBarColor`方法设置进度栏颜色仅当 Windows Vista[主题](/windows/desktop/Controls/visual-styles-overview)不起作用。

此方法将发送[PBM_SETBARCOLOR](/windows/desktop/Controls/pbm-setbarcolor)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例更改进度栏的颜色为红色、 绿色、 蓝色或默认值。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]

##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor

设置进度栏的背景色。

```
COLORREF SetBkColor(COLORREF clrNew);
```

### <a name="parameters"></a>参数

*clrNew*<br/>
一个 COLORREF 值，该值指定新背景色。 指定要用于进度栏的默认背景色的 CLR_DEFAULT 值。

### <a name="return-value"></a>返回值

[COLORREF](/windows/desktop/gdi/colorref)值，该值指示以前的背景色或 CLR_DEFAULT 如果背景色为默认颜色。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]

##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee

关闭当前进度栏控件的字幕模式打开或关闭。

```
BOOL SetMarquee(
    BOOL fMarqueeMode,
    int nInterval);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*fMarqueeMode*|[in]设置为 True 或 FALSE 可以关闭字幕模式打开字幕模式。|
|*nInterval*|[in]以毫秒为单位的字幕动画的更新之间的时间。|

### <a name="return-value"></a>返回值

此方法始终返回 TRUE。

### <a name="remarks"></a>备注

当打开字幕模式、 进度栏的动画和滚动等登录影院字幕。

此方法将发送[PBM_SETMARQUEE](/windows/desktop/Controls/pbm-setmarquee)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例启动和停止滚动动画字幕。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]

##  <a name="setpos"></a>  CProgressCtrl::SetPos

设置进度栏控件的当前位置由指定*nPos*并重新绘制条以反映新的位置。

```
int SetPos(int nPos);
```

### <a name="parameters"></a>参数

*nPos*<br/>
进度栏控件的新位置。

### <a name="return-value"></a>返回值

进度栏控件的以前的位置。

### <a name="remarks"></a>备注

进度栏控件的位置不在屏幕上的物理位置，但而不是为之间上限和下限范围所示[SetRange](#setrange)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]

##  <a name="setrange"></a>  CProgressCtrl::SetRange

设置进度栏控件的范围的上限和下限限制并重新绘制条以反映新的范围。

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>参数

*nLower*<br/>
指定范围的下限 （默认值为零）。

*nUpper*<br/>
指定范围的上限 （默认值为 100）。

### <a name="remarks"></a>备注

成员函数`SetRange32`设置进度控件的 32 位范围。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]

##  <a name="setstate"></a>  CProgressCtrl::SetState

设置当前进度栏控件的状态。

```
int SetState(int iState);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iState*|[in]要设置进度栏的状态。 使用下列值之一：<br /><br /> -PBST_NORMAL-正在进行中<br />- PBST_ERROR - Error<br />-PBST_PAUSED-暂停|

### <a name="return-value"></a>返回值

当前进度栏控件的前一个状态。

### <a name="remarks"></a>备注

此方法将发送[PBM_SETSTATE](/windows/desktop/Controls/pbm-setstate)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量 `m_progressCtrl`，该变量用于以编程方式访问进度栏控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]

### <a name="example"></a>示例

下面的代码示例将当前进度栏控件的状态设置为“已暂停”或“正在进行中”。

[!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]

##  <a name="setstep"></a>  CProgressCtrl::SetStep

指定进度栏控件的步骤增量。

```
int SetStep(int nStep);
```

### <a name="parameters"></a>参数

*nStep*<br/>
新步骤增量。

### <a name="return-value"></a>返回值

上一步骤增量。

### <a name="remarks"></a>备注

步骤增量是所根据的数量调用`CProgressCtrl::StepIt`增加进度栏的当前位置。

默认步骤增量为 10。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]

##  <a name="stepit"></a>  CProgressCtrl::StepIt

进度栏控件的当前位置提升步骤增量并重绘条以反映新的位置。

```
int StepIt();
```

### <a name="return-value"></a>返回值

进度栏控件的以前的位置。

### <a name="remarks"></a>备注

通过设置步骤增量`CProgressCtrl::SetStep`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
