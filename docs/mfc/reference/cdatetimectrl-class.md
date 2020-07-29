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
ms.openlocfilehash: 80b6177d788cfbe44388ec1e6a203b8037f834bc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223091"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl 类

封装日期和时间选取器控件功能。

## <a name="syntax"></a>语法

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDateTimeCtrl：： CDateTimeCtrl](#cdatetimectrl)|构造 `CDateTimeCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CDateTimeCtrl：： CloseMonthCal](#closemonthcal)|关闭当前日期和时间选取器控件。|
|[CDateTimeCtrl：： Create](#create)|创建日期和时间选取器控件，并将其附加到 `CDateTimeCtrl` 对象。|
|[CDateTimeCtrl：： GetDateTimePickerInfo](#getdatetimepickerinfo)|检索有关当前日期和时间选择器控件的信息。|
|[CDateTimeCtrl：： GetIdealSize](#getidealsize)|返回显示当前日期或时间所需的日期和时间选取器控件的理想大小。|
|[CDateTimeCtrl：： GetMonthCalColor](#getmonthcalcolor)|检索日期和时间选取器控件内月历的给定部分的颜色。|
|[CDateTimeCtrl：： GetMonthCalCtrl](#getmonthcalctrl)|检索 `CMonthCalCtrl` 与日期和时间选取器控件关联的对象。|
|[CDateTimeCtrl：： GetMonthCalFont](#getmonthcalfont)|检索日期和时间选择器控件的子月历控件当前使用的字体。|
|[CDateTimeCtrl：： GetMonthCalStyle](#getmonthcalstyle)|获取当前日期和时间选择器控件的样式。|
|[CDateTimeCtrl：： GetRange](#getrange)|检索日期和时间选择器控件的当前最小和最大允许系统时间。|
|[CDateTimeCtrl：： GetTime](#gettime)|从日期和时间选取器控件中检索当前选定的时间，并将其放入指定的 `SYSTEMTIME` 结构。|
|[CDateTimeCtrl：： SetFormat](#setformat)|根据给定的格式字符串，设置日期和时间选择器控件的显示。|
|[CDateTimeCtrl：： SetMonthCalColor](#setmonthcalcolor)|设置日期和时间选取器控件内月历的给定部分的颜色。|
|[CDateTimeCtrl：： SetMonthCalFont](#setmonthcalfont)|设置日期和时间选择器控件的子月历控件将使用的字体。|
|[CDateTimeCtrl：： SetMonthCalStyle](#setmonthcalstyle)|设置当前日期和时间选取器控件的样式。|
|[CDateTimeCtrl：： SetRange](#setrange)|设置日期和时间选取器控件所允许的最小和最大系统时间。|
|[CDateTimeCtrl：： SetTime](#settime)|设置日期和时间选取器控件中的时间。|

## <a name="remarks"></a>备注

日期和时间选取器控件（DTP 控制）提供了一个简单的界面，用于与用户交换日期和时间信息。 此接口包含字段，其中每个字段都显示存储在控件中的日期和时间信息的一部分。 用户可以通过更改给定字段中的字符串的内容来更改存储在控件中的信息。 用户可以使用鼠标或键盘从字段移到字段。

创建日期和时间选取器控件时，可以通过将各种样式应用于该对象来对其进行自定义。 有关特定于日期和时间选取器控件的样式的详细信息，请参阅[日期和时间选取器控件 Windows SDK 样式](/windows/win32/Controls/date-and-time-picker-control-styles)。 您可以使用格式样式设置 DTP 控件的显示格式。 在 Windows SDK 主题[日期和时间选择器控件样式](/windows/win32/Controls/date-and-time-picker-control-styles)中的 "格式样式" 下面描述了这些格式样式。

日期和时间选取器控件还使用通知和回调，如[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)中所述。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>要求

**标头：** afxdtctl

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl：： CDateTimeCtrl

构造 `CDateTimeCtrl` 对象。

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl：： CloseMonthCal

关闭当前日期和时间选取器控件。

```cpp
void CloseMonthCal() const;
```

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例关闭当前日期和时间选取器控件的下拉日历。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl：： Create

创建日期和时间选取器控件，并将其附加到 `CDateTimeCtrl` 对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定日期时间控件样式的组合。 有关日期和时间选择器样式的详细信息，请参阅[日期和时间选取器控件 Windows SDK 样式](/windows/win32/Controls/date-and-time-picker-control-styles)。

*rect*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，它是日期和时间选择器控件的位置和大小。

*pParentWnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是日期和时间选取器控件的父窗口。 值不得为 NULL。

*nID*<br/>
指定日期和时间选择器控件的控件 ID。

### <a name="return-value"></a>返回值

如果创建成功，则为非零值;否则为0。

### <a name="remarks"></a>备注

##### <a name="to-create-a-date-and-time-picker-control"></a>创建日期和时间选取器控件

1. 调用[CDateTimeCtrl](#cdatetimectrl)以构造 `CDateTimeCtrl` 对象。

1. 调用此成员函数，该函数创建 Windows 日期和时间选取器控件，并将其附加到 `CDateTimeCtrl` 对象。

调用时 `Create` ，将初始化公共控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl：： GetDateTimePickerInfo

检索有关当前日期和时间选择器控件的信息。

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pDateTimePickerInfo*|弄指向[DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo)结构的指针，该结构接收当前日期和时间选取器控件的说明。<br /><br /> 调用方负责分配此结构。 但是，此方法初始化结构的*cbSize*成员。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例指示它是否成功检索当前日期和时间选择器控件的相关信息。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDateTimeCtrl：： GetMonthCalColor

检索日期和时间选取器控件内月历的给定部分的颜色。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>参数

*iColor*<br/>
一个 **`int`** 值，该值指定要检索的月历的颜色区域。 有关值的列表，请参阅[SetMonthCalColor](#setmonthcalcolor)的*iColor*参数。

### <a name="return-value"></a>返回值

如果成功，则为表示月历控件指定部分的颜色设置的 COLORREF 值。 如果不成功，则函数返回-1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDateTimeCtrl：： GetMonthCalCtrl

检索 `CMonthCalCtrl` 与日期和时间选取器控件关联的对象。

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>返回值

指向[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)对象的指针; 如果不成功，则为 NULL; 如果窗口不可见，则为 NULL。

### <a name="remarks"></a>备注

日期和时间选取器控件在用户单击下拉箭头时创建一个子月历控件。 当 `CMonthCalCtrl` 不再需要该对象时，它将被销毁，因此，你的应用程序不得依赖于存储表示日期时间选择器控件的子月日历的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDateTimeCtrl：： GetMonthCalFont

获取日期和时间选择器控件的月历控件当前使用的字体。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>返回值

指向[CFont](../../mfc/reference/cfont-class.md)对象的指针; 如果不成功，则为 NULL。

### <a name="remarks"></a>备注

`CFont`返回值指向的对象是临时对象，在下一个空闲处理时间内被销毁。

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDateTimeCtrl：： GetMonthCalStyle

获取与当前日期和时间选取器控件相关联的下拉月历控件的样式。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>返回值

下拉月日历控件的样式，它是日期和时间选取器控件样式的按位组合（OR）。 有关详细信息，请参阅[月历控件样式](/windows/win32/Controls/month-calendar-control-styles)。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle)消息。

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl：： GetRange

检索日期和时间选择器控件的当前最小和最大允许系统时间。

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
指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针，该对象包含对象中允许的最早时间 `CDateTimeCtrl` 。

*pMaxRange*<br/>
一个指针，指向 `COleDateTime` 对象或对象，该对象 `CTime` 包含对象中允许的最晚时间 `CDateTimeCtrl` 。

### <a name="return-value"></a>返回值

一个 DWORD 值，其中包含指示设置了哪些范围的标志。 如果

`return value & GDTR_MAX` == 0

然后，第二个参数是有效的。 同样，如果

`return value & GDTR_MIN` == 0

第一个参数是有效的。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)的行为，如 Windows SDK 中所述。 在 MFC 的实现中，可以指定 `COleDateTime` 或 `CTime` 使用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl：： GetTime

从日期和时间选取器控件中检索当前选定的时间，并将其放入指定的 `SYSTEMTIME` 结构。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>参数

*timeDest*<br/>
在第一个版本中，是对将接收系统时间信息的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。 在第二个版本中，是对将接收系统时间信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*pTimeDest*<br/>
指向用于接收系统时间信息的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针。 不得为 NULL。

### <a name="return-value"></a>返回值

在第一个版本中，如果成功将时间写入对象，则 `COleDateTime` 为非零值; 否则为0。 在第二个和第三个版本中，DWORD 值等于[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构中的*dwFlag*成员集。 有关详细信息，请参阅下面的 "**备注**" 部分。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)的行为，如 Windows SDK 中所述。 在的 MFC 实现中 `GetTime` ，您可以使用 `COleDateTime` 或 `CTime` 类，也可以使用 `SYSTEMTIME` 结构来存储时间信息。

在第二个和第三个版本中，上述第二个和第三个版本中的返回值 DWORD 指示日期和时间选取器控件是否设置为 "no date" 状态，如[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构成员*dwFlags*中所示。 如果返回的值等于 GDT_NONE，则控件设置为 "无日期" 状态，并使用 DTS_SHOWNONE 样式。 如果返回的值等于 GDT_VALID，则系统时间将成功存储在目标位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl：： GetIdealSize

返回显示当前日期或时间所需的日期和时间选取器控件的理想大小。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*psize*|弄指向包含控件理想大小的[大小](/windows/win32/api/windef/ns-windef-size)结构的指针。|

### <a name="return-value"></a>返回值

返回值始终为 TRUE。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例检索显示日期和时间选择器控件的理想大小。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl：： SetFormat

根据给定的格式字符串，设置日期和时间选择器控件的显示。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>参数

*pstrFormat*<br/>
指向以零结尾的格式字符串的指针，该字符串定义所需的显示。 如果将此参数设置为 NULL，则会将控件重置为当前样式的默认格式字符串。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

> [!NOTE]
> 用户输入不会确定此调用是成功还是失败。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDateTimeCtrl：： SetMonthCalColor

设置日期和时间选取器控件内月历的给定部分的颜色。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>参数

*iColor*<br/>
**`int`** 值，该值指定要设置月历控件的哪个区域。 此值可以是下列值之一。

|值|含义|
|-----------|-------------|
|MCSC_BACKGROUND|设置在月之间显示的背景色。|
|MCSC_MONTHBK|设置在一个月内显示的背景色。|
|MCSC_TEXT|设置用于在一个月内显示文本的颜色。|
|MCSC_TITLEBK|设置日历标题中显示的背景色。|
|MCSC_TITLETEXT|设置用于在日历标题内显示文本的颜色。|
|MCSC_TRAILINGTEXT|设置用于显示标题和尾随日期文本的颜色。 标头和尾随日期是当前日历上出现的上个月和后几个月的日期。|

*ref*<br/>
一个 COLORREF 值，表示将为月历的指定区域设置的颜色。

### <a name="return-value"></a>返回值

如果成功，则为表示月历控件指定部分的前一种颜色设置的 COLORREF 值。 否则，消息将返回-1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CDateTimeCtrl：： GetMonthCalColor](#getmonthcalcolor)的示例。

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDateTimeCtrl：： SetMonthCalFont

设置日期和时间选择器控件的子月历控件将使用的字体。

```cpp
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*hFont*<br/>
要设置的字体的句柄。

*bRedraw*<br/>
指定是否应在设置字体时立即重绘控件。 将此参数设置为 TRUE 将导致控件重绘其自身。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> 如果使用此代码，你将需要将 `CDialog` 派生类的成员称为*m_MonthFont*类型 `CFont` 。

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl：： SetMonthCalStyle

设置与当前日期和时间选取器控件相关联的下拉月历控件的样式。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwStyle*|中新的月历控件样式，它是月历控件样式的按位组合（OR）。 有关详细信息，请参阅[月历控件样式](/windows/win32/Controls/month-calendar-control-styles)。|

### <a name="return-value"></a>返回值

下拉月份日历控件的上一个样式。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle)消息。

### <a name="example"></a>示例

下面的代码示例定义了用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

下面的代码示例将日期和时间选取器控件设置为显示周数、星期几的缩写名称和当前无指示器。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl：： SetRange

设置日期和时间选取器控件所允许的最小和最大系统时间。

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
指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象或[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针，该对象包含对象中允许的最早时间 `CDateTimeCtrl` 。

*pMaxRange*<br/>
一个指针，指向 `COleDateTime` 对象或对象，该对象 `CTime` 包含对象中允许的最晚时间 `CDateTimeCtrl` 。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)的行为，如 Windows SDK 中所述。 在 MFC 的实现中，可以指定 `COleDateTime` 或 `CTime` 使用。 如果 `COleDateTime` 对象的状态为 NULL，则将删除该范围。 如果 `CTime` 指针或 `COleDateTime` 指针为 NULL，则将删除该范围。

### <a name="example"></a>示例

  请参阅[CDateTimeCtrl：： GetRange](#getrange)的示例。

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl：： SetTime

设置日期和时间选取器控件中的时间。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>参数

*timeNew*<br/>
对[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用，该对象包含将设置控件的。

*pTimeNew*<br/>
在上面的第二个版本中，是指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针，该对象包含将设置控件的时间。 在上述第三个版本中，指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，该结构包含将设置控件的时间。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)的行为，如 Windows SDK 中所述。 在的 MFC 实现中 `SetTime` ，您可以使用 `COleDateTime` 或 `CTime` 类，也可以使用 `SYSTEMTIME` 结构来设置时间信息。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl 类](../../mfc/reference/cmonthcalctrl-class.md)
