---
title: COleDateTime 类
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 610cbec6cb65d4e9616c5e0e0d64e729f39febcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317751"
---
# <a name="coledatetime-class"></a>COleDateTime 类

封装 OLE`DATE`自动化中使用的数据类型。

## <a name="syntax"></a>语法

```
class COleDateTime
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleDate时间：COleDatetime](#coledatetime)|构造 `COleDateTime` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDateTime：：格式](#format)|生成`COleDateTime`对象的格式化字符串表示形式。|
|[COleDatetime：获取 ASDBTIMESTAMP](#getasdbtimestamp)|调用此方法以获取`COleDateTime`对象中作为`DBTIMESTAMP`数据结构的时间。|
|[COleDatetime：获取系统时间](#getassystemtime)|调用此方法以获取`COleDateTime`对象中作为[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)数据结构的时间。|
|[COleDate时间：获取日期](#getasudate)|调用此方法以获取 数据结构中`COleDateTime``UDATE`的时间。|
|[COleDateTime：获取当前时间](#getcurrenttime)|创建`COleDateTime`表示当前时间的对象（静态成员函数）。|
|[COleDateTime时间：获取日](#getday)|返回此`COleDateTime`对象表示的当天 （1 - 31）。|
|[COleDatetime：获取周](#getdayofweek)|返回此`COleDateTime`对象表示的一周中的一天（星期日 = 1）。|
|[COleDatetime：获得一年](#getdayofyear)|返回此`COleDateTime`对象表示的一年中的一天（1 月 1 日 = 1）。|
|[COleDatetime：获取小时](#gethour)|返回此`COleDateTime`对象表示的小时 （0 - 23）。|
|[COleDatetime：获取分钟](#getminute)|返回此`COleDateTime`对象表示的分钟 （0 - 59）。|
|[COleDateTime时间：获取月](#getmonth)|返回此`COleDateTime`对象表示的月份 （1 - 12）。|
|[COleDateTime时间：获取第二](#getsecond)|返回此`COleDateTime`对象表示的第二个对象 （0 - 59）。|
|[COleDateTime时间：获取状态](#getstatus)|获取此`COleDateTime`对象的状态（有效性）。|
|[COleDate时间：获取年份](#getyear)|返回此`COleDateTime`对象表示的年份。|
|[COleDateTime：:P时间](#parsedatetime)|从字符串读取日期/时间值并设置 的值`COleDateTime`。|
|[COleDate 时间：：设置日期](#setdate)|将此`COleDateTime`对象的值设置为指定的仅日期值。|
|[COleDate时间：：设置日期时间](#setdatetime)|将此`COleDateTime`对象的值设置为指定的日期/时间值。|
|[COleDatetime：：设置状态](#setstatus)|设置此`COleDateTime`对象的状态（有效性）。|
|[COleDateTime：：设置时间](#settime)|将此`COleDateTime`对象的值设置为指定的仅时间值。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[COleDateTime：：运算符 =，COleDateTime：：运算符<等。](#coledatetime_relational_operators)|比较两`COleDateTime`个值。|
|[COleDateTime：：运算符 +，COleDateTime：：运算符 -](#operator_add_-)|添加和减去`COleDateTime`值。|
|[COleDateTime：：运算符 =，COleDateTime：：运算符 -*](#operator_add_eq_-_eq)|从该`COleDateTime`对象中`COleDateTime`添加和减去值。|
|[COleDateTime：：运算符 |](#operator_eq)|复制值`COleDateTime`。|
|[COleDateTime：：操作员日期，COleDate时间：：操作员日期*](#operator_date)|将`COleDateTime`值转换为 或`DATE`。 `DATE*`|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleDate时间：：m_dt](#m_dt)|包含此`COleDateTime`对象的基础`DATE`。|
|[COleDate时间：：m_status](#m_status)|包含此`COleDateTime`对象的状态。|

## <a name="remarks"></a>备注

`COleDateTime`没有基类。

它是 OLE 自动化[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)数据类型的可能类型之一。 值`COleDateTime`表示绝对日期和时间值。

该`DATE`类型作为浮点值实现。 从 1899 年 12 月 30 日午夜开始测量天数。 下表显示了一些日期及其关联的值：

|Date|“值”|
|----------|-----------|
|1899年12月29日，午夜|-1.0|
|1899年12月29日，上午6时|-1.25|
|1899年12月30日 午夜|0.0|
|1899年12月31日 午夜|1.0|
|1900 年 1 月 1 日，上午 6 点|2.25|

> [!CAUTION]
> 在上表中，虽然 1899 年 12 月 30 日午夜前日值变为负值，但时间值不会。 例如，无论表示该日的整数是正数（1899 年 12 月 30 日之后）还是负值（1899 年 12 月 30 日之前），6：00 AM 始终由分数值 0.25 表示。 这意味着，简单的浮点比较会错误地将`COleDateTime`1899 年 12 月 29 日早上 6：00 的表示排序为**晚**于当天 7：00 表示的浮点。

该`COleDateTime`课程处理日期从 1 月 1 日到 9999 年 12 月 31 日。 类`COleDateTime`使用公历;它不支持朱利安日期。 `COleDateTime`忽略夏令时。 （请参阅[日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md).）

> [!NOTE]
> 您可以使用该`%y`格式仅检索从 1900 年开始的日期的两位数年份。 如果在 1900 年之前的日期使用`%y`该格式，则代码将生成 ASSERT 失败。

此类型还用于表示仅日期或仅时间值。 按照惯例，日期 0（1899 年 12 月 30 日）用于仅时间值，时间 00：00（午夜）用于仅日期值。

`COleDateTime`如果使用少于 100 的日期创建对象，则接受该日期，但随后调用`GetYear` `GetMonth`、、、、、、、、、`GetMinute``GetSecond``GetDay``GetHour`失败并返回 -1。 以前，您可以使用两位数日期，但在 MFC 4.2 及更高版本中，日期必须为 100 或更大。

为避免问题，请指定一个四位数的日期。 例如：

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

`COleDateTime`值的基本算术运算使用配套类[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。 `COleDateTimeSpan`值定义时间间隔。 这些类之间的关系类似于 CTime 和[CTimeSpan](../../atl-mfc-shared/reference/ctime-class.md) [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之间的关系。

有关`COleDateTime`和`COleDateTimeSpan`类的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="requirements"></a>要求

**标题：** ATLComTime.h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a>COleDateTime关系运算符

比较运算符。

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>参数

*日期*<br/>
要比较的 `COleDateTime` 对象。

### <a name="remarks"></a>备注

> [!NOTE]
> 如果两个操作数中的任何一个无效，则会发生 ATLASSERT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>示例

如果对象**>=** 设置为**\<** **>** null，**<**`COleDateTime`则运算符 、、和 将断言。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a>COleDate时间：COleDatetime

构造 `COleDateTime` 对象。

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>参数

*日期Src*<br/>
要复制到`COleDateTime`新`COleDateTime`对象的现有对象。

*varSrc*<br/>
要转换为`VARIANT`日期/时间值（VT_DATE）并复制到新`COleVariant``COleDateTime`对象的现有数据结构（可能是对象）。

*德茨尔克*<br/>
要复制到新`COleDateTime`对象的日期`DATE`/时间 （ ） 值。

*时间Src*<br/>
要`time_t`转换为`__time64_t`日期/时间值并复制到新`COleDateTime`对象中的 或 值。

*系统时间Src*<br/>
要`SYSTEMTIME`转换为日期/时间值并复制到新`COleDateTime`对象的结构。

*文件时间Src*<br/>
要`FILETIME`转换为日期/时间值并复制到新`COleDateTime`对象的结构。 A`FILETIME`使用通用协调时间 （UTC），因此，如果在结构中传递本地时间，则结果将不正确。 有关详细信息，请参阅 Windows SDK 中[的文件时间](/windows/win32/SysInfo/file-times)。

*nYear*， *nMonth*， *nDay*， *nHour*， *nMin*， *nSec*<br/>
指示要复制到新`COleDateTime`对象的日期和时间值。

*wDosDate*， *wDosTime*<br/>
要转换为日期/时间值并复制到新`COleDateTime`对象的 MS-DOS 日期和时间值。

*时间 戳*<br/>
对包含当前本地时间的[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)结构的引用。

### <a name="remarks"></a>备注

所有这些构造函数都创建初始化`COleDateTime`为指定值的新对象。 下表显示了每个日期和时间组件的有效范围：

|日期/时间组件|有效范围|
|--------------------------|-----------------|
|year|100 - 9999|
|月份|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

请注意，日组件的实际上限因月份和年份组件而异。 有关详细信息，请参阅 或`SetDate``SetDateTime`成员函数。

以下是每个构造函数的简要说明：

- `COleDateTime(`**）** 构造初始`COleDateTime`化为 0 的对象（1899 年 12 月 30 日午夜）。

- `COleDateTime(``dateSrc` **）** 从现有`COleDateTime``COleDateTime`对象构造对象。

- `COleDateTime(`*varSrc* **）** 构造`COleDateTime`一个对象。 尝试将`VARIANT`结构或[COleVariant](../../mfc/reference/colevariant-class.md)对象转换为日期/时间 （ `VT_DATE`） 值。 如果此转换成功，则转换后的值将复制到新`COleDateTime`对象中。 如果不是，`COleDateTime`则对象的值设置为 0（1899 年 12 月 30 日午夜），其状态无效。

- `COleDateTime(``dtSrc` **）** 从`DATE`值`COleDateTime`构造对象。

- `COleDateTime(``timeSrc` **）** 从`time_t`值`COleDateTime`构造对象。

- `COleDateTime(`*systimeSrc* **）** 从`COleDateTime``SYSTEMTIME`值构造对象。

- `COleDateTime(``filetimeSrc` **）** 从`FILETIME`值`COleDateTime`构造对象。 . A`FILETIME`使用通用协调时间 （UTC），因此，如果在结构中传递本地时间，则结果将不正确。 有关详细信息，请参阅 Windows SDK 中的[文件时间](/windows/win32/SysInfo/file-times)。

- `COleDateTime(``nYear`、、、、、、、、`nMonth``nDay``nHour``nMin``nSec`**)** 从`COleDateTime`指定的数值构造对象。

- `COleDateTime(``wDosDate` `wDosTime` **）** 从指定的 MS-DOS 日期和时间值构造`COleDateTime`对象。

有关`time_t`数据类型的详细信息，请参阅*运行时库参考*中[的时间](../../c-runtime-library/reference/time-time32-time64.md)函数。

有关详细信息，请参阅 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

> [!NOTE]
> 仅当包含 OLEDB.h 时，使用`DBTIMESTAMP`参数的构造函数才可用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a>COleDateTime：：格式

创建日期/时间值的格式化表示形式。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

dwFlags**<br/>
指示以下区域设置标志之一：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

- VAR_TIMEVALUEONLY在分析过程中忽略日期部分。

- VAR_DATEVALUEONLY在分析过程中忽略时间部分。

*Lcid*<br/>
指示用于转换区域设置 ID。 有关语言标识符的详细信息，请参阅[语言标识符](/windows/win32/Intl/language-identifiers)。

*lpsz格式*<br/>
类似于格式字符串的`printf`格式字符串。 每个格式代码（前面有百分比 （ `%`） 符号，由相应的`COleDateTime`组件替换。 格式字符串中的其他字符将复制到返回的字符串。 有关详细信息，请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。 格式化`Format`代码的值和含义是：

- `%H`当天的小时数

- `%M`当前小时内的分钟数

- `%S`当前分钟中的秒数

- `%%`百分比符号

*nFormatID*<br/>
格式控制字符串的资源 ID。

### <a name="return-value"></a>返回值

包含`CString`格式化日期/时间值的 。

### <a name="remarks"></a>备注

如果此`COleDateTime`对象的状态为 null，则返回值为空字符串。 如果状态无效，则返回字符串由字符串资源ATL_IDS_DATETIME_INVALID指定。

此函数的三种窗体的简要说明如下：

`Format`*（dwFlags*， *lcid*）<br/>
此窗体使用日期和时间的语言规范（区域设置指示）设置值格式。 使用默认参数，此窗体将打印日期和时间，除非时间部分为 0（午夜），在这种情况下，它将只打印日期，或日期部分为 0（1899 年 12 月 30 日），在这种情况下，它将只打印时间。 如果日期/时间值为 0（1899 年 12 月 30 日午夜），则此包含默认参数的窗体将在午夜打印。

`Format`*（lpszFormat*）<br/>
此窗体使用格式字符串设置值，该字符串包含特殊格式代码，前面有百分比符号 （%），如 中`printf`。 格式化字符串作为参数传递给函数。 有关格式代码的详细信息，请参阅运行时库参考中的["时刻"和"wcsftime"。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

`Format`（ *nFormatID*）<br/>
此窗体使用格式字符串设置值，该字符串包含特殊格式代码，前面有百分比符号 （%），如 中`printf`。 格式化字符串是一个资源。 此字符串资源的 ID 作为参数传递。 有关格式代码的详细信息，请参阅*运行时库参考*中的["时刻"和 wcsftime。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>COleDatetime：获取 ASDBTIMESTAMP

调用此方法以获取`COleDateTime`对象中作为`DBTIMESTAMP`数据结构的时间。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>参数

*时间 戳*<br/>
对[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)结构的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

将结果时间存储在引用*的时间戳*结构中。 此`DBTIMESTAMP`函数初始化的数据结构将使其`fraction`成员设置为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a>COleDatetime：获取系统时间

调用此方法以获取`COleDateTime`对象中作为`SYSTEMTIME`数据结构的时间。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>参数

*sysTime*<br/>
对[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的引用，用于从`COleDateTime`对象接收转换的日期/时间值。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;如果转换失败，或者对象为 NULL`COleDateTime`或无效，则 FALSE。

### <a name="remarks"></a>备注

`GetAsSystemTime`在引用的*sysTime*对象中存储生成的时间。 此`SYSTEMTIME`函数初始化的数据结构将使其`wMilliseconds`成员设置为零。

有关`COleDateTime`对象中持有的状态信息的详细信息，请参阅[获取状态](#getstatus)。

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a>COleDate时间：获取日期

调用此方法以获取`COleDateTime`对象中作为`UDATE`数据结构的时间。

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>参数

*uDate*<br/>
对结构的`UDATE`引用，用于从`COleDateTime`对象接收转换的日期/时间值。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE;如果转换失败，或者对象为 NULL`COleDateTime`或无效，则 FALSE。

### <a name="remarks"></a>备注

结构`UDATE`表示"未包装"日期。

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a>COleDateTime：获取当前时间

调用此静态成员函数以返回当前日期/时间值。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a>COleDateTime时间：获取日

获取由此日期/时间值表示的月份日期。

```
int GetDay() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime`对象的值表示的月份当天，或者如果`COleDateTime::error`无法获取该天。

### <a name="remarks"></a>备注

有效返回值范围在 1 和 31 之间。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a>COleDatetime：获取周

获取由此日期/时间值表示的月份日期。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime`对象的值表示的星期数，或者如果`COleDateTime::error`无法获取星期一。

### <a name="remarks"></a>备注

有效返回值的范围介于 1 和 7 之间，其中 1=星期日、2=星期一等。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获得新年](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a>COleDatetime：获得一年

获取由此日期/时间值表示的一年中的日期。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>返回值

以此`COleDateTime`对象的值表示的一年中的天，或者如果`COleDateTime::error`无法获取该年份的当天。

### <a name="remarks"></a>备注

有效返回值的范围介于 1 和 366 之间，其中 1 月 1 = 1。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a>COleDatetime：获取小时

获取此日期/时间值表示的小时。

```
int GetHour() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime`对象的值表示的小时，或者如果`COleDateTime::error`无法获取小时。

### <a name="remarks"></a>备注

有效返回值范围介于 0 和 23 之间。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a>COleDatetime：获取分钟

获取此日期/时间值表示的分钟。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime`对象的值表示的分钟，或者如果`COleDateTime::error`无法获取分钟。

### <a name="remarks"></a>备注

有效返回值范围介于 0 和 59 之间。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a>COleDateTime时间：获取月

获取由此日期/时间值表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime`对象的值表示的月份，或者如果`COleDateTime::error`无法获取该月。

### <a name="remarks"></a>备注

有效返回值的范围在 1 和 12 之间。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a>COleDateTime时间：获取第二

获取此日期/时间值表示的第二个。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>返回值

第二个由此`COleDateTime`对象的值表示或`COleDateTime::error`第二个无法获取。

### <a name="remarks"></a>备注

有效返回值范围介于 0 和 59 之间。

> [!NOTE]
> 类`COleDateTime`不支持闰秒。

有关 的`COleDateTime`实现的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a>COleDateTime时间：获取状态

获取给定`COleDateTime`对象的状态（有效性）。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>返回值

返回此值`COleDateTime`的状态。 如果调用`GetStatus`使用默认值构造`COleDateTime`的对象，它将返回有效。 如果调用`GetStatus`使用`COleDateTime`构造函数设置为 null 初始化的对象，`GetStatus`则返回 null。

### <a name="remarks"></a>备注

返回值由`DateTimeStatus`枚举类型定义，该类型在类中`COleDateTime`定义。

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleDateTime::error`指示尝试获取部分日期/时间值时出错。

- `COleDateTime::valid`指示此`COleDateTime`对象有效。

- `COleDateTime::invalid`指示此对象`COleDateTime`无效;如果表明此对象无效。也就是说，其值可能不正确。

- `COleDateTime::null`指示此`COleDateTime`对象为 null，即未为此对象提供任何值。 （这是"无值"的数据库意义上的"空"，而不是C++ NULL。

在以下情况下，`COleDateTime`对象的状态无效：

- 如果其值从 无法转换为`VARIANT`日期`COleVariant`/时间值的 或 值设置。

- 如果其值从`time_t`、`SYSTEMTIME`或`FILETIME`无法转换为有效日期/时间值的值设置。

- 如果其值由`SetDateTime`无效参数值设置。

- 如果此对象在算术赋值操作期间（即`+=`或`-=`） 经历了溢出或下溢。

- 如果为此对象分配了无效值。

- 如果此对象的状态被显式设置为无效使用`SetStatus`。

有关可能将状态设置为无效的操作的详细信息，请参阅以下成员函数：

- [COleDateTime](#coledatetime)

- [设置日期时间](#setdatetime)

- [运算符 +， -](#operator_add_-)

- [运算符 *， -]](#operator_add_eq_-_eq)

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a>COleDate时间：获取年份

获取由此日期/时间值表示的年份。

```
int GetYear() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime`对象的值表示的年份，或者如果`COleDateTime::error`无法获得该年份。

### <a name="remarks"></a>备注

有效返回值范围介于 100 和 9999 之间，其中包括世纪。

有关查询此`COleDateTime`对象值的其他成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

## <a name="coledatetimem_dt"></a><a name="m_dt"></a>COleDate时间：：m_dt

此`COleDateTime`对象`DATE`的基础结构。

```
DATE m_dt;
```

### <a name="remarks"></a>备注

> [!CAUTION]
> 更改此函数返回的`DATE`指针访问的对象中的值将更改此`COleDateTime`对象的值。 它不会更改此`COleDateTime`对象的状态。

有关对象的实现的详细信息，`DATE`请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="coledatetimem_status"></a><a name="m_status"></a>COleDate时间：：m_status

包含此`COleDateTime`对象的状态。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>备注

此数据成员的类型是枚举类型`DateTimeStatus`，在类中`COleDateTime`定义。 有关详细信息，请参阅[COleDateTime：：：获取状态](#getstatus)。

> [!CAUTION]
> 此数据成员适用于高级编程情况。 应使用内联成员函数["获取状态"](#getstatus)和["设置状态](#setstatus)"。 有关`SetStatus`显式设置此数据成员的进一步注意事项，请参阅。

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a>COleDateTime：：运算符 |

复制值`COleDateTime`。

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>备注

这些重载分配运算符将源日期/时间值复制到此`COleDateTime`对象中。 下面简要说明每个重载分配运算符：

- **运算符 *（** `dateSrc` **）** 操作数的值和状态将复制到此`COleDateTime`对象中。

- 运算符 **（varSrc* **operator =(** **）** 如果[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)值（或[COleVariant](../../mfc/reference/colevariant-class.md)对象）转换为日期/时间 （VT_DATE） 成功，则转换后的值将复制到此`COleDateTime`对象中，其状态设置为有效。 如果转换不成功，则此对象的值设置为零（1899 年 12 月 30 日午夜），其状态设置为无效。

- **运算符 *（** `dtSrc` **）** 该`DATE`值将复制到此`COleDateTime`对象，其状态设置为有效。

- **运算符 *（** `timeSrc` **）** 或`time_t``__time64_t`值将转换并复制到此`COleDateTime`对象中。 如果转换成功，则此对象的状态设置为有效;如果转换成功，则此对象的状态将设置为"有效"。如果不成功，则将其设置为无效。

- **运算符 =（***系统Src）* **)**[系统时间](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)值将转换并复制到此`COleDateTime`对象。 如果转换成功，则此对象的状态设置为有效;如果转换成功，则此对象的状态将设置为"有效"。如果不成功，则将其设置为无效。

- **运算符 *（** `uDate` **）** 该`UDATE`值将转换并复制到此`COleDateTime`对象。 如果转换成功，则此对象的状态设置为有效;如果转换成功，则此对象的状态将设置为"有效"。如果不成功，则将其设置为无效。 结构`UDATE`表示"未包装"日期。 有关详细信息，请参阅函数[VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate)。

- **运算符 *（** `filetimeSrc` **）**[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)值将转换并复制到此`COleDateTime`对象中。 如果转换成功，则此对象的状态设置为有效;如果转换成功，则此对象的状态将设置为"有效"。否则，它设置为无效。 `FILETIME`使用通用协调时间 （UTC），因此，如果您在结构中传递 UTC 时间，则结果将从 UTC 时间转换为本地时间，并将存储为变体时间。 此行为与 Visual C++ 6.0 和 Visual C++.NET 2003 SP2 中的行为相同。 有关详细信息，请参阅 Windows SDK 中的[文件时间](/windows/win32/SysInfo/file-times)。

有关详细信息，请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)条目。

有关`time_t`数据类型的详细信息，请参阅*运行时库参考*中[的时间](../../c-runtime-library/reference/time-time32-time64.md)函数。

有关详细信息，请参阅 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a>COleDateTime：：操作员 +， -

添加和减去`ColeDateTime`值。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>备注

`COleDateTime`对象表示绝对时间。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)对象表示相对时间。 前两个运算符允许您从值中添加和减去`COleDateTimeSpan`值`COleDateTime`。 第三个运算符允许您从另一`COleDateTime`个值中减去一个`COleDateTimeSpan`值以生成值。

如果任一操作数为空，则结果`COleDateTime`值的状态为 null。

如果生成的`COleDateTime`值超出可接受值的边界，则该`COleDateTime`值的状态无效。

如果任一操作数无效，另一个操作数不为空，则结果`COleDateTime`值的状态无效。

如果**+** 对象**-** 设置为 null，`COleDateTime`和 运算符将断言。 有关示例，请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDate时间：：操作员*，-*

从该`COleDateTime`对象中`ColeDateTime`添加和减去值。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>备注

这些运算符允许您在此和 中添加和`COleDateTimeSpan`减去值`COleDateTime`。 如果任一操作数为空，则结果`COleDateTime`值的状态为 null。

如果生成的`COleDateTime`值超出可接受值的边界，则此值`COleDateTime`的状态设置为无效。

如果任一操作数无效，而其他操作数不为空，则结果`COleDateTime`值的状态无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

如果**+=** 对象**-=** 设置为 null，`COleDateTime`和 运算符将断言。 有关示例，请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)。

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a>COleDate 时间：：操作员日期

将`ColeDateTime`值转换为 。 `DATE`

```
operator DATE() const throw();
```

### <a name="remarks"></a>备注

此运算符返回其`DATE`值从此`COleDateTime`对象复制的对象。 有关对象的实现的详细信息，`DATE`请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

如果`DATE`对象设置为 null，`COleDateTime`则运算符将断言。 有关示例，请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)。

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a>COleDateTime：:P时间

分析要读取日期/时间值的字符串。

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*lpszDate*<br/>
指向要解析的 null 终止字符串的指针。 有关详细信息，请参阅“备注”。

dwFlags**<br/>
指示区域设置和解析的标志。 以下一个或多个标志：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

- VAR_TIMEVALUEONLY在分析过程中忽略日期部分。

- VAR_DATEVALUEONLY在分析过程中忽略时间部分。

*Lcid*<br/>
指示用于转换区域设置 ID。

### <a name="return-value"></a>返回值

如果字符串已成功转换为日期/时间值（否则为 FALSE），则返回 TRUE。

### <a name="remarks"></a>备注

如果字符串已成功转换为日期/时间值，则此`COleDateTime`对象的值将设置为该值，其状态将有效。

> [!NOTE]
> 年值必须介于 100 和 9999 之间（包括）。

*lpszDate*参数可以采用各种格式。 例如，以下字符串包含可接受的日期/时间格式：

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

区域设置 ID 还将影响字符串格式是否可以转换为日期/时间值。

在VAR_DATEVALUEONLY的情况下，时间值设置为时间 0 或午夜。 就VAR_TIMEVALUEONLY而言，日期值设置为日期 0，即 1899 年 12 月 30 日。

如果无法将字符串转换为日期/时间值，或者存在数字溢出，则此`COleDateTime`对象的状态无效。

有关`COleDateTime`值的边界和实现的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="coledatetimesetdate"></a><a name="setdate"></a>COleDate 时间：：设置日期

设置此`COleDateTime`对象的日期。

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>参数

*n 年*， *n月*， *nDay*<br/>
指示要复制到此`COleDateTime`对象的日期组件。

### <a name="return-value"></a>返回值

如果已成功设置此`COleDateTime`对象的值，则为零;否则，1。 此返回值基于`DateTimeStatus`枚举类型。 有关详细信息，请参阅["设置状态"](#setstatus)成员函数。

### <a name="remarks"></a>备注

日期设置为指定的值。 时间设置为时间 0，午夜。

有关参数值的边界，请参阅下表：

|参数|边界|
|---------------|------------|
|*n年*|100 - 9999|
|*n月*|1 - 12|
|*nDay*|0 - 31|

如果月中的天溢出，它将转换为下个月的正确日，月份和/或年份将相应地增加。 零的日值表示上个月的最后一天。 行为与`SystemTimeToVariantTime`相同。

如果参数指定的日期值无效，则此对象的状态将设置为`COleDateTime::invalid`。 应使用[GetStatus](#getstatus)检查`DATE`该值的有效性，并且不应假定[m_dt](#m_dt)的值将保持未修改状态。

下面是日期值的一些示例：

|*n年*|*n月*|*nDay*|“值”|
|-------------|--------------|------------|-----------|
|2000|2|29|2000年2月29日|
|1776|7|4|1776年7月4日|
|1925|4|35|1925年4月35日（无效日期）|
|10000|1|1|10000 年 1 月 1 日（无效日期）|

要同时设置日期和时间，请参阅[COleDateTime：：：设置日期时间](#setdatetime)。

有关查询此`COleDateTime`对象值的成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a>COleDate时间：：设置日期时间

设置此`COleDateTime`对象的日期和时间。

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>参数

*nYear*， *nMonth*， *nDay*， *nHour*， *nMin*， *nSec*<br/>
指示要复制到此`COleDateTime`对象的日期和时间组件。

### <a name="return-value"></a>返回值

如果已成功设置此`COleDateTime`对象的值，则为零;否则，1。 此返回值基于`DateTimeStatus`枚举类型。 有关详细信息，请参阅["设置状态"](#setstatus)成员函数。

### <a name="remarks"></a>备注

有关参数值的边界，请参阅下表：

|参数|边界|
|---------------|------------|
|*n年*|100 - 9999|
|*n月*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果月中的天溢出，它将转换为下个月的正确日，月份和/或年份将相应地增加。 零的日值表示上个月的最后一天。 该行为与[系统时间到变量时间](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime)相同。

如果参数指定的日期或时间值无效，则此对象的状态设置为无效，并且不会更改此对象的值。

下面是一些时间值示例：

|*nHour*|*nMin*|*nSec*|“值”|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|无效|
|9|60|0|无效|

下面是日期值的一些示例：

|*n年*|*n月*|*nDay*|“值”|
|-------------|--------------|------------|-----------|
|1995|4|15|1995年4月15日|
|1789|7|14|17 7月17日 1789|
|1925|2|30|无效|
|10000|1|1|无效|

要仅设置日期，请参阅[COleDateTime：：：设置日期](#setdate)。 要仅设置时间，请参阅[COleDateTime：：：设置时间](#settime)。

有关查询此`COleDateTime`对象值的成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

### <a name="example"></a>示例

请参阅[获取状态的示例](#getstatus)。

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a>COleDatetime：：设置状态

设置此`COleDateTime`对象的状态。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>参数

*状态*<br/>
此`COleDateTime`对象的新状态值。

### <a name="remarks"></a>备注

*状态*参数值由`DateTimeStatus`枚举类型定义，该类型在类中`COleDateTime`定义。 有关详细信息[，请参阅 COleDateTime：获取状态](#getstatus)。

> [!CAUTION]
> 此功能适用于高级编程情况。 此函数不会更改此对象中的数据。 它最常用于将状态设置为**null**或**无效**。 赋值运算符 （[运算符 =](#operator_eq)） 和[SetDateTime](#setdatetime)会根据源值设置对象的状态。

### <a name="example"></a>示例

请参阅[获取状态的示例](#getstatus)。

## <a name="coledatetimesettime"></a><a name="settime"></a>COleDateTime：：设置时间

设置此`COleDateTime`对象的时间。

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>参数

*nHour*， *nMin*， *nSec*<br/>
指示要复制到此`COleDateTime`对象的时间组件。

### <a name="return-value"></a>返回值

如果已成功设置此`COleDateTime`对象的值，则为零;否则，1。 此返回值基于`DateTimeStatus`枚举类型。 有关详细信息，请参阅["设置状态"](#setstatus)成员函数。

### <a name="remarks"></a>备注

时间设置为指定的值。 日期设置为日期 0，即 1899 年 12 月 30 日。

有关参数值的边界，请参阅下表：

|参数|边界|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果参数指定的时间值无效，则此对象的状态设置为无效，并且不会更改此对象的值。

下面是一些时间值示例：

|*nHour*|*nMin*|*nSec*|“值”|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|无效|
|9|60|0|无效|

要同时设置日期和时间，请参阅[COleDateTime：：：设置日期时间](#setdatetime)。

有关查询此`COleDateTime`对象值的成员函数的信息，请参阅以下成员函数：

- [获取日](#getday)

- [获取月](#getmonth)

- [获取年份](#getyear)

- [获取小时](#gethour)

- [获取分钟](#getminute)

- [获取第二](#getsecond)

- [获取周](#getdayofweek)

- [获得新年](#getdayofyear)

有关`COleDateTime`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

### <a name="example"></a>示例

请参阅[SetDate](#setdate)的示例。

## <a name="see-also"></a>另请参阅

[COleVariant 类](../../mfc/reference/colevariant-class.md)<br/>
[CTime 类](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
