---
title: CMonthCalCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
ms.openlocfilehash: bd062a4e0d4db364c9cb628608c6af165dc0edc2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "58777163"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl 类

封装月历控件的功能。

## <a name="syntax"></a>语法

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|构造 `CMonthCalCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMonthCalCtrl::Create](#create)|创建月历控件，并将其附加到`CMonthCalCtrl`对象。|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|检索当前月份的日历控件的边框的宽度。|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|检索当前月份的日历控件中显示的日历的数。|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|检索当前月份的日历控件有关的信息。|
|[CMonthCalCtrl::GetCalID](#getcalid)|检索当前月历控件的日历标识符。|
|[CMonthCalCtrl::GetColor](#getcolor)|获取月历控件的指定区域的颜色。|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|检索当前月份的日历控件当前显示的视图。|
|[CMonthCalCtrl::GetCurSel](#getcursel)|检索系统时间所指示的当前所选日期。|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|获取一周中的日历的最左侧列中显示的第一天。|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|检索当前的最大数目的可选择在月历控件中的天。|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|检索当前月份的日历控件的"Today"字符串的最大宽度。|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|检索在月历控件中显示一整月所需的最小大小。|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|检索月历控件的滚动率。|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|检索的日期表示月历控件的显示的高和低限制的信息。|
|[CMonthCalCtrl::GetRange](#getrange)|检索在月历控件中设置的当前最小和最大日期。|
|[CMonthCalCtrl::GetSelRange](#getselrange)|检索表示用户当前选择的日期范围的上限和下限限制日期信息。|
|[CMonthCalCtrl::GetToday](#gettoday)|检索指定为"今天"的月历控件的日期的日期信息。|
|[CMonthCalCtrl::HitTest](#hittest)|确定在屏幕上给定点处为月历控件的哪个部分。|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|指示当前月历控件的当前视图是否为世纪视图。|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|指示当前月历控件的当前视图是否为十年视图。|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|指示当前月历控件的当前视图是否为月视图。|
|[CMonthCalCtrl::IsYearView](#isyearview)|指示当前月历控件的当前视图是否为年视图。|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|设置当前月份的日历控件的边框宽度。|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|设置当前月份的日历控件的边框的默认宽度。|
|[CMonthCalCtrl::SetCalID](#setcalid)|设置当前月历控件的日历标识符。|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|设置要显示世纪视图的当前月份的日历控件。|
|[CMonthCalCtrl::SetColor](#setcolor)|设置月历控件的指定区域的颜色。|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|设置当前月份的日历控件，以显示指定的视图。|
|[CMonthCalCtrl::SetCurSel](#setcursel)|设置月历控件的当前所选的日期。|
|[CMonthCalCtrl::SetDayState](#setdaystate)|将天显示设置月历控件中。|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|设置当前的月历控件到十年视图。|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|设置要在日历的最左侧列中显示的每周的某一日。|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|设置月历控件中可选择最大天数。|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|设置月历控件的滚动率。|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|设置要显示月视图的当前月份的日历控件。|
|[CMonthCalCtrl::SetRange](#setrange)|设置最小值和最大允许月历控件的日期。|
|[CMonthCalCtrl::SetSelRange](#setselrange)|设置月历所选内容来控制对给定的日期范围。|
|[CMonthCalCtrl::SetToday](#settoday)|设置当前日期的日历控件。|
|[CMonthCalCtrl::SetYearView](#setyearview)|设置当前的月历控件到年视图。|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|重绘月历控制转移到其最小值、 一个月的大小。|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|对于当前月份的日历控件，将计算的最小矩形可以包含指定的矩形中容纳不下的所有日历。|

## <a name="remarks"></a>备注

月历控件提供了一个简单的日历界面，用户可以从中选择一个日期的用户。 用户可以更改通过显示：

- 从本月截止到月向后和向前移动，滚动。

- 单击以显示当前日期 （如果未使用 MCS_NOTODAY 样式） 的当前文本。

- 选择一个月或年从弹出菜单。

你可以自定义该月通过将各种样式应用于该对象在创建时的月历控件。 这些样式中所述[个月日历控件样式](/windows/desktop/Controls/month-calendar-control-styles)Windows SDK 中。

月历控件可以显示多个月份，并且可以指示特殊天 （如节假日） 通过粗体日期。

使用月历控件的详细信息，请参阅[使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>要求

**标头：** afxdtctl.h

##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl

构造 `CMonthCalCtrl` 对象。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>备注

必须调用`Create`构造对象后。

##  <a name="create"></a>  CMonthCalCtrl::Create

创建月历控件，并将其附加到`CMonthCalCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定应用于月历控件的 Windows 样式的组合。 请参阅[个月日历控件样式](/windows/desktop/Controls/month-calendar-control-styles)有关样式的详细信息 Windows SDK 中。

