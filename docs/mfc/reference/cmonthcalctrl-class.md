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
ms.openlocfilehash: da9d588811361d3dfd72d44d5b9ced8460d23936
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319745"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl 类

封装月历控件的功能。

## <a name="syntax"></a>语法

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMonthCalCtrl：cmonthCalCtrl](#cmonthcalctrl)|构造 `CMonthCalCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMonthCalctrl：：创建](#create)|创建月历控件并将其附加到`CMonthCalCtrl`对象。|
|[CMonthCalctrl：：获取日历边框](#getcalendarborder)|检索当前月日历控件的边框的宽度。|
|[CMonthCalctrl：：获取日历计数](#getcalendarcount)|检索当前月份日历控件中显示的日历数。|
|[CMonthCalctrl：：获取日历网格信息](#getcalendargridinfo)|检索有关当月日历控件的信息。|
|[CMonthCalctrl：：GetCalID](#getcalid)|检索当月日历控件的日历标识符。|
|[CMonthCalctrl：获取颜色](#getcolor)|获取月份日历控件的指定区域的颜色。|
|[CMonthCalctrl：：获取电流视图](#getcurrentview)|检索当前由当前月份日历控件显示的视图。|
|[CMonthCalctrl：：获取CurSel](#getcursel)|检索当前选择的日期指示的系统时间。|
|[CmonthCalctrl：获取第一天周](#getfirstdayofweek)|获取要显示在日历最左侧列中的一周的第一天。|
|[CMonthCalctrl：：获取MaxSelCount](#getmaxselcount)|检索可在月份日历控件中选择的当前最大天数。|
|[CMonthCalctrl：：获取今天最大宽度](#getmaxtodaywidth)|检索当前月份日历控件的"今天"字符串的最大宽度。|
|[CMonthCalctrl：：获取MinReqrect](#getminreqrect)|检索在月份日历控件中显示完整月份所需的最小大小。|
|[CMonthCalctrl：：获取月德尔塔](#getmonthdelta)|检索一个月日历控件的滚动速率。|
|[CMonthCalctrl：获取月航程](#getmonthrange)|检索表示月历控件显示的上限和低点的日期信息。|
|[CMonthCalctrl：获取范围](#getrange)|检索在月份日历控件中设置的当前最小和最大日期。|
|[CMonthCalctrl：：GetSelRange](#getselrange)|检索表示用户当前选择的日期范围的上限和下限的日期信息。|
|[CMonthCalctrl：今天获取](#gettoday)|检索指定为"今天"的日期的日期信息，用于一个月的日历控件。|
|[CMonthCalctrl：hitTest](#hittest)|确定月历控件的哪个部分位于屏幕上的给定点。|
|[CMonthCalctrl：Is世纪视图](#iscenturyview)|指示当前月历控件的视图是否是世纪视图。|
|[CMonthCalctrl：：是十年视图](#isdecadeview)|指示当前月日历控件的当前视图是否是十年视图。|
|[CMonthCalctrl：：IsMonthView](#ismonthview)|指示当前月日历控件的当前视图是否是月视图。|
|[CMonthCalctrl：isYearView](#isyearview)|指示当前月日历控件的当前视图是否是年份视图。|
|[CMonthCalctrl：：设置日历边框](#setcalendarborder)|设置当前月日历控件的边框的宽度。|
|[CMonthCalctrl：：设置日历边框默认](#setcalendarborderdefault)|设置当前月日历控件边框的默认宽度。|
|[CMonthCalctrl：：SetCalID](#setcalid)|设置当月日历控件的日历标识符。|
|[CMonthCalctrl：：设置世纪视图](#setcenturyview)|设置当前月历控件以显示世纪视图。|
|[CMonthCalctrl：：设置颜色](#setcolor)|设置月历控件的指定区域的颜色。|
|[CMonthCalctrl：：设置电流视图](#setcurrentview)|设置当前月历控件以显示指定的视图。|
|[CMonthCalctrl：：SetCurSel](#setcursel)|设置月份日历控件的当前选定日期。|
|[CMonthCalctrl：setDayState](#setdaystate)|设置一个月日历控件中的天数的显示。|
|[CMonthCalctrl：：设置十年视图](#setdecadeview)|将当前月历控件设置到十年视图。|
|[CmonthCalctrl：：每周第一天](#setfirstdayofweek)|将要显示在日历最左侧列中的星期几。|
|[CMonthCalctrl：：SetMaxSelCount](#setmaxselcount)|设置可在月份日历控件中选择的最大天数。|
|[CMonthCalctrl：：设置月德尔塔](#setmonthdelta)|设置月历控件的滚动速率。|
|[CMonthCalctrl：：设置月景](#setmonthview)|设置当前月历控件以显示月视图。|
|[CMonthCalctrl：：SetRange](#setrange)|设置月历控件的最小和最大允许日期。|
|[CMonthCalctrl：：SetSelRange](#setselrange)|将月份日历控件的选择设置为给定日期范围。|
|[CMonthCalctrl：：今天设置](#settoday)|设置当天的日历控件。|
|[CMonthCalctrl：：SetYearView](#setyearview)|将当前月日历控件设置为年视图。|
|[CMonthCalctrl：：SizeMinReq](#sizeminreq)|将月历控件重新绘制为其最小一个月大小。|
|[CmonthCalctrl：：大小雷克特明](#sizerecttomin)|对于当前月历控件，计算可以包含适合指定矩形的所有日历的最小矩形。|

## <a name="remarks"></a>备注

月历控件为用户提供了一个简单的日历界面，用户可以从中选择日期。 用户可以通过以下更改显示：

- 逐月向后滚动和向前滚动。

- 单击"今天"文本以显示当前天（如果未使用MCS_NOTODAY样式）。

- 从弹出式菜单中选择一个月或一年。

您可以在创建对象时对对象应用各种样式来自定义月历控件。 这些样式在 Windows SDK 中的[月历控制样式](/windows/win32/Controls/month-calendar-control-styles)中描述。

月历控件可以显示超过一个月，并且可以通过粗体日期来指示特殊日期（如假日）。

有关使用月历控件的详细信息，请参阅[使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>要求

**标题：** afxdtctl.h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl：cmonthCalCtrl

构造 `CMonthCalCtrl` 对象。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>备注

构造对象后`Create`必须调用。

## <a name="cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalctrl：：创建

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
指定应用于月历控件的 Windows 样式的组合。 有关样式的详细信息，请参阅 Windows SDK 中的[月日历控件样式](/windows/win32/Controls/month-calendar-control-styles)。

*矩形*<br/>
对[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用。 包含月历控件的位置和大小。

*pt*<br/>
对标识月历控件位置的[POINT](/previous-versions/dd162805\(v=vs.85\))结构的引用。

*pparentwnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是月历控件的父窗口。 值不得为 NULL。

*nID*<br/>
指定月历控件的控制 ID。

### <a name="return-value"></a>返回值

初始化成功时非零;否则 0。

### <a name="remarks"></a>备注

通过两个步骤创建月历控件：

1. 调用[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)构造`CMonthCalCtrl`对象。

1. 调用此成员函数，该函数创建月历控件并将其附加到`CMonthCalCtrl`对象。

调用`Create`时调用 ，将初始化公共控件。 调用的版本`Create`决定了其大小：

- 要让 MFC 自动将控件大小调整为一个月，请调用使用*pt*参数的重写。

- 要自行调整控件的大小，请调用使用*rect*参数的此函数的重写。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalctrl：：获取日历边框

检索当前月日历控件的边框的宽度。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>返回值

控件边框的宽度（以像素为单位）。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder)消息，这在 Windows SDK 中介绍。

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalctrl：：获取日历计数

检索当前月份日历控件中显示的日历数。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>返回值

当前显示在月份日历控件中的日历数。 允许的最大日历数为 12。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount)消息，这在 Windows SDK 中介绍。

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalctrl：：获取日历网格信息

检索有关当月日历控件的信息。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pmcGrid信息*|[出]指向接收有关当月日历控件信息的[MCGRIDINFO](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo)结构的指针。 调用方负责分配和初始化此结构。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_monthCalCtrl`月份日历控件的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

以下代码示例使用 方法`GetCalendarGridInfo`检索当前月份日历控件显示的日历日期。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalctrl：：GetCalID

检索当月日历控件的日历标识符。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>返回值

[日历标识符](/windows/win32/Intl/calendar-identifiers)常量之一。

### <a name="remarks"></a>备注

日历标识符表示特定于区域的日历，例如公历（本地化）、日语或 Hijri 日历。 您的应用程序可以使用具有各种语言支持功能的日历标识符。

此方法发送[MCM_GETCALID](/windows/win32/Controls/mcm-getcalid)消息，这在 Windows SDK 中介绍。

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalctrl：获取颜色

检索*n 区域*指定的月历控件的区域的颜色。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>参数

*n区域*<br/>
从中检索颜色的月历控件的区域。 有关值列表，请参阅[SetColor](#setcolor)的*n 区域*参数。

### <a name="return-value"></a>返回值

指定与月历控件部分关联的颜色（如果成功）的[COLORREF](/windows/win32/gdi/colorref)值。 否则，此成员函数返回 -1。

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalctrl：：获取电流视图

检索当前由当前月份日历控件显示的视图。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>返回值

当前视图，由以下值之一指示：

|“值”|含义|
|-----------|-------------|
|MCMV_MONTH|每月视图|
|MCMV_YEAR|年度视图|
|MCMV_DECADE|十年视图|
|MCMV_CENTURY|世纪景观|

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_monthCalCtrl`月份日历控件的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

显示以下查看月历控件的代码示例报告。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalctrl：：获取CurSel

检索当前选择的日期指示的系统时间。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>参数

*参考日期时间*<br/>
对[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。 接收当前时间。

*pDateTime*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，该结构将接收当前选择的日期信息。 此参数必须是有效地址，不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，则非零;其他w化0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)的行为，如 Windows SDK 中所述。

> [!NOTE]
> 如果设置了样式MCS_MULTISELECT，则此成员函数将失败。

在 MFC 的`GetCurSel`实现 中，可以`COleDateTime`指定用法`CTime`、用法或`SYSTEMTIME`结构用法。

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CmonthCalctrl：获取第一天周

获取要显示在日历最左侧列中的一周的第一天。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>参数

*pb 本地*<br/>
指向 BOOL 值的指针。 如果值为非零，则控件的设置与控制面板中的设置不匹配。

### <a name="return-value"></a>返回值

表示一周第一天的整数值。 有关这些整数代表的内容的详细信息，请参阅**备注**。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)的行为，如 Windows SDK 中所述。 星期的天数表示为整数，如下所示。

|“值”|星期一|
|-----------|---------------------|
|0|星期一|
|1|星期二|
|2|星期三|
|3|星期四|
|4|星期五|
|5|星期六|
|6|星期日|

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl 的示例：：设置第一天周](#setfirstdayofweek)。

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalctrl：：获取MaxSelCount

检索可在月份日历控件中选择的当前最大天数。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>返回值

表示可以为控件选择的天数的总天数的整数值。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)的行为，如 Windows SDK 中所述。 对于具有MCS_MULTISELECT样式集的控件，使用此成员函数。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl 的示例：：SetMaxSelCount](#setmaxselcount)。

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalctrl：：获取今天最大宽度

检索当前月份日历控件的"今天"字符串的最大宽度。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>返回值

"今天"字符串的宽度（以像素为单位）。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_monthCalCtrl`月份日历控件的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

以下代码示例演示了该方法`GetMaxTodayWidth`。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>备注

用户可以通过单击"今天"字符串返回到当前日期，该字符串显示在月历控件的底部。 "今天"字符串包括标签文本和日期文本。

此方法发送[MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth)消息，这在 Windows SDK 中介绍。

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalctrl：：获取MinReqrect

检索在月份日历控件中显示完整月份所需的最小大小。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>参数

*普雷克*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构将接收边界矩形信息。 此参数必须是有效地址，不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，此成员函数将返回非零`lpRect`并接收适用的边界信息。 如果不成功，成员函数返回 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)的行为，如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalctrl：：获取月德尔塔

检索一个月日历控件的滚动速率。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>返回值

月历控件的滚动速率。 滚动速率是当用户单击滚动按钮一次时控件移动其显示的月数。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)的行为，如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalctrl：获取月航程

检索表示月历控件显示的上限和低点的日期信息。

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
对包含允许的最小日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*refMaxRange*<br/>
对包含允许的最大`COleDateTime`日期`CTime`的 或 对象的引用。

*普明朗*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含范围最底层的日期。

*pMaxRange*<br/>
指向`SYSTEMTIME`包含范围最高端日期的结构的指针。

dwFlags**<br/>
指定要检索的范围限制的范围的值。 此值必须是以下值之一。

|“值”|含义|
|-----------|-------------|
|GMR_DAYSTATE|包括仅部分显示的可见范围的前几个月和后几个月。|
|GMR_VISIBLE|仅包括完全显示的月份。|

### <a name="return-value"></a>返回值

以月表示范围的整数，由第一和第二版本中*refMinRange*和*refMaxRange*指示的两个限制，或第三版本中*的 pMinRange*和*pMaxRange*表示。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)的行为，如 Windows SDK 中所述。 在 MFC 的`GetMonthRange`实现 中，`COleDateTime`可以指定用`CTime`法、用法`SYSTEMTIME`或结构用法。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl 的示例：：SetDayState](#setdaystate)。

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalctrl：获取范围

检索在月份日历控件中设置的当前最小和最大日期。

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

*普明朗*<br/>
指向`COleDateTime`对象、`CTime`对象或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含范围最底层的日期。

*pMaxRange*<br/>
指向`COleDateTime`对象、`CTime`对象或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含范围最高端的日期。

### <a name="return-value"></a>返回值

可以为零（不设置限制）的 DWORD 或指定限制信息的以下值的组合。

|“值”|含义|
|-----------|-------------|
|GDTR_MAX|为控件设置了最大限制;*pMaxRange*有效，包含适用日期信息。|
|GDTR_MIN|为控件设置了最小限制;*pMinRange*有效，包含适用日期信息。|

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETRANGE](/windows/win32/Controls/mcm-getrange)的行为，如 Windows SDK 中所述。 在 MFC 的`GetRange`实现 中，可以`COleDateTime`指定用法`CTime`、用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalctrl：：GetSelRange

检索表示用户当前选择的日期范围的上限和下限的日期信息。

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
对包含允许的最小日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*refMaxRange*<br/>
对包含允许的最大`COleDateTime`日期`CTime`的 或 对象的引用。

*普明朗*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含范围最底层的日期。

*pMaxRange*<br/>
指向`SYSTEMTIME`包含范围最高端日期的结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)的行为，如 Windows SDK 中所述。 `GetSelRange`如果应用于不使用MCS_MULTISELECT样式的月历控件，将失败。

在 MFC 的`GetSelRange`实现 中，`COleDateTime`可以指定用`CTime`法、用法`SYSTEMTIME`或结构用法。

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalctrl：今天获取

检索指定为"今天"的日期的日期信息，用于一个月的日历控件。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>参数

*参考日期时间*<br/>
对指示当前日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*pDateTime*<br/>
指向将接收日期信息的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针。 此参数必须是有效地址，不能为 NULL。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)的行为，如 Windows SDK 中所述。 在 MFC 的`GetToday`实现 中，可以`COleDateTime`指定用法`CTime`、用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalctrl：hitTest

确定哪个月历控件（如果有）处于指定位置。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>参数

*pMCHitTest*<br/>
指向[MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo)结构的指针，其中包含月份日历控件的热门测试点。

### <a name="return-value"></a>返回值

DWORD 值。 等于`MCHITTESTINFO`结构的**uHit**成员。

### <a name="remarks"></a>备注

`HitTest`使用包含`MCHITTESTINFO`命中测试信息的结构。

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalctrl：Is世纪视图

指示当前月历控件的视图是否是世纪视图。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是世纪视图，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息，这在 Windows SDK 中介绍。 如果该消息返回MCMV_CENTURY，则此方法返回 TRUE。

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalctrl：：是十年视图

指示当前月日历控件的当前视图是否是十年视图。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是十年视图，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息，这在 Windows SDK 中介绍。 如果该消息返回MCMV_DECADE，则此方法返回 TRUE。

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalctrl：：IsMonthView

指示当前月日历控件的当前视图是否是月视图。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是月视图，则为 TRUE;如果当前视图为"月视图"，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息，这在 Windows SDK 中介绍。 如果该消息返回MCMV_MONTH，则此方法返回 TRUE。

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalctrl：isYearView

指示当前月日历控件的当前视图是否是年份视图。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>返回值

如果当前视图是年份视图，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息，这在 Windows SDK 中介绍。 如果该消息返回MCMV_YEAR，则此方法返回 TRUE。

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalctrl：：设置日历边框

设置当前月日历控件的边框的宽度。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*cxy 边界*|[在]边框的宽度（以像素为单位）。|

### <a name="remarks"></a>备注

如果此方法成功，边框宽度将设置为*cxyBorder*参数。 否则，边框宽度将重置为当前[主题](/windows/win32/Controls/visual-styles-overview)指定的默认值，如果未使用主题，则将重置为零。

此方法发送[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_monthCalCtrl`月份日历控件的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

以下代码示例将月历控件的边框宽度设置为 8 像素。 使用[CMonthCalCtrl：：GetCalendarBorder](#getcalendarborder)方法确定此方法是否成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalctrl：：设置日历边框默认

设置当前月日历控件边框的默认宽度。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>备注

边框宽度设置为当前[主题](/windows/win32/Controls/visual-styles-overview)指定的默认值，如果未使用主题，则为零。

此方法发送[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)消息，这在 Windows SDK 中介绍。

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalctrl：：SetCalID

设置当月日历控件的日历标识符。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*卡利德*|[在][日历标识符](/windows/win32/Intl/calendar-identifiers)常量之一。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

日历标识符指定特定于区域的日历，例如公历（本地化）、日语或 Hijri 日历。 如果计算机上`SetCalID`安装了包含日历的区域设置，则使用 方法显示由*校准*参数指定的日历。

此方法发送[MCM_SETCALID](/windows/win32/Controls/mcm-setcalid)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_monthCalCtrl`月份日历控件的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

以下代码示例设置月历控件以显示日本天皇时代日历。 仅当`SetCalID`计算机上安装了该日历时，该方法才会成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalctrl：：设置世纪视图

设置当前月历控件以显示世纪视图。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl：：SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_CENTURY`，表示世纪视图。

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalctrl：：设置颜色

设置月历控件的指定区域的颜色。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>参数

*n区域*<br/>
指定要设置的月历颜色的整数值。 此值可以是以下值之一。

|“值”|含义|
|-----------|-------------|
|MCSC_BACKGROUND|月份之间显示的背景颜色。|
|MCSC_MONTHBK|月份内显示的背景颜色。|
|MCSC_TEXT|用于在一个月内显示文本的颜色。|
|MCSC_TITLEBK|日历标题中显示的背景颜色。|
|MCSC_TITLETEXT|用于在日历标题中显示文本的颜色。|
|MCSC_TRAILINGTEXT|用于显示标题和尾随日文本的颜色。 标题和尾随日是当前日历上显示的前一个月和后几个月的天数。|

*ref*<br/>
月历控件指定部分的新颜色设置的 COLORREF 值。

### <a name="return-value"></a>返回值

COLORREF 值，表示月份日历控件指定部分的上一个颜色设置（如果成功）。 否则，此消息返回 -1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalctrl：：设置电流视图

设置当前月历控件以显示指定的视图。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwNewView*|[在]指定每月、年度、十年或世纪视图的以下值之一。<br /><br /> MCMV_MONTH：每月视图<br /><br /> MCMV_YEAR：年度视图<br /><br /> MCMV_DECADE：十年视图<br /><br /> MCMV_CENTURY：世纪景观|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview)消息，这在 Windows SDK 中介绍。

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalctrl：：SetCurSel

设置月份日历控件的当前选定日期。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>参数

*参考日期时间*<br/>
对指示当前选择的月份日历控件的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*pDateTime*<br/>
指向包含要设置为当前选择的日期的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)的行为，如 Windows SDK 中所述。 在 MFC 的`SetCurSel`实现 中，可以`COleDateTime`指定用法`CTime`、用法或`SYSTEMTIME`结构用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalctrl：setDayState

设置一个月日历控件中的天数的显示。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>参数

*nmonths*<br/>
指示*pA 指向*的数组中的元素数的值。

*p国家*<br/>
指向["月日状态](/windows/win32/Controls/monthdaystate)"值数组的指针，用于定义月历控件每天在显示中如何绘制。 MonthDAYSTATE 数据类型是位字段，其中每个位（1 到 31）表示一个月内一天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalctrl：：设置十年视图

将当前月历控件设置到十年视图。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl：：SetCurrentView](#setcurrentview)方法将视图设置为`MCMV_DECADE`，表示十年视图。

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CmonthCalctrl：：每周第一天

将要显示在日历最左侧列中的星期几。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>参数

*iDay*<br/>
表示将哪一天设置为星期的第一天的整数值。 此值必须是天数之一。 有关日数的说明，请参阅获取第一[天](#getfirstdayofweek)。

*lpnOld*<br/>
指向一个整数的指针，指示之前设置的一周的第一天。

### <a name="return-value"></a>返回值

如果星期的前一天设置为LOCALE_IFIRSTDAYOFWEEK的值（控制面板设置中指示的当天）以外的值，则非零。 否则，此函数返回 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalctrl：：SetMaxSelCount

设置可在月份日历控件中选择的最大天数。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>参数

*nMax*<br/>
将设置为表示可选择天数的最大值。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalctrl：：设置月德尔塔

设置月历控件的滚动速率。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>参数

*iDelta*<br/>
要设置为控件滚动速率的月数。 如果此值为零，则月份增量将重置为默认值，即控件中显示的月数。

### <a name="return-value"></a>返回值

以前的滚动速率。 如果以前未设置滚动速率，则返回值为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta)的行为，如 Windows SDK 中所述。

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalctrl：：设置月景

设置当前月历控件以显示月视图。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl：：SetCurrentView](#setcurrentview)方法将视图设置为MCMV_MONTH，该视图表示月视图。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问`m_monthCalCtrl`月份日历控件的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>示例

以下代码示例将月历控件设置以显示月份、年份、十年和世纪视图。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalctrl：：SetRange

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

*普明朗*<br/>
指向`COleDateTime`对象、`CTime`对象或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含范围最底层的日期。

*pMaxRange*<br/>
指向`COleDateTime`对象、`CTime`对象或`SYSTEMTIME`结构的指针，其中包含范围最高端的日期。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)的行为，如 Windows SDK 中所述。 在 MFC 的`SetRange`实现 中，`COleDateTime`可以指定用`CTime`法、用法`SYSTEMTIME`或结构用法。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl 的示例：：获取范围](#getrange)。

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalctrl：：SetSelRange

将月份日历控件的选择设置为给定日期范围。

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

*普明朗*<br/>
指向`COleDateTime`对象、`CTime`对象或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含范围最底层的日期。

*pMaxRange*<br/>
指向`COleDateTime`对象、`CTime`对象或`SYSTEMTIME`结构的指针，其中包含范围最高端的日期。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange)，如 Windows SDK 中所述。 在 MFC 的`SetSelRange`实现 中，`COleDateTime`可以指定用`CTime`法、用法`SYSTEMTIME`或结构用法。

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalctrl：：今天设置

设置当天的日历控件。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>参数

*参考日期时间*<br/>
对包含当前日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。

*pDateTime*<br/>
在第二个版本中，指向包含当前日期信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针。 在第三个版本中，指向包含当前日期信息的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CMonthCalCtrl 的示例：：获取今天](#gettoday)。

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalctrl：：SetYearView

将当前月日历控件设置为年视图。

```
BOOL SetYearView();
```

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法使用[CMonthCalCtrl：：SetCurrentView](#setcurrentview)方法将视图设置为MCMV_YEAR，该视图表示年度视图。

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalctrl：：SizeMinReq

将月历控件显示为显示一个月的最小大小。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>参数

*bRepaint*<br/>
指定是否要重新绘制控件。 默认情况下，TRUE。 如果 FALSE，则不进行重新绘制。

### <a name="return-value"></a>返回值

如果月历控件的大小调整到其最小值，则非零;否则 0。

### <a name="remarks"></a>备注

呼叫`SizeMinReq`成功显示一个月日历的整个月历控件。

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CmonthCalctrl：：大小雷克特明

对于当前月历控件，计算可以包含适合指定矩形的所有日历的最小矩形。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*lpRect*|[在]指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构定义包含所需日历数的矩形。|

### <a name="return-value"></a>返回值

指向[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构定义大小小于或等于*lpRect*参数定义的矩形的矩形。

### <a name="remarks"></a>备注

此方法计算*lpRect*参数指定的矩形中可以容纳的日历数，然后返回可以包含该日历数的最小矩形。 实际上，此方法收缩指定的矩形以完全适合所需的日历数。

此方法发送[MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin)消息，这在 Windows SDK 中介绍。

## <a name="see-also"></a>另请参阅

[MFC 样品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl 类](../../mfc/reference/cdatetimectrl-class.md)
