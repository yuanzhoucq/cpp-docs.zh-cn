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
ms.openlocfilehash: 577dde7f4f4209f15590825fdb87fe23f788a1ce
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754608"
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
|[CDateTimeCtrl：：CDatetimeCtrl](#cdatetimectrl)|构造 `CDateTimeCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDateTimeCtrl：：关闭月卡尔](#closemonthcal)|关闭当前日期和时间选取器控件。|
|[CDateTimeCtrl：：创建](#create)|创建日期和时间选取器控件并将其附加到`CDateTimeCtrl`对象。|
|[CDateTimeCtrl：：获取DateTime选取器信息](#getdatetimepickerinfo)|检索有关当前日期和时间选取器控件的信息。|
|[CDateTimeCtrl：获取理想尺寸](#getidealsize)|返回显示当前日期和时间所需的日期和时间选取器控件的理想大小。|
|[CDatetimeCtrl：：获取月色](#getmonthcalcolor)|在日期和时间选取器控件中检索月历给定部分的颜色。|
|[CDatetimeCtrl：：获取月卡Ctrl](#getmonthcalctrl)|检索与`CMonthCalCtrl`日期和时间选取器控件关联的对象。|
|[CDatetimeCtrl：：获取月卡方](#getmonthcalfont)|检索日期和时间选取器控件的子月日历控件当前使用的字体。|
|[CDatetimeCtrl：：获取月卡风格](#getmonthcalstyle)|获取当前日期和时间选取器控件的样式。|
|[CDateTimeCtrl：：获取范围](#getrange)|检索日期和时间选取器控件的当前最小和最大允许的系统时间。|
|[CDateTimeCtrl：获取时间](#gettime)|从日期和时间选取器控件检索当前选择的时间，并将其放入指定的`SYSTEMTIME`结构中。|
|[CDateTimeCtrl：：设置格式](#setformat)|根据给定的格式字符串设置日期和时间选取器控件的显示。|
|[CDatetimeCtrl：：设置月色](#setmonthcalcolor)|在日期和时间选取器控件内设置月历给定部分的颜色。|
|[CDatetimeCtrl：：设置月卡方](#setmonthcalfont)|设置日期和时间选取器控件的子月日历控件将使用的字体。|
|[CDateTimeCtrl：：设置月卡风格](#setmonthcalstyle)|设置当前日期和时间选取器控件的样式。|
|[CDateTimeCtrl：：设置范围](#setrange)|设置日期和时间选取器控件的最小和最大允许的系统时间。|
|[CDateTimeCtrl：：设置时间](#settime)|设置日期和时间选取器控件中的时间。|

## <a name="remarks"></a>备注

日期和时间选取器控件 （DTP 控件） 提供了一个简单的界面，以便与用户交换日期和时间信息。 此接口包含字段，每个字段都显示存储在控件中的日期和时间信息的一部分。 用户可以通过更改给定字段中字符串的内容来更改控件中存储的信息。 用户可以使用鼠标或键盘从一个字段移动到一个字段。

您可以在创建对象时对对象应用各种样式来自定义日期和时间选取器控件。 有关特定于日期和时间选取器控件的样式的详细信息，请参阅 Windows SDK 中的[日期和时间选取器控件样式](/windows/win32/Controls/date-and-time-picker-control-styles)。 您可以使用格式样式设置 DTP 控件的显示格式。 这些格式样式在 Windows SDK 主题["日期和时间选取器控件样式](/windows/win32/Controls/date-and-time-picker-control-styles)"中的"格式样式"下进行了描述。

日期和时间选取器控件还使用通知和回调，这在[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)中描述。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>要求

**标题：** afxdtctl.h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl：：CDatetimeCtrl

构造 `CDateTimeCtrl` 对象。

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl：：关闭月卡尔

关闭当前日期和时间选取器控件。

```cpp
void CloseMonthCal() const;
```

### <a name="remarks"></a>备注

此方法发送[DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

以下代码示例关闭当前日期和时间选取器控件的下拉日历。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl：：创建

创建日期和时间选取器控件并将其附加到`CDateTimeCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定日期时间控制样式的组合。 有关日期和时间选取器样式的详细信息，请参阅 Windows SDK 中的[日期和时间选取器控件样式](/windows/win32/Controls/date-and-time-picker-control-styles)。

*矩形*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，它是日期和时间选取器控件的位置和大小。

*pparentwnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是日期和时间选取器控件的父窗口。 值不得为 NULL。

*nID*<br/>
指定日期和时间选取器控件的控制 ID。

### <a name="return-value"></a>返回值

如果创建成功，则非零;否则 0。

### <a name="remarks"></a>备注

##### <a name="to-create-a-date-and-time-picker-control"></a>创建日期和时间选取器控件

1. 调用[CDateTimeCtrl](#cdatetimectrl)构造`CDateTimeCtrl`对象。

1. 调用此成员函数，该函数创建 Windows 日期和时间选取器控件并将其附加到`CDateTimeCtrl`对象。

调用`Create`时调用 ，将初始化公共控件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl：：获取DateTime选取器信息

检索有关当前日期和时间选取器控件的信息。

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*pDateTime拾取信息*|[出]指向[DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo)结构的指针，该结构接收当前日期和时间选取器控件的说明。<br /><br /> 调用方负责分配此结构。 但是，此方法初始化结构的*cbSize*成员。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

以下代码示例指示它是否成功检索有关当前日期和时间选取器控件的信息。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDatetimeCtrl：：获取月色

在日期和时间选取器控件中检索月历给定部分的颜色。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>参数

*iColor*<br/>
指定要检索的月历的颜色区域的**int**值。 有关值列表，请参阅[SetMonthCalColor](#setmonthcalcolor)的*iColor*参数。

### <a name="return-value"></a>返回值

COLORREF 值，表示月份日历控件指定部分的颜色设置（如果成功）。 如果不成功，函数返回 -1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDatetimeCtrl：：获取月卡Ctrl

检索与`CMonthCalCtrl`日期和时间选取器控件关联的对象。

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>返回值

指向[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)对象的指针，如果不成功或窗口不可见，则指向 NULL。

### <a name="remarks"></a>备注

日期和时间选取器控件在用户单击下拉箭头时创建子月日历控件。 当不再需要`CMonthCalCtrl`该对象时，该对象将被销毁，因此应用程序不得依赖存储表示日期时间选取器控件的子月日历的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDatetimeCtrl：：获取月卡方

获取日期和时间选取器控件的月份日历控件当前使用的字体。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>返回值

指向[CFont](../../mfc/reference/cfont-class.md)对象的指针，如果不成功，则指向 NULL。

### <a name="remarks"></a>备注

返回`CFont`值指向的对象是临时对象，并在下一个空闲处理期间销毁。

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDatetimeCtrl：：获取月卡风格

获取与当前日期和时间选取器控件关联的下拉月日历控件的样式。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>返回值

下拉月日历控件的样式，它是日期和时间选取器控件样式的位组合 （OR）。 有关详细信息，请参阅[月历控件样式](/windows/win32/Controls/month-calendar-control-styles)。

### <a name="remarks"></a>备注

此方法发送[DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle)消息，这在 Windows SDK 中介绍。

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl：：获取范围

检索日期和时间选取器控件的当前最小和最大允许的系统时间。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>参数

*普明朗*<br/>
指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的指针或包含`CDateTimeCtrl`对象中允许的最早时间的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针。

*pMaxRange*<br/>
指向`COleDateTime`对象或包含`CTime``CDateTimeCtrl`对象中允许的最近时间的对象的指针。

### <a name="return-value"></a>返回值

包含指示设置范围的标志的 DWORD 值。 如果

`return value & GDTR_MAX` == 0

然后第二个参数有效。 同样，如果

`return value & GDTR_MIN` == 0

然后第一个参数有效。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)的行为，如 Windows SDK 中所述。 在 MFC 的实现中，您可以指定`COleDateTime`或`CTime`用法。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl：获取时间

从日期和时间选取器控件检索当前选择的时间，并将其放入指定的`SYSTEMTIME`结构中。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>参数

*时间时间*<br/>
在第一个版本中，对将收到系统时间信息的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。 在第二个版本中，对将收到系统时间信息的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的引用。

*pTimeD最*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，用于接收系统时间信息。 不能为 NULL。

### <a name="return-value"></a>返回值

在第一个版本中，如果时间已成功写入`COleDateTime`对象，则非零;否则 0。 在第二和第三版本中，DWORD 值等于[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构中设置的*dwFlag*成员。 有关详细信息，请参阅下面的**备注**部分。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)的行为，如 Windows SDK 中所述。 在`GetTime`MFC 实现的 中，可以使用`COleDateTime``CTime`或 类，也可以使用`SYSTEMTIME`结构来存储时间信息。

上面第二和第三版本中的返回值 DWORD 指示日期和时间选取器控件是否设置为"无日期"状态，如[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)结构成员*dwFlags*中所示。 如果返回的值等于GDT_NONE，则控件设置为"无日期"状态，并使用DTS_SHOWNONE样式。 如果返回的值等于GDT_VALID，则系统时间将成功存储在目标位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl：获取理想尺寸

返回显示当前日期和时间所需的日期和时间选取器控件的理想大小。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*psize*|[出]指向包含控件理想大小的[SIZE](/windows/win32/api/windef/ns-windef-size)结构的指针。|

### <a name="return-value"></a>返回值

返回值始终为 TRUE。

### <a name="remarks"></a>备注

此方法发送[DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

以下代码示例检索理想大小以显示日期和时间选取器控件。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl：：设置格式

根据给定的格式字符串设置日期和时间选取器控件的显示。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>参数

*pstrFormat*<br/>
指向定义所需显示的零端接格式字符串的指针。 将此参数设置为 NULL 会将控件重置为当前样式的默认格式字符串。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

> [!NOTE]
> 用户输入不能决定此调用的成功或失败。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDatetimeCtrl：：设置月色

在日期和时间选取器控件内设置月历给定部分的颜色。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>参数

*iColor*<br/>
**int**值，指定要设置的月历控件的哪个区域。 此值可以是以下值之一。

|“值”|含义|
|-----------|-------------|
|MCSC_BACKGROUND|设置月份之间显示的背景颜色。|
|MCSC_MONTHBK|设置一个月内显示的背景颜色。|
|MCSC_TEXT|设置用于在一个月内显示文本的颜色。|
|MCSC_TITLEBK|设置日历标题中显示的背景颜色。|
|MCSC_TITLETEXT|设置用于在日历标题中显示文本的颜色。|
|MCSC_TRAILINGTEXT|设置用于显示标题和尾随日文本的颜色。 标题和尾随日是当前日历上显示的前一个月和后几个月的天数。|

*ref*<br/>
表示将为月历的指定区域设置的颜色的 COLORREF 值。

### <a name="return-value"></a>返回值

COLORREF 值，表示月份日历控件指定部分的上一个颜色设置（如果成功）。 否则，消息返回 -1。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CDateTimeCtrl 的示例：获取月卡颜色](#getmonthcalcolor)。

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDatetimeCtrl：：设置月卡方

设置日期和时间选取器控件的子月日历控件将使用的字体。

```cpp
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>参数

*h字体*<br/>
处理要设置的字体。

*bredraw*<br/>
指定是否应在设置字体时立即重绘控件。 将此参数设置为 TRUE 会导致控件重新绘制自身。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> 如果使用此代码，则需要使`CDialog`派生类的成员称为*m_MonthFont*类型`CFont`。

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl：：设置月卡风格

设置与当前日期和时间选取器控件关联的下拉月日历控件的样式。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwStyle*|[在]新的月历控制样式，它是月历控件样式的位组合 （OR）。 有关详细信息，请参阅[月历控件样式](/windows/win32/Controls/month-calendar-control-styles)。|

### <a name="return-value"></a>返回值

下拉月日历控件的上一样式。

### <a name="remarks"></a>备注

此方法发送[DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例定义用于以编程方式访问日期和时间选取器控件的变量*m_dateTimeCtrl*。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>示例

以下代码示例将日期和时间选取器控件设置以显示周数、星期几缩写名称和"今日指示器"。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl：：设置范围

设置日期和时间选取器控件的最小和最大允许的系统时间。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>参数

*普明朗*<br/>
指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的指针或包含`CDateTimeCtrl`对象中允许的最早时间的[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针。

*pMaxRange*<br/>
指向`COleDateTime`对象或包含`CTime``CDateTimeCtrl`对象中允许的最近时间的对象的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)的行为，如 Windows SDK 中所述。 在 MFC 的实现中，您可以指定`COleDateTime`或`CTime`用法。 如果`COleDateTime`对象具有 NULL 状态，则该范围将被删除。 如果`CTime`指针或`COleDateTime`指针为 NULL，则将删除该范围。

### <a name="example"></a>示例

  请参阅[CDateTimeCtrl 的示例：：获取范围](#getrange)。

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl：：设置时间

设置日期和时间选取器控件中的时间。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>参数

*时间新*<br/>
对包含要向其设置控件的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)对象的引用。

*pTimeNew*<br/>
在上面的第二个版本中，指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象的指针，其中包含将控件设置为的时间。 在上面的第三个版本中，指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的指针，其中包含将控件设置为的时间。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)的行为，如 Windows SDK 中所述。 在 MFC 的`SetTime`实现中，可以使用`COleDateTime`或`CTime`类，也可以使用`SYSTEMTIME`结构来设置时间信息。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl 类](../../mfc/reference/cmonthcalctrl-class.md)
