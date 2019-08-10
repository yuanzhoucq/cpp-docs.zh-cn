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
ms.openlocfilehash: 1215247c194d75409c43d3fe1968ebab9ca71781
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916842"
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
|[CMonthCalCtrl::Create](#create)|创建月历控件并将其附加到`CMonthCalCtrl`对象。|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|检索当前月历控件的边框宽度。|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|检索当前月历控件中显示的日历的数目。|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|检索有关当月日历控件的信息。|
|[CMonthCalCtrl::GetCalID](#getcalid)|检索当前月历控件的日历标识符。|
|[CMonthCalCtrl::GetColor](#getcolor)|获取月历控件指定区域的颜色。|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|检索当前月历控件当前显示的视图。|
|[CMonthCalCtrl::GetCurSel](#getcursel)|按当前选定的日期检索系统时间。|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|获取要在日历的最左侧列中显示的一周中的第一天。|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|检索月历控件中可选择的最大天数。|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|检索当前月历控件的 "今日" 字符串的最大宽度。|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|检索在月历控件中显示完整月份所需的最小大小。|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|检索月历控件的滚动率。|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|检索表示月历控件显示的上限和下限的日期信息。|
|[CMonthCalCtrl::GetRange](#getrange)|检索月历控件中设置的当前最小和最大日期。|
|[CMonthCalCtrl::GetSelRange](#getselrange)|检索表示用户当前所选日期范围的上限和下限的日期信息。|
|[CMonthCalCtrl::GetToday](#gettoday)|检索为月历控件指定为 "今日" 的日期的日期信息。|
|[CMonthCalCtrl::HitTest](#hittest)|确定月历控件的哪个部分位于屏幕上的给定点。|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|指示当前月历控件的当前视图是否为 "世纪" 视图。|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|指示当前月历控件的当前视图是否为十年视图。|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|指示当前月历控件的当前视图是否为月份视图。|
|[CMonthCalCtrl::IsYearView](#isyearview)|指示当前月历控件的当前视图是否为 "年" 视图。|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|设置当前月历控件的边框宽度。|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|设置当前月历控件的边框的默认宽度。|
|[CMonthCalCtrl::SetCalID](#setcalid)|设置当月日历控件的日历标识符。|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|设置当前月历控件以显示 "世纪" 视图。|
|[CMonthCalCtrl::SetColor](#setcolor)|设置月历控件的指定区域的颜色。|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|设置当前月历控件以显示指定的视图。|
|[CMonthCalCtrl::SetCurSel](#setcursel)|为月历控件设置当前选定的日期。|
|[CMonthCalCtrl::SetDayState](#setdaystate)|设置月历控件中的天数显示。|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|将 "当月日历" 控件设置为十年视图。|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|设置要在日历的最左侧列中显示的周日期。|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|设置月历控件中可选择的最大天数。|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|设置月历控件的滚动率。|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|设置当前月历控件以显示 "月" 视图。|
|[CMonthCalCtrl::SetRange](#setrange)|设置月历控件允许的最小和最大日期。|
|[CMonthCalCtrl::SetSelRange](#setselrange)|将月历控件的选择设置为给定的日期范围。|
|[CMonthCalCtrl::SetToday](#settoday)|设置当前日期的日历控件。|
|[CMonthCalCtrl::SetYearView](#setyearview)|将当前月历控件设置为 "年" 视图。|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|将月历控件重绘到最小单月大小。|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|对于 "当月日历" 控件, 计算可包含符合指定矩形的所有日历的最小矩形。|

## <a name="remarks"></a>备注

月历控件为用户提供了一个简单的日历界面, 用户可以从中选择日期。 用户可以通过以下方式更改显示:

- 向后和向前 (从月到月) 滚动。

- 单击 "今天" 文本以显示当前日期 (如果未使用 MCS_NOTODAY 样式)。

- 从弹出菜单中选择月份或年份。

您可以在创建月历控件时, 通过将各种样式应用于该对象来对其进行自定义。 Windows SDK 中的月历[控件样式](/windows/desktop/Controls/month-calendar-control-styles)中描述了这些样式。

月历控件可以显示超过一个月, 它可以通过使日期加粗来指示特殊日期 (如假日)。

有关使用月历控件的详细信息, 请参阅[Using CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>要求

**标头:** afxdtctl

##  <a name="cmonthcalctrl"></a>CMonthCalCtrl:: CMonthCalCtrl

构造 `CMonthCalCtrl` 对象。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>备注

构造对象之后`Create` , 必须调用。

##  <a name="create"></a>CMonthCalCtrl:: Create

创建月历控件并将其附加到`CMonthCalCtrl`对象。

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
指定应用于月历控件的 Windows 样式的组合。 有关样式的详细信息, 请参阅[月历控件样式](/windows/desktop/Controls/month-calendar-control-styles)Windows SDK。

*rect*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用。 包含月历控件的位置和大小。

*pt*<br/>
对用于标识月历控件位置的[点](/previous-versions/dd162805\(v=vs.85\))结构的引用。

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针, 该对象是月历控件的父窗口。 它不能为 NULL。

*nID*<br/>
指定月历控件的控件 ID。

### <a name="return-value"></a>返回值

如果初始化成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

通过两个步骤创建月历控件:

1. 调用[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)以构造`CMonthCalCtrl`对象。

1. 调用此成员函数, 该函数创建月历控件并将其附加到`CMonthCalCtrl`对象。

调用`Create`时, 将初始化公共控件。 `Create`您调用的版本确定如何调整它的大小:

- 若要使 MFC 自动将控件大小设置为一个月, 请调用使用*pt*参数的重写。

- 若要自行调整控件大小, 请调用使用*rect*参数的此函数的重写。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>CMonthCalCtrl:: GetCalendarBorder

检索当前月历控件的边框宽度。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>返回值

控件边框的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder)消息, 如 Windows SDK 中所述。

##  <a name="getcalendarcount"></a>CMonthCalCtrl:: GetCalendarCount

检索当前月历控件中显示的日历的数目。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>返回值

月历控件中当前显示的日历数。 允许的最大日历数量为12。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount)消息, 如 Windows SDK 中所述。

##  <a name="getcalendargridinfo"></a>CMonthCalCtrl:: GetCalendarGridInfo

检索有关当月日历控件的信息。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pmcGridInfo*|弄指向[MCGRIDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo)结构的指针, 该结构接收当前月历控件的相关信息。 调用方负责分配和初始化此结构。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义了变量, `m_monthCalCtrl`该变量用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例使用`GetCalendarGridInfo`方法检索当前月历控件显示的日历日期。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>CMonthCalCtrl:: GetCalID

检索当前月历控件的日历标识符。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>返回值

[日历标识符](/windows/desktop/Intl/calendar-identifiers)常量之一。

### <a name="remarks"></a>备注

日历标识符表示特定于区域的日历, 如公历 (本地化)、日语或回历。 应用程序可以使用具有各种语言支持函数的日历标识符。

此方法发送[MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid)消息, 如 Windows SDK 中所述。

##  <a name="getcolor"></a>CMonthCalCtrl:: GetColor

检索由*nRegion*指定的月历控件区域的颜色。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>参数

*nRegion*<br/>
从中检索颜色的月历控件区域。 有关值的列表, 请参阅[SetColor](#setcolor)的*nRegion*参数。

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/desktop/gdi/colorref)值, 指定与月历控件的部分关联的颜色 (如果成功)。 否则, 此成员函数将返回-1。

##  <a name="getcurrentview"></a>CMonthCalCtrl:: GetCurrentView

检索当前月历控件当前显示的视图。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>返回值

当前视图, 由以下值之一指示:

|值|含义|
|-----------|-------------|
|MCMV_MONTH|每月视图|
|MCMV_YEAR|年度视图|
|MCMV_DECADE|十年视图|
|MCMV_CENTURY|世纪视图|

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义了变量, `m_monthCalCtrl`该变量用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例报表查看当前显示的月历控件。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>CMonthCalCtrl:: GetCurSel

按当前选定的日期检索系统时间。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。 接收当前时间。

*pDateTime*<br/>
指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该结构将接收当前选定的日期信息。 此参数必须是有效的地址, 并且不能为 NULL。

### <a name="return-value"></a>返回值

如果成功, 则为非零值;otherwize 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel)的行为, 如 Windows SDK 中所述。

> [!NOTE]
>  如果设置了样式 MCS_MULTISELECT, 此成员函数将失败。

`GetCurSel`在 MFC 的实现中, 可以`COleDateTime`指定使用情况、 `CTime`用法或`SYSTEMTIME`结构用法。

##  <a name="getfirstdayofweek"></a>CMonthCalCtrl:: GetFirstDayOfWeek

获取要在日历的最左侧列中显示的一周中的第一天。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>参数

*pbLocal*<br/>
指向布尔值的指针。 如果该值为非零, 则该控件的设置与控制面板中的设置不匹配。

### <a name="return-value"></a>返回值

一个整数值, 该值表示一周的第一天。 有关这些整数表示的内容的详细信息, 请参阅 "**备注**"。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek)的行为, 如 Windows SDK 中所述。 一周中的几天以整数表示, 如下所示。

|值|一周中的某一日|
|-----------|---------------------|
|0|星期一|
|1|星期二|
|2|星期三|
|3|星期四|
|4|星期五|
|5|星期六|
|6|星期日|

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl:: SetFirstDayOfWeek](#setfirstdayofweek)的示例。

##  <a name="getmaxselcount"></a>CMonthCalCtrl:: GetMaxSelCount

检索月历控件中可选择的最大天数。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>返回值

一个整数值, 表示可以为控件选择的总天数。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount)的行为, 如 Windows SDK 中所述。 将此成员函数用于具有 MCS_MULTISELECT 样式集的控件。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl:: SetMaxSelCount](#setmaxselcount)的示例。

##  <a name="getmaxtodaywidth"></a>CMonthCalCtrl:: GetMaxTodayWidth

检索当前月历控件的 "今日" 字符串的最大宽度。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>返回值

"今天" 字符串的宽度 (以像素为单位)。

### <a name="example"></a>示例

下面的代码示例定义了变量, `m_monthCalCtrl`该变量用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例演示`GetMaxTodayWidth`方法。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>备注

用户可以通过单击 "今天" 字符串返回到当前日期, 该字符串显示在月历控件的底部。 "今天" 字符串包括标签文本和日期文本。

此方法发送[MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth)消息, 如 Windows SDK 中所述。

##  <a name="getminreqrect"></a>CMonthCalCtrl:: GetMinReqRect

检索在月历控件中显示完整月份所需的最小大小。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>参数

*pRect*<br/>
指向将接收边框信息的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针。 此参数必须是有效的地址, 并且不能为 NULL。

### <a name="return-value"></a>返回值

如果成功, 此成员函数将返回非`lpRect`零值并接收适用的边界信息。 如果不成功, 则成员函数返回0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect)的行为, 如 Windows SDK 中所述。

##  <a name="getmonthdelta"></a>CMonthCalCtrl:: GetMonthDelta

检索月历控件的滚动率。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>返回值

月历控件的滚动率。 滚动速率是指当用户单击滚动按钮一次时, 控件移动其显示的月份数。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta)的行为, 如 Windows SDK 中所述。

##  <a name="getmonthrange"></a>CMonthCalCtrl:: GetMonthRange

检索表示月历控件显示的上限和下限的日期信息。

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
对包含所允许的最小日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*refMaxRange*<br/>
对`COleDateTime` 或`CTime`对象的引用, 该对象包含允许的最大日期。

*pMinRange*<br/>
指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该结构包含位于范围下限的日期。

*pMaxRange*<br/>
指向一个`SYSTEMTIME`结构的指针, 该结构包含范围的最大端的日期。

*dwFlags*<br/>
值, 该值指定要检索的范围限制的范围。 此值必须是下列值之一。

|值|含义|
|-----------|-------------|
|GMR_DAYSTATE|包括仅部分显示的可见范围的前几个月和后几个月。|
|GMR_VISIBLE|仅包括完全显示的月份。|

### <a name="return-value"></a>返回值

一个整数, 表示在第一个和第二个版本中, *refMinRange*和*refMaxRange*所表示的两个限制的范围 (以月为单位), 或者第三个版本中的*pMinRange*和*pMaxRange* 。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange)的行为, 如 Windows SDK 中所述。 在 MFC 的`GetMonthRange`实现中, 可以指定`COleDateTime`用法、 `CTime`用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl:: SetDayState](#setdaystate)的示例。

##  <a name="getrange"></a>CMonthCalCtrl:: GetRange

检索月历控件中设置的当前最小和最大日期。

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
指向`COleDateTime`对象`CTime` 、对象或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该对象包含范围的最低端日期。

*pMaxRange*<br/>
指向`COleDateTime`对象`CTime` 、对象或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该对象包含范围最高端的日期。

### <a name="return-value"></a>返回值

可以为零的 DWORD (未设置任何限制) 或以下值的组合, 这些值用于指定限制信息。

|值|含义|
|-----------|-------------|
|GDTR_MAX|为控件设置了最大限制;*pMaxRange*有效并且包含适用的日期信息。|
|GDTR_MIN|为控件设置最小限制;*pMinRange*有效并且包含适用的日期信息。|

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange)的行为, 如 Windows SDK 中所述。 `GetRange`在 MFC 的实现中, 可以`COleDateTime`指定使用情况、 `CTime`用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>CMonthCalCtrl:: GetSelRange

检索表示用户当前所选日期范围的上限和下限的日期信息。

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
对包含所允许的最小日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*refMaxRange*<br/>
对`COleDateTime` 或`CTime`对象的引用, 该对象包含允许的最大日期。

*pMinRange*<br/>
指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该结构包含位于范围下限的日期。

*pMaxRange*<br/>
指向一个`SYSTEMTIME`结构的指针, 该结构包含范围的最大端的日期。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange)的行为, 如 Windows SDK 中所述。 `GetSelRange`如果应用于不使用 MCS_MULTISELECT 样式的月历控件, 则将失败。

在 MFC 的`GetSelRange`实现中, 可以指定`COleDateTime`用法、 `CTime`用法或`SYSTEMTIME`结构用法。

##  <a name="gettoday"></a>CMonthCalCtrl:: GetToday

检索为月历控件指定为 "今日" 的日期的日期信息。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对指示当前日的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*pDateTime*<br/>
指向将接收日期信息的[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针。 此参数必须是有效的地址, 并且不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday)的行为, 如 Windows SDK 中所述。 `GetToday`在 MFC 的实现中, 可以`COleDateTime`指定使用情况、 `CTime`用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>CMonthCalCtrl:: System.windows.media.visualtreehelper.hittest

确定在指定位置有哪些月历控件 (如果有)。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>参数

*pMCHitTest*<br/>
指向[MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo)结构的指针, 该结构包含月历控件的命中测试点。

### <a name="return-value"></a>返回值

DWORD 值。 等于`MCHITTESTINFO`结构的**uHit**成员。

### <a name="remarks"></a>备注

`HitTest``MCHITTESTINFO`使用结构, 该结构包含有关命中测试的信息。

##  <a name="iscenturyview"></a>CMonthCalCtrl:: IsCenturyView

指示当前月历控件的当前视图是否为 "世纪" 视图。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是世纪视图, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息, 如 Windows SDK 中所述。 如果该消息返回 MCMV_CENTURY, 则此方法返回 TRUE。

##  <a name="isdecadeview"></a>CMonthCalCtrl:: IsDecadeView

指示当前月历控件的当前视图是否为十年视图。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是十年视图, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息, 如 Windows SDK 中所述。 如果该消息返回 MCMV_DECADE, 则此方法返回 TRUE。

##  <a name="ismonthview"></a>CMonthCalCtrl:: IsMonthView

指示当前月历控件的当前视图是否为月份视图。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是月份视图, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息, 如 Windows SDK 中所述。 如果该消息返回 MCMV_MONTH, 则此方法返回 TRUE。

##  <a name="isyearview"></a>CMonthCalCtrl:: IsYearView

指示当前月历控件的当前视图是否为 "年" 视图。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>返回值

如果当前视图为年视图, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)消息, 如 Windows SDK 中所述。 如果该消息返回 MCMV_YEAR, 则此方法返回 TRUE。

##  <a name="setcalendarborder"></a>CMonthCalCtrl:: SetCalendarBorder

设置当前月历控件的边框宽度。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*cxyBorder*|中边框的宽度 (以像素为单位)。|

### <a name="remarks"></a>备注

如果此方法成功, 则边框宽度设置为*cxyBorder*参数。 否则, 边框宽度将重置为当前[主题](/windows/desktop/Controls/visual-styles-overview)指定的默认值, 如果未使用主题, 则为零。

此方法发送[MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义了变量, `m_monthCalCtrl`该变量用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例将月历控件的边框宽度设置为八个像素。 使用[CMonthCalCtrl:: GetCalendarBorder](#getcalendarborder)方法来确定此方法是否成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>CMonthCalCtrl:: SetCalendarBorderDefault

设置当前月历控件的边框的默认宽度。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>备注

边框宽度设置为当前[主题](/windows/desktop/Controls/visual-styles-overview)指定的默认值, 如果未使用主题, 则为零。

此方法发送[MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)消息, 如 Windows SDK 中所述。

##  <a name="setcalid"></a>CMonthCalCtrl:: SetCalID

设置当月日历控件的日历标识符。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*calid*|中[日历标识符](/windows/desktop/Intl/calendar-identifiers)常量之一。|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

日历标识符指定特定于区域的日历, 如公历 (本地化)、日语或回历。 如果计算机上安装了包含日历的区域设置, 请使用方法显示由calid参数指定的`SetCalID`日历。

此方法发送[MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid)消息, 如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义了变量, `m_monthCalCtrl`该变量用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例设置月历控件以显示日语高层时代日历。 仅`SetCalID`当计算机上已安装该日历时, 此方法才会成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>CMonthCalCtrl:: SetCenturyView

设置当前月历控件以显示 "世纪" 视图。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_CENTURY`, 这表示纪元视图。

##  <a name="setcolor"></a>CMonthCalCtrl:: SetColor

设置月历控件的指定区域的颜色。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>参数

*nRegion*<br/>
一个整数值, 指定要设置的月份日历颜色。 此值可以是下列值之一。

|值|含义|
|-----------|-------------|
|MCSC_BACKGROUND|在月之间显示的背景色。|
|MCSC_MONTHBK|月份内显示的背景色。|
|MCSC_TEXT|用于在一个月内显示文本的颜色。|
|MCSC_TITLEBK|日历标题中显示的背景色。|
|MCSC_TITLETEXT|用于显示日历标题内的文本的颜色。|
|MCSC_TRAILINGTEXT|用于显示标题和尾随日期文本的颜色。 标头和尾随日期是当前日历上出现的上个月和后几个月的日期。|

*ref*<br/>
月份日历控件指定部分的新颜色设置的 COLORREF 值。

### <a name="return-value"></a>返回值

如果成功, 则为表示月历控件指定部分的前一种颜色设置的 COLORREF 值。 否则, 此消息将返回-1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>CMonthCalCtrl:: SetCurrentView

设置当前月历控件以显示指定的视图。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*dwNewView*|中指定 "每月"、"年"、"年" 或 "世纪" 视图的下列值之一。<br /><br /> MCMV_MONTH:每月视图<br /><br /> MCMV_YEAR:年度视图<br /><br /> MCMV_DECADE:十年视图<br /><br /> MCMV_CENTURY:世纪视图|

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview)消息, 如 Windows SDK 中所述。

##  <a name="setcursel"></a>CMonthCalCtrl:: SetCurSel

为月历控件设置当前选定的日期。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用, 该对象指示当前选定的月历控件。

*pDateTime*<br/>
指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该结构包含要设置为当前选择的日期。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel)的行为, 如 Windows SDK 中所述。 `SetCurSel`在 MFC 的实现中, 可以`COleDateTime`指定使用情况、 `CTime`用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>CMonthCalCtrl:: SetDayState

设置月历控件中的天数显示。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>参数

*nMonths*<br/>
指示数组中*pStates*指向的元素数的值。

*pStates*<br/>
指向值的[MONTHDAYSTATE](/windows/desktop/Controls/monthdaystate)数组的指针, 这些值定义月历控件在其显示中将如何绘制。 MONTHDAYSTATE 数据类型是一个位域, 其中每个位 (1 到 31) 表示一个月中某一天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>CMonthCalCtrl:: SetDecadeView

将 "当月日历" 控件设置为十年视图。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_DECADE`, 这表示十年视图。

##  <a name="setfirstdayofweek"></a>CMonthCalCtrl:: SetFirstDayOfWeek

设置要在日历的最左侧列中显示的周日期。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>参数

*iDay*<br/>
一个整数值, 表示要将哪一天设置为一周的第一天。 此值必须是某一天数值。 有关日数字的说明, 请参阅[GetFirstDayOfWeek](#getfirstdayofweek) 。

*lpnOld*<br/>
指向一个整数的指针, 该整数指示之前设置的一周中的第一天。

### <a name="return-value"></a>返回值

如果将第一周的第一天的值设置为非 LOCALE_IFIRSTDAYOFWEEK 的值, 则为非零值, 这是 "控制面板" 设置中指示的那一天。 否则, 此函数返回0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>CMonthCalCtrl:: SetMaxSelCount

设置月历控件中可选择的最大天数。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>参数

*nMax*<br/>
将设置为表示可选择的最大天数的值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

设置月历控件的滚动率。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>参数

*iDelta*<br/>
要设置为控件的滚动率的月数。 如果此值为零, 则月份增量将重置为默认值, 即显示在控件中的月数。

### <a name="return-value"></a>返回值

上一个滚动率。 如果之前尚未设置滚动率, 则返回值为0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta)的行为, 如 Windows SDK 中所述。

##  <a name="setmonthview"></a>CMonthCalCtrl:: SetMonthView

设置当前月历控件以显示 "月" 视图。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法将视图设置为 MCMV_MONTH, 这表示 "月" 视图。

### <a name="example"></a>示例

下面的代码示例定义了变量, `m_monthCalCtrl`该变量用于以编程方式访问月历控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

下面的代码示例设置月历控件以显示 "月"、"年"、"年" 和 "世纪" 视图。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>CMonthCalCtrl:: SetRange

设置月历控件允许的最小和最大日期。

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
指向`COleDateTime`对象`CTime` 、对象或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该对象包含范围的最低端日期。

*pMaxRange*<br/>
指向`COleDateTime`对象`SYSTEMTIME` 、对象或结构的指针, 该对象包含范围最高端的日期。 `CTime`

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange)的行为, 如 Windows SDK 中所述。 在 MFC 的`SetRange`实现中, 可以指定`COleDateTime`用法、 `CTime`用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl:: GetRange](#getrange)的示例。

##  <a name="setselrange"></a>CMonthCalCtrl:: SetSelRange

将月历控件的选择设置为给定的日期范围。

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
指向`COleDateTime`对象`CTime` 、对象或[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针, 该对象包含范围的最低端日期。

*pMaxRange*<br/>
指向`COleDateTime`对象`SYSTEMTIME` 、对象或结构的指针, 该对象包含范围最高端的日期。 `CTime`

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange)的行为, 如 Windows SDK 中所述。 在 MFC 的`SetSelRange`实现中, 可以指定`COleDateTime`用法、 `CTime`用法或`SYSTEMTIME`结构用法。

##  <a name="settoday"></a>CMonthCalCtrl:: SetToday

设置当前日期的日历控件。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>参数

*refDateTime*<br/>
对包含当前日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。

*pDateTime*<br/>
在第二个版本中, 是指向包含当前日期信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针。 在第三个版本中, 指向包含当前日期信息的[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday)的行为, 如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl:: GetToday](#gettoday)的示例。

##  <a name="setyearview"></a>CMonthCalCtrl:: SetYearView

将当前月历控件设置为 "年" 视图。

```
BOOL SetYearView();
```

### <a name="return-value"></a>返回值

如果此方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法将视图设置为 MCMV_YEAR, 这表示 "年" 视图。

##  <a name="sizeminreq"></a>CMonthCalCtrl:: SizeMinReq

将月历控件显示为显示一个月的最小大小。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>参数

*bRepaint*<br/>
指定是否要重新绘制控件。 默认情况下, 为 TRUE。 如果为 FALSE, 则不进行重画。

### <a name="return-value"></a>返回值

如果月历控件的大小调整为最小值, 则为非零值;否则为0。

### <a name="remarks"></a>备注

若`SizeMinReq`要成功调用, 将显示一个月的日历的整个月历控件。

##  <a name="sizerecttomin"></a>CMonthCalCtrl:: SizeRectToMin

对于 "当月日历" 控件, 计算可包含符合指定矩形的所有日历的最小矩形。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*lpRect*|中指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针, 该结构定义包含所需日历数的矩形。|

### <a name="return-value"></a>返回值

指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针, 该结构定义一个其大小小于或等于*lpRect*参数所定义的矩形的矩形。

### <a name="remarks"></a>备注

此方法计算*lpRect*参数指定的矩形中可容纳的日历数量, 然后返回可包含该日历数的最小矩形。 实际上, 此方法会缩小指定的矩形, 使其与所需的日历数量完全吻合。

此方法发送[MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin)消息, 如 Windows SDK 中所述。

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl 类](../../mfc/reference/cdatetimectrl-class.md)