*rect*<br/>
对引用[RECT](/previous-versions/dd162897\(v=vs.85\))结构。 包含的位置和月历控件的大小。

*pt*<br/>
对引用[点](/previous-versions/dd162805\(v=vs.85\))结构，它标识月历控件的位置。

*pParentWnd*<br/>
一个指向[CWnd](../../mfc/reference/cwnd-class.md)是月历控件的父窗口的对象。 它不能为 NULL。

*nID*<br/>
指定月历控件的控件 id。

### <a name="return-value"></a>返回值

如果初始化成功，则非零值否则为 0。

### <a name="remarks"></a>备注

创建一个月的月历控件中两个步骤：

1. 调用[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)构造`CMonthCalCtrl`对象。

1. 调用此成员函数，将创建月历控件并将其附加到`CMonthCalCtrl`对象。

当您调用`Create`，公共控件进行初始化。 版本的`Create`您调用确定如何调整大小：

- 如果希望自动调整大小为一个月的控件的 MFC，请调用使用的重写*pt*参数。

- 若要自行调整该控件，调用此函数，它使用的重写*rect*参数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder

检索当前月份的日历控件的边框的宽度。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>返回值

控件边框，以像素为单位的宽度。

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder)消息，Windows SDK 中所述。

##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount

检索当前月份的日历控件中显示的日历的数。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>返回值

月历控件中当前显示的日历的数。 日历的最大允许的数目为 12。

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount)消息，Windows SDK 中所述。

##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo

检索当前月份的日历控件有关的信息。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pmcGridInfo*|[out]指向[MCGRIDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo)接收当前月历控件的相关信息的结构。 调用方负责分配和初始化此结构。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例使用`GetCalendarGridInfo`方法来检索当前月份的日历控件显示的日历日期。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID

检索当前月历控件的日历标识符。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>返回值

之一[日历标识符](/windows/desktop/Intl/calendar-identifiers)常量。

### <a name="remarks"></a>备注

日历标识符表示特定于区域的日历，例如公历 （本地化）、 日语或回历日历。 你的应用程序可以使用具有函数的支持的各种语言的日历标识符。

此方法将发送[MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid)消息，Windows SDK 中所述。

##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor

检索的月份中的一个区域的颜色的月历控件指定*nRegion*。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>参数

*nRegion*<br/>
从中检索颜色月历控件的区域。 值的列表，请参阅*nRegion*的参数[SetColor](#setcolor)。

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/desktop/gdi/colorref)值，如果成功，则指定的部分月历控件，与关联的颜色。 否则，此成员函数返回-1。

##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView

检索当前月份的日历控件当前显示的视图。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>返回值

当前视图，这将由以下值之一：

|值|含义|
|-----------|-------------|
|MCMV_MONTH|每月视图|
|MCMV_YEAR|每年的视图|
|MCMV_DECADE|十年视图|
|MCMV_CENTURY|世纪视图|

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

以下代码示例报表的查看月历控件当前显示。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel

检索系统时间所指示的当前所选日期。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。 接收当前时间。

*pDateTime*<br/>
一个指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它将接收的当前所选日期信息。 此参数必须是有效的地址，并且不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，则非零值otherwize 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel)，如 Windows SDK 中所述。

> [!NOTE]
>  如果 style 设 MCS_MULTISELECT，此成员函数将失败。

在 MFC 的实现中的`GetCurSel`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek

获取一周中的日历的最左侧列中显示的第一天。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>参数

*pbLocal*<br/>
指向布尔值的指针。 如果值为非零值，该控件的设置不匹配控制面板中的设置。

### <a name="return-value"></a>返回值

一个表示一周的第一天的整数值。 请参阅**备注**有关这些整数表示的含义的详细信息。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek)，如 Windows SDK 中所述。 每周天数表示为整数，按如下所示。

|值|日期是星期几|
|-----------|---------------------|
|0|星期一|
|1|星期二|
|2|星期三|
|3|星期四|
|4|星期五|
|5|星期六|
|6|星期日|

### <a name="example"></a>示例

  有关示例，请参阅[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)。

##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount

检索当前的最大数目的可选择在月历控件中的天。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>返回值

