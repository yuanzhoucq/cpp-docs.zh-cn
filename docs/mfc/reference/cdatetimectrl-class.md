---
title: CDateTimeCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: 8c69473ab813c2fa692044fddc406a74a5aeb197
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253512"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl 类

封装日期和时间选取器控件功能。

## <a name="syntax"></a>语法

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|构造 `CDateTimeCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|关闭当前的日期和时间选取器控件。|
|[CDateTimeCtrl::Create](#create)|创建日期和时间选取器控件，并将其附加到`CDateTimeCtrl`对象。|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|检索当前日期和时间选取器控件有关的信息。|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|返回显示的当前日期或时间所需的日期和时间选取器控件的理想大小。|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|检索日期和时间选取器控件中的月日历的指定部分的颜色。|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|检索`CMonthCalCtrl`与日期和时间选取器控件相关联的对象。|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|检索当前使用的日期和时间选取器控件的子月历控件的字体。|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|获取当前日期和时间选取器控件的样式。|
|[CDateTimeCtrl::GetRange](#getrange)|检索当前最小值和最大允许将日期和时间选取器控件的系统时间。|
|[CDateTimeCtrl::GetTime](#gettime)|从日期和时间选取器控件检索当前所选的时间，并将其放入指定`SYSTEMTIME`结构。|
|[CDateTimeCtrl::SetFormat](#setformat)|将根据给定的格式字符串的日期和时间选取器控件的显示设置。|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|设置日期和时间选取器控件中的月日历的指定部分的颜色。|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|设置日期和时间选取器控件的子月历控件将使用的字体。|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|将当前日期和时间选取器控件的样式设置。|
|[CDateTimeCtrl::SetRange](#setrange)|设置日期和时间选取器控件的最小值和最大允许的系统时间。|
|[CDateTimeCtrl::SetTime](#settime)|在日期和时间选取器控件中设置的时间。|

## <a name="remarks"></a>备注

日期和时间选取器控件 （DTP 控件） 提供了简单的界面来交换与用户的日期和时间信息。 此接口包含的字段，其中每个显示存储在控件中的日期和时间信息的一部分。 用户可以更改存储在控件中的更改的给定字段中的字符串内容的信息。 用户可以移动域之间使用鼠标或键盘。

可以在创建时对该对象应用多种样式自定义日期和时间选取器控件。 请参阅[日期和时间选取器控件样式](/windows/desktop/Controls/date-and-time-picker-control-styles)适用于特定于日期和时间选取器控件的样式有关的详细信息的 Windows SDK 中。 可以设置使用格式样式在 DTP 控件的显示格式。 在"格式样式"下，Windows SDK 主题中介绍这些格式样式[日期和时间选取器控件样式](/windows/desktop/Controls/date-and-time-picker-control-styles)。

日期和时间选取器控件还使用通知和中所述的回调[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>要求

**标头：** afxdtctl.h

##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl

构造 `CDateTimeCtrl` 对象。

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>  CDateTimeCtrl::CloseMonthCal

关闭当前的日期和时间选取器控件。

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>备注

此方法将发送[DTM_CLOSEMONTHCAL](/windows/desktop/Controls/dtm-closemonthcal)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， *m_dateTimeCtrl*，即用于以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例将关闭当前的日期和时间选取器控件的下拉日历。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>  CDateTimeCtrl::Create

创建日期和时间选取器控件，并将其附加到`CDateTimeCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定日期时间控件样式的组合。 请参阅[日期和时间选取器控件样式](/windows/desktop/Controls/date-and-time-picker-control-styles)有关日期和时间选取器样式的详细信息 Windows SDK 中。

*rect*<br/>
对引用[RECT](/previous-versions/dd162897\(v=vs.85\))结构，它是位置和日期和时间选取器控件的大小。

*pParentWnd*<br/>
一个指向[CWnd](../../mfc/reference/cwnd-class.md)是日期和时间选取器控件的父窗口的对象。 它不能为 NULL。

*nID*<br/>
指定日期和时间选取器控件的控件 id。

### <a name="return-value"></a>返回值

如果创建成功，则非零值否则为 0。

### <a name="remarks"></a>备注

##### <a name="to-create-a-date-and-time-picker-control"></a>若要创建的日期和时间选取器控件

