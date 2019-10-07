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
ms.openlocfilehash: a254019d1efe916365799affa3d2c5271883bafb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491260"
---
# <a name="coledatetime-class"></a>COleDateTime 类

封装 OLE 自动化中使用的数据类型。`DATE`

## <a name="syntax"></a>语法

```
class COleDateTime
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDateTime:: COleDateTime](#coledatetime)|构造 `COleDateTime` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDateTime::Format](#format)|生成`COleDateTime`对象的格式化字符串表示形式。|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|调用此方法以获取`COleDateTime`对象中的时间`DBTIMESTAMP`作为数据结构。|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|调用此方法以获取`COleDateTime`对象中的时间作为[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)数据结构。|
|[COleDateTime::GetAsUDATE](#getasudate)|调用此方法以获取中`COleDateTime`的时间`UDATE`作为数据结构。|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|创建一个`COleDateTime`对象, 该对象表示当前时间 (静态成员函数)。|
|[COleDateTime::GetDay](#getday)|返回此`COleDateTime`对象表示的日期 (1-31)。|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|返回此`COleDateTime`对象所表示的周中的第几天 (星期日 = 1)。|
|[COleDateTime::GetDayOfYear](#getdayofyear)|返回此`COleDateTime`对象所表示的年中的第几天 (1 月1日)。|
|[COleDateTime::GetHour](#gethour)|返回此`COleDateTime`对象所表示的小时数 (0-23)。|
|[COleDateTime::GetMinute](#getminute)|返回此`COleDateTime`对象所表示的分钟数 (0-59)。|
|[COleDateTime::GetMonth](#getmonth)|返回此`COleDateTime`对象表示的月份 (1-12)。|
|[COleDateTime::GetSecond](#getsecond)|返回此`COleDateTime`对象表示的第二个 (0-59)。|
|[COleDateTime::GetStatus](#getstatus)|获取此`COleDateTime`对象的状态 (有效性)。|
|[COleDateTime::GetYear](#getyear)|返回此`COleDateTime`对象表示的年份。|
|[COleDateTime::ParseDateTime](#parsedatetime)|从字符串中读取日期/时间值, 并设置的值`COleDateTime`。|
|[COleDateTime::SetDate](#setdate)|将此`COleDateTime`对象的值设置为指定的仅日期值。|
|[COleDateTime::SetDateTime](#setdatetime)|将此`COleDateTime`对象的值设置为指定的日期/时间值。|
|[COleDateTime::SetStatus](#setstatus)|设置此`COleDateTime`对象的状态 (有效性)。|
|[COleDateTime::SetTime](#settime)|将此`COleDateTime`对象的值设置为指定的仅限时值。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[COleDateTime:: operator = =、COleDateTime:: operator < 等。](#coledatetime_relational_operators)|比较两`COleDateTime`个值。|
|[COleDateTime:: operator +, COleDateTime:: operator-](#operator_add_-)|增加和减少`COleDateTime`值。|
|[COleDateTime:: operator + =, COleDateTime:: operator-=](#operator_add_eq_-_eq)|在此`COleDateTime` `COleDateTime`对象中添加和减去值。|
|[COleDateTime:: operator =](#operator_eq)|`COleDateTime`复制值。|
|[COleDateTime:: operator DATE, COleDateTime:: operator Date *](#operator_date)|将值转换`DATE`为或`DATE*`。 `COleDateTime`|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|包含此`DATE` `COleDateTime`对象的基础。|
|[COleDateTime:: m_status](#m_status)|包含此`COleDateTime`对象的状态。|

## <a name="remarks"></a>备注

`COleDateTime`没有基类。

它是 OLE 自动化的[变量](/windows/win32/api/oaidl/ns-oaidl-variant)数据类型的可能类型之一。 `COleDateTime`值表示绝对日期和时间值。

`DATE`类型实现为浮点值。 天从1899年12月30日 (午夜) 开始。 下表显示了一些日期及其关联值:

|日期|值|
|----------|-----------|
|1899年12月29日午夜|-1.0|
|12月29日 1899, 6 A M M|-1.25|
|1899年12月30日, 午夜|0.0|
|午夜1899年12月31日|1.0|
|1900年1月1日, 上午6点|2.25|

> [!CAUTION]
> 在上表中, 尽管日期值在12月 30 1899 日午夜之前变成负值, 但当天时间值不是。 例如, 6:00 AM 始终由一个小值0.25 表示, 而不考虑表示 day 的整数是否为正值 (12 月 30 1899 日之后) 或负数 (12 月 30 1899 日之前)。 这意味着, 简单的浮点比较会错误7:00 地对`COleDateTime`表示 6:00 am on 12/29/1899 的进行排序。

`COleDateTime`类处理从100年1月1日到9999年12月31日的日期。 `COleDateTime`类使用公历, 而不支持儒略历日期。 `COleDateTime`忽略夏令时。 (请[参阅日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。)

> [!NOTE]
> 您可以使用`%y`格式仅检索从1900开始的日期的两位数年份。 如果在1900之前`%y`的日期使用格式, 则代码将生成断言失败。

此类型还用于表示仅限日期或仅限时间的值。 按照约定, 日期 0 (12 月 30, 1899) 用于仅限时间的值, 而时间 00:00 (午夜) 用于仅限日期的值。

如果通过使用小于`COleDateTime` 100 的日期创建对象, 则将接受该日期, 但随后对`GetYear`、 `GetMonth`、 `GetDay`、 `GetHour` `GetMinute`、和`GetSecond`的调用将失败并返回-1。 以前, 你可以使用两位数日期, 但 MFC 4.2 和更高版本中的日期必须是100或更大。

若要避免出现问题, 请指定一个四位数的日期。 例如:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

`COleDateTime`值的基本算术运算使用伴生类[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。 `COleDateTimeSpan`值定义时间间隔。 这些类之间的关系类似于[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之间的关系。

有关`COleDateTime` [和`COleDateTimeSpan`类的详细信息, 请参阅文章日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="requirements"></a>要求

**标头：** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>COleDateTime 关系运算符

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
>  如果两个操作数都无效, 则会发生 ATLASSERT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>示例

运算符 **>=** ， **\<=** ， **>** ，和 **<** ，如果将断言`COleDateTime`对象设置为 null。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>COleDateTime:: COleDateTime

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

*dateSrc*<br/>
要复制`COleDateTime`到新`COleDateTime`对象的现有对象。

*varSrc*<br/>
要转换`VARIANT`为日期/时间值`COleVariant` (VT_DATE) 并将其复制到新`COleDateTime`对象中的现有数据结构 (可能为对象)。

*dtSrc*<br/>
要复制到新`DATE` `COleDateTime`对象中的日期/时间 () 值。

*timeSrc*<br/>
要`time_t`转换`__time64_t`为日期/时间值并将其复制到新`COleDateTime`的对象中的或值。

*systimeSrc*<br/>
要转换为日期/时间值并将其复制到新`COleDateTime`的对象中的结构。`SYSTEMTIME`

*filetimeSrc*<br/>
要转换为日期/时间值并将其复制到新`COleDateTime`的对象中的结构。`FILETIME` `FILETIME`使用协调世界时 (UTC), 因此, 如果您在结构中传递了本地时间, 则结果将是不正确的。 有关详细信息, 请参阅 Windows SDK 中的[文件时间](/windows/win32/SysInfo/file-times)。

*nYear*、 *nMonth*、 *nDay*、 *nHour*、 *nMin*、 *nSec*<br/>
指示要复制到新`COleDateTime`对象中的日期和时间值。

*wDosDate*、 *wDosTime*<br/>
要转换为日期/时间值并将其复制到新`COleDateTime`对象中的 MS-DOS 日期和时间值。

*timeStamp*<br/>
对包含当前本地时间的[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)结构的引用。

### <a name="remarks"></a>备注

所有这些构造函数将`COleDateTime`创建初始化为指定值的新对象。 下表显示了每个日期和时间组件的有效范围:

|日期/时间组件|有效范围|
|--------------------------|-----------------|
|year|100 - 9999|
|月|0 - 12|
|天|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

请注意, "日" 部分的实际上限取决于 "月" 和 "年" 组件。 有关详细信息, 请`SetDate`参阅`SetDateTime`或成员函数。

下面是每个构造函数的简要说明:

- `COleDateTime(` **)** 构造初始化`COleDateTime`为 0 (午夜12月 30 1899 年12月) 的对象。

- `COleDateTime(`) 构造现有`COleDateTime` 对象`COleDateTime`中的对象。 `dateSrc`

- `COleDateTime(`*varSrc* **)** 构造`COleDateTime`对象。 尝试将`VARIANT`结构或[COleVariant](../../mfc/reference/colevariant-class.md)对象转换为日期/时间 ( `VT_DATE`) 值。 如果此转换成功, 转换后的值将复制到新`COleDateTime`的对象。 如果不是, 则将该`COleDateTime`对象的值设置为 0 (午夜 1899 12 月30日), 将其状态设置为 "无效"。

- `COleDateTime(``COleDateTime` **)** 从值构造对象`DATE` 。 `dtSrc`

- `COleDateTime(``COleDateTime` **)** 从值构造对象`time_t` 。 `timeSrc`

- `COleDateTime(`*systimeSrc* **)** `COleDateTime` 从`SYSTEMTIME`值构造对象。

- `COleDateTime(``COleDateTime` **)** 从值构造对象`FILETIME` 。 `filetimeSrc` . `FILETIME`使用协调世界时 (UTC), 因此, 如果您在结构中传递了本地时间, 则结果将是不正确的。 有关详细信息, 请参阅 Windows SDK 中的[文件时间](/windows/win32/SysInfo/file-times)。

- `COleDateTime(``nYear`、 、、`nDay`、、 **) 从**指定的数值构造`COleDateTime`对象。 `nMin` `nHour` `nMonth` `nSec`

- `COleDateTime(``wDosDate`, )`wDosTime`从指定`COleDateTime`的 MS-DOS 日期和时间值构造对象。

有关`time_t`数据类型的详细信息, 请参阅《*运行时库参考*中的[时间](../../c-runtime-library/reference/time-time32-time64.md)函数。

有关详细信息, 请参阅 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

> [!NOTE]
> 仅当包含`DBTIMESTAMP` OLEDB 时, 使用参数的构造函数才可用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>COleDateTime:: Format

创建日期/时间值的格式化表示形式。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
指示以下区域设置标志之一:

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置, 而不是使用自定义用户设置。

- 在分析过程中, VAR_TIMEVALUEONLY 将忽略 date 部分。

- VAR_DATEVALUEONLY 在分析过程中忽略时间部分。

*lcid*<br/>
指示用于转换的区域设置 ID。 有关语言标识符的详细信息, 请参阅[语言标识符](/windows/win32/Intl/language-identifiers)。

*lpszFormat*<br/>
格式字符串类似`printf`于格式设置字符串。 每个格式设置代码前面有一个百分号`%`() 号, 都将替换为`COleDateTime`相应的组件。 格式字符串中的其他字符将按原样复制到返回的字符串中。 有关详细信息, 请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。 格式设置代码`Format`的值和含义为:

- `%H`当天的小时

- `%M`当前小时内的分钟数

- `%S`当前分钟中的秒数

- `%%`百分号

*nFormatID*<br/>
格式控制字符串的资源 ID。

### <a name="return-value"></a>返回值

一个`CString` , 它包含格式化日期/时间值。

### <a name="remarks"></a>备注

如果此`COleDateTime`对象的状态为 null, 则返回值为空字符串。 如果状态无效, 则返回字符串由字符串资源 ATL_IDS_DATETIME_INVALID 指定。

此函数的三个窗体的简要说明如下所示:

`Format`( *dwFlags*, *lcid*)<br/>
此窗体使用日期和时间的语言规范 (区域设置 Id) 来设置值的格式。 使用默认参数, 此窗体将打印日期和时间, 除非时间部分为 0 (午夜), 在这种情况下, 它将只打印日期, 或日期部分为 0 (1899 12 月30日), 在这种情况下, 它将只打印时间。 如果日期/时间值为 0 (午夜 12 1899 月30日), 则此带有默认参数的窗体将在午夜打印。

`Format`( *lpszFormat*)<br/>
此窗体通过使用包含以百分号 (%) 开头的特殊格式设置代码来设置值的格式, 如中`printf`所示。 格式化字符串作为参数传递给函数。 有关格式设置代码的详细信息, 请参阅《运行时库参考中的[strftime、wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

`Format`( *nFormatID*)<br/>
此窗体通过使用包含以百分号 (%) 开头的特殊格式设置代码来设置值的格式, 如中`printf`所示。 格式化字符串是资源。 此字符串资源的 ID 作为参数传递。 有关格式设置代码的详细信息, 请参阅《*运行时库参考*中的[strftime、wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>COleDateTime:: GetAsDBTIMESTAMP

调用此方法以获取`COleDateTime`对象中的时间`DBTIMESTAMP`作为数据结构。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>参数

*timeStamp*<br/>
对[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)结构的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

将生成时间存储在引用的*时间戳*结构中。 此函数初始化的`fraction` 数据结构将其成员设置为零。`DBTIMESTAMP`

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>COleDateTime:: GetAsSystemTime

调用此方法以获取`COleDateTime`对象中的时间`SYSTEMTIME`作为数据结构。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>参数

*sysTime*<br/>
对用于接收`COleDateTime`对象中转换的日期/时间值的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的引用。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE;如果转换失败, 则为 FALSE; 如果`COleDateTime`对象为 NULL 或无效, 则为 FALSE。

### <a name="remarks"></a>备注

`GetAsSystemTime`将生成的时间存储在引用的*sysTime*对象中。 此函数初始化的`wMilliseconds` 数据结构将其成员设置为零。`SYSTEMTIME`

有关在`COleDateTime`对象中保存的状态信息的详细信息, 请参阅[GetStatus](#getstatus)。

##  <a name="getasudate"></a>COleDateTime:: GetAsUDATE

调用此方法以获取`COleDateTime`对象中的时间`UDATE`作为数据结构。

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>参数

*uDate*<br/>
对`UDATE`结构的引用, 该结构`COleDateTime`从对象接收转换的日期/时间值。

### <a name="return-value"></a>返回值

如果成功, 则返回 TRUE;如果转换失败, 则为 FALSE; 如果`COleDateTime`对象为 NULL 或无效, 则为 FALSE。

### <a name="remarks"></a>备注

`UDATE`结构表示 "解包" 日期。

##  <a name="getcurrenttime"></a>COleDateTime:: GetCurrentTime

调用此静态成员函数以返回当前日期/时间值。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>COleDateTime:: GetDay

获取此日期/时间值所表示的月份中的某一天。

```
int GetDay() const throw();
```

### <a name="return-value"></a>返回值

`COleDateTime` 此`COleDateTime::error`对象的值表示的月中的第几天, 如果无法获取当天的日期, 则为。

### <a name="remarks"></a>备注

有效的返回值范围是1到31之间的值。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>COleDateTime:: GetDayOfWeek

获取此日期/时间值所表示的月份中的某一天。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>返回值

`COleDateTime` 此`COleDateTime::error`对象的值表示的一周中的某一天, 如果无法获取该周中的日期, 则为。

### <a name="remarks"></a>备注

有效的返回值介于1到7之间, 其中 1 = 星期日, 2 = 星期一, 依此类推。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>COleDateTime:: GetDayOfYear

获取此日期/时间值所表示的年中的某一天。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>返回值

`COleDateTime` 此`COleDateTime::error`对象的值表示的年中的某一天, 如果无法获取该年的某一天, 则为。

### <a name="remarks"></a>备注

有效的返回值范围介于1到366之间, 其中1月 1 = 1。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>COleDateTime:: GetHour

获取此日期/时间值表示的小时。

```
int GetHour() const throw();
```

### <a name="return-value"></a>返回值

`COleDateTime` 此`COleDateTime::error`对象的值表示的小时, 如果无法获取该小时, 则为。

### <a name="remarks"></a>备注

有效的返回值范围为0到23。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>COleDateTime:: GetMinute

获取此日期/时间值所表示的分钟数。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>返回值

此`COleDateTime`对象的值表示的分钟数, 或者`COleDateTime::error` , 如果未能获得分钟。

### <a name="remarks"></a>备注

有效的返回值范围介于0到59之间。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

##  <a name="getmonth"></a>COleDateTime:: GetMonth

获取此日期/时间值所表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime` `COleDateTime::error`对象的值表示的月份, 如果无法获取月份, 则为。

### <a name="remarks"></a>备注

有效的返回值范围介于1到12之间。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

##  <a name="getsecond"></a>COleDateTime:: GetSecond

获取此日期/时间值表示的第二个。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime` `COleDateTime::error`对象的值表示的第二个, 如果无法获取第二个值, 则为。

### <a name="remarks"></a>备注

有效的返回值范围介于0到59之间。

> [!NOTE]
>  `COleDateTime`类不支持闰秒。

有关实现的`COleDateTime`详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

##  <a name="getstatus"></a>COleDateTime:: GetStatus

获取给定`COleDateTime`对象的状态 (有效性)。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>返回值

返回此`COleDateTime`值的状态。 如果对使用`GetStatus`默认构造`COleDateTime`的对象调用, 它将返回有效的。 如果对通过`GetStatus`将构造`COleDateTime`函数设置为 null 的对象调用, `GetStatus`将返回 null。

### <a name="remarks"></a>备注

返回值由`DateTimeStatus`枚举类型定义, 该类型是`COleDateTime`在类中定义的。

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

有关这些状态值的简要说明, 请参阅以下列表:

- `COleDateTime::error`指示在尝试获取部分日期/时间值时出错。

- `COleDateTime::valid`指示此`COleDateTime`对象有效。

- `COleDateTime::invalid`指示此`COleDateTime`对象无效; 也就是说, 它的值可能不正确。

- `COleDateTime::null`指示此`COleDateTime`对象为 null, 即没有为此对象提供值。 (在数据库意义上, 这是 "null", 而不是C++ null。)

`COleDateTime`对象的状态在下列情况下无效:

- 如果其值是从`VARIANT`无法转换为日期/时间值的或`COleVariant`值设置的, 则为。

- 如果它的值是从`time_t`无法转换为有效日期/时间值的、或`FILETIME`值设置的, `SYSTEMTIME`则为。

- 如果其值由`SetDateTime`无效参数值设置, 则为。

- 如果此对象在算术赋值操作期间遇到溢出或下溢, `+=`则为或。 `-=`

- 如果分配给此对象的值无效。

- 如果此对象的状态使用`SetStatus`显式设置为 "无效", 则为。

有关可能将状态设置为 "无效" 的操作的详细信息, 请参阅以下成员函数:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operator +、-](#operator_add_-)

- [operator +=, -=](#operator_add_eq_-_eq)

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>COleDateTime:: GetYear

获取此日期/时间值所表示的年份。

```
int GetYear() const throw();
```

### <a name="return-value"></a>返回值

由此`COleDateTime` `COleDateTime::error`对象的值表示的年份, 如果无法获取年份, 则为。

### <a name="remarks"></a>备注

有效的返回值范围为100到 9999, 包括世纪。

有关查询此`COleDateTime`对象的值的其他成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

##  <a name="m_dt"></a>COleDateTime:: m_dt

`DATE` 此`COleDateTime`对象的基础结构。

```
DATE m_dt;
```

### <a name="remarks"></a>备注

> [!CAUTION]
>  更改由此函数返回的`DATE`指针所访问的对象中的值将更改此`COleDateTime`对象的值。 它不会更改此`COleDateTime`对象的状态。

有关`DATE`对象实现的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="m_status"></a>COleDateTime:: m_status

包含此`COleDateTime`对象的状态。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>备注

此数据成员的类型是在`DateTimeStatus` `COleDateTime`类中定义的枚举类型。 有关详细信息, 请参阅[COleDateTime:: GetStatus](#getstatus)。

> [!CAUTION]
>  此数据成员适用于高级编程情况。 应使用内联成员函数[GetStatus](#getstatus)和[SetStatus](#setstatus)。 有关`SetStatus`显式设置此数据成员的其他注意事项, 请参阅。

##  <a name="operator_eq"></a>COleDateTime:: operator =

`COleDateTime`复制值。

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

这些重载赋值运算符将源日期/时间值复制到此`COleDateTime`对象中。 下面是每个重载赋值运算符的简要说明:

- **operator = (** `dateSrc` **)** 将操作数的值和状态复制到此`COleDateTime`对象中。

- **operator = (** *varSrc* **)** 如果将[变量](/windows/win32/api/oaidl/ns-oaidl-variant)值 (或[COleVariant](../../mfc/reference/colevariant-class.md)对象) 转换为日期/时间 (VT_DATE) 成功, 则会将转换后的值复制到此`COleDateTime`对象中, 并将其状态设置为 "有效"。 如果转换不成功, 则此对象的值将设置为零 (1899 年12月30日), 其状态将设置为 "无效"。

- **operator = (** `dtSrc` **)** 将`DATE`该值复制到此`COleDateTime`对象中, 并将其状态设置为 "有效"。

- **operator = (** `timeSrc` **)** 将`time_t`或`__time64_t`值转换并复制到此`COleDateTime`对象中。 如果转换成功, 则此对象的状态将设置为 "有效";如果不成功, 则将其设置为无效。

- **operator = (** *systimeSrc* **)** 转换[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)值并将其复制到此`COleDateTime`对象中。 如果转换成功, 则此对象的状态将设置为 "有效";如果不成功, 则将其设置为无效。

- **operator = (** `uDate` **)** 将`UDATE`值转换并复制到此`COleDateTime`对象中。 如果转换成功, 则此对象的状态将设置为 "有效";如果不成功, 则将其设置为无效。 `UDATE`结构表示 "解包" 日期。 有关详细信息, 请参阅函数[VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate)。

- **operator = (** `filetimeSrc` **)** 将[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)值转换并复制到此`COleDateTime`对象中。 如果转换成功, 则此对象的状态将设置为 "有效";否则设置为 "无效"。 `FILETIME`使用协调世界时 (UTC), 因此, 如果您在结构中传递 UTC 时间, 则结果将从 UTC 时间转换为本地时间, 并将存储为变体时间。 此行为与 Visual C++ 6.0 和 visual C++.net 2003 SP2 中的行为相同。 有关详细信息, 请参阅 Windows SDK 中的[文件时间](/windows/win32/SysInfo/file-times)。

有关详细信息, 请参阅 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)条目。

有关`time_t`数据类型的详细信息, 请参阅《*运行时库参考*中的[时间](../../c-runtime-library/reference/time-time32-time64.md)函数。

有关详细信息, 请参阅 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_add_-"></a>COleDateTime:: operator +,-

增加和减少`ColeDateTime`值。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>备注

`COleDateTime`对象表示绝对时间。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)对象表示相对时间。 前两个运算符允许您在`COleDateTimeSpan` `COleDateTime`值中添加和减去值。 第三个运算符允许您从一个`COleDateTime`值中减去一个值以`COleDateTimeSpan`产生一个值。

如果任一操作数为 null, 则结果`COleDateTime`值的状态为 null。

如果结果`COleDateTime`值超出可接受值的范围, 则该值的状态`COleDateTime`将无效。

如果其中一个操作数无效, 而另一个不为 null, 则结果`COleDateTime`值的状态将无效。

如果 **+** `COleDateTime`对象 **-** 设置为 null, 则和运算符将断言。 有关示例, 请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)。

有关有效、无效和 null 状态值的详细信息, 请参阅[m_status](#m_status)成员变量。

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>COleDateTime:: operator + =,-=

在此`ColeDateTime` `COleDateTime`对象中添加和减去值。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>备注

通过这些运算符, 可以在此`COleDateTimeSpan` `COleDateTime`中添加和减去值。 如果任一操作数为 null, 则结果`COleDateTime`值的状态为 null。

如果结果`COleDateTime`值超出可接受值的界限, 则此`COleDateTime`值的状态将设置为 "无效"。

如果其中一个操作数无效, 而另一个不为 null, 则结果`COleDateTime`值的状态将无效。

有关有效、无效和 null 状态值的详细信息, 请参阅[m_status](#m_status)成员变量。

如果 **+=** `COleDateTime`对象 **-=** 设置为 null, 则和运算符将断言。 有关示例, 请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)。

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_date"></a>COleDateTime:: operator DATE

将值转换为`DATE`。 `ColeDateTime`

```
operator DATE() const throw();
```

### <a name="remarks"></a>备注

此运算符将返回`DATE`一个对象, 该对象的值`COleDateTime`从此对象复制。 有关`DATE`对象实现的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

如果对象设置为 null,运算符将断言。`DATE` `COleDateTime` 有关示例, 请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)。

##  <a name="parsedatetime"></a>COleDateTime::P arseDateTime

分析字符串以读取日期/时间值。

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*lpszDate*<br/>
指向要分析的以 null 结尾的字符串的指针。 有关详细信息，请参阅“备注”。

*dwFlags*<br/>
指示区域设置和分析的标志。 以下一个或多个标志:

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置, 而不是自定义用户设置。

- 在分析过程中, VAR_TIMEVALUEONLY 将忽略 date 部分。

- VAR_DATEVALUEONLY 在分析过程中忽略时间部分。

*lcid*<br/>
指示用于转换的区域设置 ID。

### <a name="return-value"></a>返回值

如果字符串已成功转换为日期/时间值, 则返回 TRUE; 否则返回 FALSE。

### <a name="remarks"></a>备注

如果字符串已成功转换为日期/时间值, 此`COleDateTime`对象的值将设置为该值, 并将其状态设置为 "有效"。

> [!NOTE]
>  年份值必须介于100到 9999 (含) 之间。

*LpszDate*参数可以采用多种格式。 例如, 以下字符串包含可接受的日期/时间格式:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

区域设置 ID 还会影响字符串格式是否可用于转换为日期/时间值。

对于 VAR_DATEVALUEONLY, 时间值设置为 time 0 或午夜。 对于 VAR_TIMEVALUEONLY, 日期值设置为日期 0, 表示30年 12 1899 月30日。

如果字符串无法转换为日期/时间值, 或者如果存在数值溢出, 则此`COleDateTime`对象的状态无效。

有关`COleDateTime`值的界限和实现的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="setdate"></a>COleDateTime:: SetDate

设置此`COleDateTime`对象的日期。

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>参数

*nYear*、 *nMonth*、 *nDay*<br/>
指示要复制到此`COleDateTime`对象中的日期部分。

### <a name="return-value"></a>返回值

如果已成功设置此`COleDateTime`对象的值, 则为零; 否则为1。 此返回值基于枚举的`DateTimeStatus`类型。 有关详细信息, 请参阅[SetStatus](#setstatus)成员函数。

### <a name="remarks"></a>备注

日期设置为指定值。 时间设置为时间 0 (午夜)。

有关参数值的界限, 请参阅下表:

|参数|汇编|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

如果该月中的第几天溢出, 则会将其转换为下个月的正确日期, 月份和/或年份会相应递增。 如果日期值为零, 则表示上个月的最后一天。 行为与相同`SystemTimeToVariantTime`。

如果参数指定的日期值无效, 则此对象的状态将设置为`COleDateTime::invalid`。 应使用[GetStatus](#getstatus)来检查`DATE`值的有效性, 并不要假设[m_dt](#m_dt)的值将保持不变。

下面是一些日期值的示例:

|*nYear*|*nMonth*|*nDay*|值|
|-------------|--------------|------------|-----------|
|2000|2|29|2000年2月29日|
|1776|7|4|4 1776 7 月|
|1925|4|35|35年4月 1925 (日期无效)|
|10000|1|1|1 10000 年1月 (日期无效)|

若要设置日期和时间, 请参阅[COleDateTime:: SetDateTime](#setdatetime)。

有关查询此`COleDateTime`对象的值的成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>COleDateTime:: SetDateTime

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

*nYear*、 *nMonth*、 *nDay*、 *nHour*、 *nMin*、 *nSec*<br/>
指示要复制到此`COleDateTime`对象中的日期和时间部分。

### <a name="return-value"></a>返回值

如果已成功设置此`COleDateTime`对象的值, 则为零; 否则为1。 此返回值基于枚举的`DateTimeStatus`类型。 有关详细信息, 请参阅[SetStatus](#setstatus)成员函数。

### <a name="remarks"></a>备注

有关参数值的界限, 请参阅下表:

|参数|汇编|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果该月中的第几天溢出, 则会将其转换为下个月的正确日期, 月份和/或年份会相应递增。 如果日期值为零, 则表示上个月的最后一天。 此行为与[SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime)相同。

如果参数指定的日期或时间值无效, 则此对象的状态将设置为 "无效", 并且不会更改此对象的值。

下面是一些时间值示例:

|*nHour*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|无效|
|9|60|0|无效|

下面是一些日期值的示例:

|*nYear*|*nMonth*|*nDay*|值|
|-------------|--------------|------------|-----------|
|1995|4|15|4月15日1995|
|1789|7|14|17年7月1789|
|1925|2|30|无效|
|10000|1|1|无效|

若要设置日期, 请参阅[COleDateTime:: SetDate](#setdate)。 若要设置时间, 请参阅[COleDateTime:: SetTime](#settime)。

有关查询此`COleDateTime`对象的值的成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

请参阅[GetStatus](#getstatus)的示例。

##  <a name="setstatus"></a>COleDateTime:: SetStatus

设置此`COleDateTime`对象的状态。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>参数

*status*<br/>
此`COleDateTime`对象的新状态值。

### <a name="remarks"></a>备注

*状态*参数值由`DateTimeStatus`枚举类型定义, 该类型`COleDateTime`是在类中定义的。 有关详细信息, 请参阅[COleDateTime:: GetStatus](#getstatus) 。

> [!CAUTION]
>  此函数适用于高级编程情况。 此函数不会更改此对象中的数据。 通常用于将状态设置为**null**或**无效**。 赋值运算符 ([operator =](#operator_eq)) 和[SetDateTime](#setdatetime)根据源值设置对象的状态。

### <a name="example"></a>示例

请参阅[GetStatus](#getstatus)的示例。

##  <a name="settime"></a>COleDateTime:: SetTime

设置此`COleDateTime`对象的时间。

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>参数

*nHour*、 *nMin*、 *nSec*<br/>
指示要复制到此`COleDateTime`对象中的时间部分。

### <a name="return-value"></a>返回值

如果已成功设置此`COleDateTime`对象的值, 则为零; 否则为1。 此返回值基于枚举的`DateTimeStatus`类型。 有关详细信息, 请参阅[SetStatus](#setstatus)成员函数。

### <a name="remarks"></a>备注

时间设置为指定值。 日期设置为日期 0, 表示 30 1899 年12月30日。

有关参数值的界限, 请参阅下表:

|参数|汇编|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果参数指定的时间值无效, 则此对象的状态将设置为 "无效", 并且不会更改此对象的值。

下面是一些时间值示例:

|*nHour*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|无效|
|9|60|0|无效|

若要设置日期和时间, 请参阅[COleDateTime:: SetDateTime](#setdatetime)。

有关查询此`COleDateTime`对象的值的成员函数的信息, 请参阅以下成员函数:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关`COleDateTime`值界限的详细信息, 请参阅文章[日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

请参阅[SetDate](#setdate)的示例。

## <a name="see-also"></a>请参阅

[COleVariant 类](../../mfc/reference/colevariant-class.md)<br/>
[CTime 类](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