一个表示总的控件可以选择的天数的整数值。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount)，如 Windows SDK 中所述。 使用此成员函数具有 MCS_MULTISELECT 样式设置控件。

### <a name="example"></a>示例

  有关示例，请参阅[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)。

##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth

检索当前月份的日历控件的"Today"字符串的最大宽度。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>返回值

"Today"字符串，以像素为单位的宽度。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例演示了`GetMaxTodayWidth`方法。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>备注

用户可以通过单击"Today"字符串，它在月历控件的底部显示返回为当前日期。 "Today"字符串包括标签文本和日期的文本。

此方法将发送[MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth)消息，Windows SDK 中所述。

##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect

检索在月历控件中显示一整月所需的最小大小。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>参数

*pRect*<br/>
一个指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构，它将接收边界矩形信息。 此参数必须是有效的地址，并且不能为 NULL。

### <a name="return-value"></a>返回值

如果设置成功后，此成员函数将返回非零值和`lpRect`接收相应的边界信息。 如果不成功，则成员函数返回 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect)，如 Windows SDK 中所述。

##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta

检索月历控件的滚动率。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>返回值

月历控件的滚动率。 滚动率是控制移动其显示，当用户单击滚动按钮一次的月数。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta)，如 Windows SDK 中所述。

##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange

检索的日期表示月历控件的显示的高和低限制的信息。

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>参数

*refMinRange*<br/>
对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含允许的最小日期。

*refMaxRange*<br/>
对引用`COleDateTime`或`CTime`对象，其中包含允许的最大日期。

*pMinRange*<br/>
一个指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它包含最小范围的末尾处的日期。

*pMaxRange*<br/>
一个指向`SYSTEMTIME`结构，它包含的日期范围的最高的末尾。

*dwFlags*<br/>
值，该值指定要检索的范围限制的作用域。 此值必须是以下值之一。

|值|含义|
|-----------|-------------|
|GMR_DAYSTATE|包括前导和尾随的可见范围仅部分显示的月份。|
|GMR_VISIBLE|包含完全显示的月份。|

### <a name="return-value"></a>返回值

一个整数，表示跨两个限制的范围，以月为单位，为由*refMinRange*并*refMaxRange*中的第一个和第二个版本，或*pMinRange*并*pMaxRange*中的第三个版本。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange)，如 Windows SDK 中所述。 在 MFC 的实现中的`GetMonthRange`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

### <a name="example"></a>示例

  有关示例，请参阅[cmonthcalctrl:: Setdaystate](#setdaystate)。

##  <a name="getrange"></a>  CMonthCalCtrl::GetRange

检索在月历控件中设置的当前最小和最大日期。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>参数

*pMinRange*<br/>
一个指向`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它包含最小范围的末尾处的日期。

*pMaxRange*<br/>
一个指向`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它包含的日期范围的最高的末尾。

### <a name="return-value"></a>返回值

可以为零的 DWORD （设置无限制） 或指定限制的信息的以下值的组合。

|值|含义|
|-----------|-------------|
|GDTR_MAX|为控件; 设置最大限制*pMaxRange*有效，并且包含的适用日期信息。|
|GDTR_MIN|为控件; 设置最小限制*pMinRange*有效，并且包含的适用日期信息。|

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange)，如 Windows SDK 中所述。 在 MFC 的实现中的`GetRange`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange

检索表示用户当前选择的日期范围的上限和下限限制日期信息。

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>参数

*refMinRange*<br/>
对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含允许的最小日期。

*refMaxRange*<br/>
对引用`COleDateTime`或`CTime`对象，其中包含允许的最大日期。

*pMinRange*<br/>
一个指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它包含最小范围的末尾处的日期。

*pMaxRange*<br/>
一个指向`SYSTEMTIME`结构，它包含的日期范围的最高的末尾。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange)，如 Windows SDK 中所述。 `GetSelRange` 如果应用于月历控件不使用 MCS_MULTISELECT 样式将失败。

在 MFC 的实现中的`GetSelRange`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday

检索指定为"今天"的月历控件的日期的日期信息。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，该值指示当前的日期。

*pDateTime*<br/>
一个指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它将接收的日期信息。 此参数必须是有效的地址，并且不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday)，如 Windows SDK 中所述。 在 MFC 的实现中的`GetToday`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>  CMonthCalCtrl::HitTest

确定哪些月历控件，如果任何，在指定位置。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>参数

*pMCHitTest*<br/>
一个指向[MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo)为月历控件的结构，它包含命中测试点。

### <a name="return-value"></a>返回值