1. 调用[CDateTimeCtrl](#cdatetimectrl)构造`CDateTimeCtrl`对象。

1. 调用此成员函数，将创建 Windows 日期和时间选取器控件并将其附加到`CDateTimeCtrl`对象。

当您调用`Create`，公共控件进行初始化。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>  CDateTimeCtrl::GetDateTimePickerInfo

检索当前日期和时间选取器控件有关的信息。

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*pDateTimePickerInfo*|[out]一个指向[DATETIMEPICKERINFO](/windows/desktop/api/commctrl/ns-commctrl-tagdatetimepickerinfo)结构，它接收当前日期和时间选取器控件的说明。<br /><br /> 调用方负责分配此结构。 但是，此方法初始化*cbSize*结构中的成员。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法将发送[DTM_GETDATETIMEPICKERINFO](/windows/desktop/Controls/dtm-getdatetimepickerinfo)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， *m_dateTimeCtrl*，即用于以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例指示是否已成功检索有关当前的日期和时间选取器控件的信息。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>  CDateTimeCtrl::GetMonthCalColor

检索日期和时间选取器控件中的月日历的指定部分的颜色。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>参数

*iColor*<br/>
**Int**值，该值指定要检索的月日历的颜色区域。 值的列表，请参阅*iColor*参数[SetMonthCalColor](#setmonthcalcolor)。

### <a name="return-value"></a>返回值

一个 COLORREF 值，该值表示如果成功，则将 month calendar 控件的指定部分的颜色设置。 如果不成功，则该函数返回-1。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_GETMCCOLOR](/windows/desktop/Controls/dtm-getmccolor)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>  CDateTimeCtrl::GetMonthCalCtrl

检索`CMonthCalCtrl`与日期和时间选取器控件相关联的对象。

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>返回值

一个指向[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)对象，或者如果不成功，或如果窗口不可见，则为 NULL。

### <a name="remarks"></a>备注

日期和时间选取器控件创建子月历控件，当用户单击下拉箭头。 当`CMonthCalCtrl`不再需要对象时，它被销毁，因此你的应用程序必须不依赖于存储对象，表示日期时间选取器控件的子月的日历。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont

获取当前使用的日期和时间选取器控件的月历控件的字体。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>返回值

一个指向[CFont](../../mfc/reference/cfont-class.md)对象，或者如果不成功，则为 NULL。

### <a name="remarks"></a>备注

`CFont`返回值指向的对象是临时对象并在下一步的空闲处理期间被销毁。

##  <a name="getmonthcalstyle"></a>  CDateTimeCtrl::GetMonthCalStyle

获取与当前的日期和时间选取器控件相关联的下拉列表月日历控件的样式。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>返回值

样式的日期和时间选取器控件样式的下拉月历控件，这是一个按位组合 （或者）。 有关详细信息，请参阅[个月日历控件样式](/windows/desktop/Controls/month-calendar-control-styles)。

### <a name="remarks"></a>备注

此方法将发送[DTM_GETMCSTYLE](/windows/desktop/Controls/dtm-getmcstyle)消息，Windows SDK 中所述。

##  <a name="getrange"></a>  CDateTimeCtrl::GetRange

检索当前最小值和最大允许将日期和时间选取器控件的系统时间。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>参数

*pMinRange*<br/>
一个指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含在允许的最早时间`CDateTimeCtrl`对象。

*pMaxRange*<br/>
一个指向`COleDateTime`对象或`CTime`对象，其中包含在允许的最新时间`CDateTimeCtrl`对象。

### <a name="return-value"></a>返回值

包含这些标志指示的范围设置的 DWORD 值。 如果

`return value & GDTR_MAX` == 0

然后第二个参数是有效的。 同样，如果

`return value & GDTR_MIN` == 0

然后第一个参数是有效的。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_GETRANGE](/windows/desktop/Controls/dtm-getrange)，如 Windows SDK 中所述。 在 MFC 的实现中，您可以指定`COleDateTime`或`CTime`用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>  CDateTimeCtrl::GetTime

从日期和时间选取器控件检索当前所选的时间，并将其放入指定`SYSTEMTIME`结构。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>参数

*timeDest*<br/>
在第一个版本中，对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)将收到系统时间信息的对象。 在第二个版本中，对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)将收到系统时间信息的对象。

*pTimeDest*<br/>
一个指向[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，以接收系统时间信息。 不能为 NULL。

### <a name="return-value"></a>返回值

在第一个版本中，如果时间成功写入到非零`COleDateTime`对象; 否则为 0。 在第二个和第三个版本中，DWORD 值等于*dwFlag*成员中设置[NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)结构。 请参阅**备注**部分获取详细信息。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_GETSYSTEMTIME](/windows/desktop/Controls/dtm-getsystemtime)，如 Windows SDK 中所述。 中的 MFC 实现`GetTime`，可以使用`COleDateTime`或`CTime`类，也可以使用`SYSTEMTIME`结构，用于存储的时间信息。

DWORD 的返回值在第二个和第三个版本中，更高版本，指示是否将日期和时间选取器控件设置为"无日期"状态，如下所示[NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)结构成员*dwFlags*. 如果返回的值等于 GDT_NONE，该控件设置为"无日期"状态，并使用 DTS_SHOWNONE 样式。 如果返回的值等于 GDT_VALID，已成功在目标位置中存储的系统时间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize

返回显示的当前日期或时间所需的日期和时间选取器控件的理想大小。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*psize*|[out]指向[大小](/windows/desktop/api/windef/ns-windef-tagsize)结构，其中包含该控件的理想大小。|

### <a name="return-value"></a>返回值

返回值始终为 TRUE。

### <a name="remarks"></a>备注