一个 DWORD 值。 等于**uHit**的成员`MCHITTESTINFO`结构。

### <a name="remarks"></a>备注

`HitTest` 使用`MCHITTESTINFO`结构，其中包含有关命中测试的信息。

##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView

指示当前月历控件的当前视图是否为世纪视图。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是世纪视图; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息，Windows SDK 中所述。 如果该消息返回 MCMV_CENTURY，此方法返回 TRUE。

##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView

指示当前月历控件的当前视图是否为十年视图。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是十年视图; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息，Windows SDK 中所述。 如果该消息返回 MCMV_DECADE，此方法返回 TRUE。

##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView

指示当前月历控件的当前视图是否为月视图。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是月视图中; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息，Windows SDK 中所述。 如果该消息返回 MCMV_MONTH，此方法返回 TRUE。

##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView

指示当前月历控件的当前视图是否为年视图。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是该年视图; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息，Windows SDK 中所述。 如果该消息返回 MCMV_YEAR，此方法返回 TRUE。

##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder

设置当前月份的日历控件的边框宽度。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*cxyBorder*|[in]以像素为单位的边框宽度。|

### <a name="remarks"></a>备注

如果此方法成功，边框宽度设置为*cxyBorder*参数。 否则，边框宽度将重置为当前指定的默认值[主题](/windows/desktop/Controls/visual-styles-overview)，或为零则不使用主题。

此方法将发送[MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例设置月历的边框宽度控制为八个像素。 使用[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)方法来确定此方法是否成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault

设置当前月份的日历控件的边框的默认宽度。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>备注

边框宽度设置为当前指定的默认值[主题](/windows/desktop/Controls/visual-styles-overview)，或为零则不使用主题。

此方法将发送[MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)消息，Windows SDK 中所述。

##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID

设置当前月历控件的日历标识符。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*calid*|[in]之一[日历标识符](/windows/desktop/Intl/calendar-identifiers)常量。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

日历标识符指定特定于区域的日历，例如公历 （本地化）、 日语或回历日历。 使用`SetCalID`方法来显示由指定的日历*calid*参数，如果在计算机上安装包含日历的区域设置。

此方法将发送[MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例设置月历控件以显示日语和历日历。 `SetCalID`方法成功，只有当您的计算机上安装了该日历。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView

设置要显示世纪视图的当前月份的日历控件。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法设置为视图`MCMV_CENTURY`，它表示世纪视图。

##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor

设置月历控件的指定区域的颜色。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>参数

*nRegion*<br/>
一个整数值，指定要设置哪些月日历颜色。 此值可以是以下值之一。

|值|含义|
|-----------|-------------|
|MCSC_BACKGROUND|显示不同的月份的背景色。|
|MCSC_MONTHBK|显示月份中的背景色。|
|MCSC_TEXT|用来在一个月内显示文本的颜色。|
|MCSC_TITLEBK|在日历的标题中显示的背景色。|
|MCSC_TITLETEXT|用于显示日历的标题中的文本的颜色。|
|MCSC_TRAILINGTEXT|用于显示标头和尾部日文本的颜色。 标头和后续日期是当前日历会显示以前及以后月份的天数。|

*ref*<br/>
新颜色设置月历控件的指定部分 COLORREF 值。

### <a name="return-value"></a>返回值

如果成功，则 COLORREF 值表示的指定部分的月历控件，以前的颜色设置。 否则，此消息返回-1。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView

设置当前月份的日历控件，以显示指定的视图。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*dwNewView*|[in]每月、 年、 十年中或世纪视图指定以下值之一。<br /><br /> MCMV_MONTH:每月视图<br /><br /> MCMV_YEAR:每年的视图<br /><br /> MCMV_DECADE:十年视图<br /><br /> MCMV_CENTURY:世纪视图|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview)消息，Windows SDK 中所述。

##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel

设置月历控件的当前所选的日期。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md) ，该值指示当前所选月历控件的对象。

*pDateTime*<br/>
指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，其中包含要设置为当前所选内容的日期。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel)，如 Windows SDK 中所述。 在 MFC 的实现中的`SetCurSel`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>  CMonthCalCtrl::SetDayState

将天显示设置月历控件中。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>参数

*nMonths*<br/>
值，该值指示元素的数量数组中的*pStates*指向。

*pStates*<br/>
一个指向[MONTHDAYSTATE](/windows/desktop/Controls/monthdaystate)定义如何月历控件将其显示在绘制每一天的值的数组。 MONTHDAYSTATE 数据类型是一个位字段，其中每个位 (1 到 31 之间) 表示一个月中某天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView

设置当前的月历控件到十年视图。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法设置为视图`MCMV_DECADE`，它表示十年视图。

##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek

设置要在日历的最左侧列中显示的每周的某一日。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>参数

*iDay*<br/>
一个整数值，表示哪一天是设置为一周的第一天。 此值必须是一天的数字。 请参阅[GetFirstDayOfWeek](#getfirstdayofweek)有关的日编号的说明。

*lpnOld*<br/>
指向一个整数，指示以前的一周的第一天的设置。

### <a name="return-value"></a>返回值

如果以前的第一个日期是星期几设置以外，LOCALE_IFIRSTDAYOFWEEK 的值为非零，这是一天中的控件面板设置指示。 否则，此函数返回 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount

设置月历控件中可选择最大天数。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>参数

*nMax*<br/>
将设置用于表示最大天数可选择的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

设置月历控件的滚动率。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>参数

*iDelta*<br/>
要设置为控件的滚动率的月数。 如果此值为零，则会将月增量重置为默认情况下，在控件中显示的月份数。

### <a name="return-value"></a>返回值

以前的滚动率。 如果之前尚未设置的滚动率，返回值为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta)，如 Windows SDK 中所述。

##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView

设置要显示月视图的当前月份的日历控件。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法设置为 MCMV_MONTH，表示月视图的视图。

### <a name="example"></a>示例

下面的代码示例定义变量， `m_monthCalCtrl`，即用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例设置月历控件以显示月、 年、 十年中和世纪视图。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>  CMonthCalCtrl::SetRange

设置月历控件的最小和最大允许日期。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>参数

*pMinRange*<br/>
一个指向`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它包含最小范围的末尾处的日期。

*pMaxRange*<br/>
一个指向`COleDateTime`对象，`CTime`对象，或`SYSTEMTIME`结构，它包含的日期范围的最高的末尾。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange)，如 Windows SDK 中所述。 在 MFC 的实现中的`SetRange`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

### <a name="example"></a>示例

  有关示例，请参阅[CMonthCalCtrl::GetRange](#getrange)。

##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange

设置月历所选内容来控制对给定的日期范围。

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>参数

*pMinRange*<br/>
一个指向`COleDateTime`对象，`CTime`对象，或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它包含最小范围的末尾处的日期。

*pMaxRange*<br/>
一个指向`COleDateTime`对象，`CTime`对象，或`SYSTEMTIME`结构，它包含的日期范围的最高的末尾。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange)，如 Windows SDK 中所述。 在 MFC 的实现中的`SetSelRange`，可以指定`COleDateTime`使用率`CTime`使用情况，或`SYSTEMTIME`结构使用情况。

##  <a name="settoday"></a>  CMonthCalCtrl::SetToday

设置当前日期的日历控件。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
  void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含当前日期。

*pDateTime*<br/>
在第二个版本中，一个指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含当前日期信息。 在第三个版本中，一个指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，其中包含当前日期信息。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday)，如 Windows SDK 中所述。

### <a name="example"></a>示例

  有关示例，请参阅[CMonthCalCtrl::GetToday](#gettoday)。

##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView

设置当前的月历控件到年视图。

```
BOOL SetYearView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法设置为 MCMV_YEAR，表示每年的视图的视图。

##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq

显示日历控件为的最小大小的月份显示一个月。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>参数

*bRepaint*<br/>
指定是否要重新绘制控件。 默认情况下，则为 TRUE。 如果为 FALSE，没有重新绘制时发生。

### <a name="return-value"></a>返回值

月历控件的大小为其最小值; 如果非零值否则为 0。

### <a name="remarks"></a>备注

调用`SizeMinReq`成功显示整个月历控件的一个月的日历。

##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin

对于当前月份的日历控件，将计算的最小矩形可以包含指定的矩形中容纳不下的所有日历。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpRect*|[in]指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构，它定义包含日历所需的数量的矩形。|

### <a name="return-value"></a>返回值

指向[RECT](/previous-versions/dd162897\(v=vs.85\))由定义结构，它定义的矩形的大小小于或等于矩形*lpRect*参数。

### <a name="remarks"></a>备注

此方法计算指定的矩形中可以容纳多少日历*lpRect*参数，然后返回可以包含该数量的日历的最小矩形。 实际上，此方法会以完全适合所需的日历数的指定的矩形。

此方法将发送[MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin)消息，Windows SDK 中所述。

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl 类](../../mfc/reference/cdatetimectrl-class.md)