此方法将发送[DTM_GETIDEALSIZE](/windows/desktop/Controls/dtm-getidealsize)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， *m_dateTimeCtrl*，即用于以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例检索要显示的日期和时间选取器控件的理想大小。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>  CDateTimeCtrl::SetFormat

将根据给定的格式字符串的日期和时间选取器控件的显示设置。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>参数

*pstrFormat*<br/>
指向一个定义所需的显示的零终止格式字符串的指针。 此参数设置为 NULL 将控件重置为当前样式的默认格式字符串。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

> [!NOTE]
>  用户输入不确定成功或失败的此调用。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_SETFORMAT](/windows/desktop/Controls/dtm-setformat)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>  CDateTimeCtrl::SetMonthCalColor

设置日期和时间选取器控件中的月日历的指定部分的颜色。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>参数

*iColor*<br/>
**int**值，该值指定要设置的月份的日历控件的区域。 此值可以是以下值之一。

|“值”|含义|
|-----------|-------------|
|MCSC_BACKGROUND|设置显示不同的月份的背景色。|
|MCSC_MONTHBK|设置显示在一个月中的背景色。|
|MCSC_TEXT|设置用于在一个月内显示文本的颜色。|
|MCSC_TITLEBK|设置显示在日历的标题的背景色。|
|MCSC_TITLETEXT|设置用于显示日历的标题中的文本的颜色。|
|MCSC_TRAILINGTEXT|设置用于显示标头和尾部天文本的颜色。 标头和后续日期是当前日历会显示以前及以后月份的天数。|

*ref*<br/>
COLORREF 值，表示将会为月日历的指定区域设置的颜色。

### <a name="return-value"></a>返回值

COLORREF 值表示的指定部分的月历控件如果成功，则以前的颜色设置。 否则，消息将返回-1。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_SETMCCOLOR](/windows/desktop/Controls/dtm-setmccolor)，如 Windows SDK 中所述。

### <a name="example"></a>示例

  有关示例，请参阅[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)。

##  <a name="setmonthcalfont"></a>  CDateTimeCtrl::SetMonthCalFont

设置日期和时间选取器控件的子月历控件将使用的字体。

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*hFont*<br/>
将设置该字体的句柄。

*bRedraw*<br/>
指定是否应立即绘该控件后设置该字体。 此参数设置为 TRUE，则会导致控件重绘自身。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_SETMCFONT](/windows/desktop/Controls/dtm-setmcfont)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  如果使用此代码，您需要使成员的你`CDialog`的派生类调用*m_MonthFont*类型的`CFont`。

##  <a name="setmonthcalstyle"></a>  CDateTimeCtrl::SetMonthCalStyle

设置下拉月历控件与当前的日期和时间选取器控件相关联的样式。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*dwStyle*|[in]新月份的日历控件样式，这是个月日历控件样式的按位组合 (OR)。 有关详细信息，请参阅[个月日历控件样式](/windows/desktop/Controls/month-calendar-control-styles)。|

### <a name="return-value"></a>返回值

上一个下拉月历控件的样式。

### <a name="remarks"></a>备注

此方法将发送[DTM_SETMCSTYLE](/windows/desktop/Controls/dtm-setmcstyle)消息，Windows SDK 中所述。

### <a name="example"></a>示例

下面的代码示例定义变量， *m_dateTimeCtrl*，即用于以编程方式访问日期和时间选取器控件。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例设置要显示周数，缩写的星期几，和任何今日指示器的天的日期和时间选取器控件。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>  CDateTimeCtrl::SetRange

设置日期和时间选取器控件的最小值和最大允许的系统时间。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>参数

*pMinRange*<br/>
一个指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含在允许的最早时间`CDateTimeCtrl`对象。

*pMaxRange*<br/>
一个指向`COleDateTime`对象或`CTime`对象，其中包含在允许的最新时间`CDateTimeCtrl`对象。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_SETRANGE](/windows/desktop/Controls/dtm-setrange)，如 Windows SDK 中所述。 在 MFC 的实现中，您可以指定`COleDateTime`或`CTime`用法。 如果`COleDateTime`对象中的 NULL 状态，将删除范围。 如果`CTime`指针或`COleDateTime`指针为 NULL，则将删除范围。

### <a name="example"></a>示例

  有关示例，请参阅[CDateTimeCtrl::GetRange](#getrange)。

##  <a name="settime"></a>  CDateTimeCtrl::SetTime

在日期和时间选取器控件中设置的时间。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>参数

*timeNew*<br/>
对引用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象，其中包含为控件设置。

*pTimeNew*<br/>
在上面的指针的第二个版本[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象，其中包含将控件设置的时间。 在上面的指针的第三个版本[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它包含将控件设置的时间。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数可实现 Win32 消息的行为[DTM_SETSYSTEMTIME](/windows/desktop/Controls/dtm-setsystemtime)，如 Windows SDK 中所述。 中的 MFC 实现`SetTime`，可以使用`COleDateTime`或`CTime`类，也可以使用`SYSTEMTIME`结构，若要设置的时间信息。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl 类](../../mfc/reference/cmonthcalctrl-class.md)
