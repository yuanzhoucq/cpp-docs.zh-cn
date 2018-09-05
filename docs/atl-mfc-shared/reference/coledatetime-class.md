---
title: COleDateTime 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c2cb19908b177ea1e07e0178023e868b96a4560
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754768"
---
# <a name="coledatetime-class"></a>COleDateTime 类

封装`DATE`OLE 自动化中使用的数据类型。

## <a name="syntax"></a>语法

```
class COleDateTime
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|构造 `COleDateTime` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleDateTime::Format](#format)|生成带格式的字符串表示形式的`COleDateTime`对象。|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|调用此方法以获取在时间`COleDateTime`对象作为`DBTIMESTAMP`数据结构。|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|调用此方法以获取在时间`COleDateTime`对象作为[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)数据结构。|
|[COleDateTime::GetAsUDATE](#getasudate)|调用此方法以获取在时间`COleDateTime`作为`UDATE`数据结构。|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|创建`COleDateTime`对象，表示当前时间 （静态成员函数）。|
|[COleDateTime::GetDay](#getday)|这将返回一天`COleDateTime`对象都表示 (1-31)。|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|这将返回日期是星期几`COleDateTime`对象 （星期日 = 1） 表示。|
|[COleDateTime::GetDayOfYear](#getdayofyear)|这将返回一年中的天`COleDateTime`对象的表示 （1 年 1 月 = 1）。|
|[COleDateTime::GetHour](#gethour)|将小时返回这`COleDateTime`对象表示 (0-23)。|
|[COleDateTime::GetMinute](#getminute)|返回分钟这`COleDateTime`对象表示 (0-59)。|
|[COleDateTime::GetMonth](#getmonth)|这将返回该月`COleDateTime`对象都表示 (1-12)。|
|[COleDateTime::GetSecond](#getsecond)|这将返回第二个`COleDateTime`对象表示 (0-59)。|
|[COleDateTime::GetStatus](#getstatus)|获取此状态 （有效期）`COleDateTime`对象。|
|[COleDateTime::GetYear](#getyear)|返回年份这`COleDateTime`对象表示。|
|[COleDateTime::ParseDateTime](#parsedatetime)|从字符串读取日期/时间值，并设置的值`COleDateTime`。|
|[COleDateTime::SetDate](#setdate)|设置此值`COleDateTime`为指定的纯日期值的对象。|
|[COleDateTime::SetDateTime](#setdatetime)|设置此值`COleDateTime`对象到指定的日期/时间值。|
|[COleDateTime::SetStatus](#setstatus)|设置此状态 （有效期）`COleDateTime`对象。|
|[COleDateTime::SetTime](#settime)|设置此值`COleDateTime`对象到指定的仅限时间的值。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[COleDateTime::operator = =、 COleDateTime::operator <，等等。](#coledatetime_relational_operators)|比较两个`COleDateTime`值。|
|[COleDateTime::operator + COleDateTime::operator-](#operator_add_-)|加法和减法`COleDateTime`值。|
|[COleDateTime::operator + =，COleDateTime::operator =](#operator_add_eq_-_eq)|加法和减法`COleDateTime`从此值`COleDateTime`对象。|
|[COleDateTime::operator =](#operator_eq)|副本`COleDateTime`值。|
|[COleDateTime::operator 日期，COleDateTime::operator 日期 *](#operator_date)|将转换`COleDateTime`值到`DATE`或`DATE*`。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|包含基础`DATE`此`COleDateTime`对象。|
|[COleDateTime::m_status](#m_status)|包含此状态`COleDateTime`对象。|

## <a name="remarks"></a>备注

`COleDateTime` 没有基类。

它是一种可能的类型[变体](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)的 OLE 自动化的数据类型。 一个`COleDateTime`值表示绝对日期和时间值。

`DATE`类型作为浮点值。 天是从 1899 年 12 月 30 日，在午夜测量的。 下表显示了某些日期和相关联的值：

|日期|“值”|
|----------|-----------|
|1899 年 12 月 29日日午夜|-1.0|
|1899 年 12 月 29日日，6 点|-1.25|
|1899 年 12 月 30日日午夜|0.0|
|1899 年 12 月 31日日午夜|1.0|
|1900 年 1 月 1日日，上午 6|2.25|

> [!CAUTION]
> 请注意，在上面的表，尽管日的值变为负值 1899 年 12 月 30 日，午夜之前的时间值不这样做。 例如，上午 6:00 始终表示无论整数代表日是正值 （之后 1899 年 12 月 30 日） 或负值 （之前 1899 年 12 月 30 日） 的小数部分值 0.25。 这意味着，简单的浮动点比较会错误地进行排序`COleDateTime`表示为 12/29/1899年 6:00 AM**更高版本**个表示同一天上午 7:00。

`COleDateTime`类处理 100 1 月 1 日，年 12 月 31 日的日期到 9999。 `COleDateTime`类使用公历; 它不支持对儒略历日期。 `COleDateTime` 将忽略夏时制。 (请参阅[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。)

> [!NOTE]
> 可以使用`%y`要检索仅对从 1900年开始日期的两位数的年份格式。 如果使用`%y`上代码前 1900 年的日期的格式生成断言失败。

此类型还用于表示纯日期或仅限时间的值。 按照约定，仅限时间的值使用 0 (1899 年 12 月 30 日) 的日期和时间 00:00 （午夜） 用于纯日期值。

如果您创建`COleDateTime`通过使用日期的对象少于 100 个，则日期是接受，但后续调用`GetYear`， `GetMonth`， `GetDay`， `GetHour`， `GetMinute`，和`GetSecond`失败并返回-1。 以前，可以使用两位数日期，但日期必须是 100 或更大在 MFC 4.2 及更高版本。

若要避免出现问题，指定四位数字日期。 例如：

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

有关基本算术运算`COleDateTime`值使用伴生类[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。 `COleDateTimeSpan` 值定义的时间间隔。 这些类之间的关系非常类似于之间[CTime](../../atl-mfc-shared/reference/ctime-class.md)并[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。

有关详细信息`COleDateTime`并`COleDateTimeSpan`类，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="requirements"></a>要求

**标头：** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>  COleDateTime 关系运算符

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

*日期*  
要比较的 `COleDateTime` 对象。

### <a name="remarks"></a>备注

> [!NOTE]
>  如果两个操作数之一无效，将发生 ATLASSERT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>示例

运算符**>=**， **\< =**， **>**，和**<**，如果将断言`COleDateTime`对象设置为 null。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>  COleDateTime::COleDateTime

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
COleDateTime(const DBTIMESTAMP& dbts) throw();
```

### <a name="parameters"></a>参数

*dateSrc*  
将现有`COleDateTime`对象复制到新`COleDateTime`对象。

*varSrc*  
将现有`VARIANT`数据结构 (可能`COleVariant`对象) 转换为日期/时间值 (VT_DATE) 并复制到新`COleDateTime`对象。

*dtSrc*  
日期/时间 (`DATE`) 要复制到新值`COleDateTime`对象。

*timeSrc*  
一个`time_t`或`__time64_t`值转换为日期/时间值并复制到新`COleDateTime`对象。

*systimeSrc*  
一个`SYSTEMTIME`结构转换为日期/时间值并复制到新`COleDateTime`对象。

*filetimeSrc*  
一个`FILETIME`结构转换为日期/时间值并复制到新`COleDateTime`对象。 请注意，`FILETIME`使用协调世界时 (UTC)，因此如果结构中传递了本地时间，则结果将为不正确。 请参阅[文件时间](/windows/desktop/SysInfo/file-times)Windows SDK for 的详细信息中。

*nYear*， *nMonth*，*第几日*，*几点*， *nMin*， *nSec*  
指示要复制到新的日期和时间值`COleDateTime`对象。

*wDosDate*， *wDosTime*  
MS-DOS 日期和时间值转换为日期/时间值并复制到新`COleDateTime`对象。

*dbts*  
对引用[DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype)结构，它包含当前本地时间。

### <a name="remarks"></a>备注

所有这些构造函数创建新`COleDateTime`对象初始化为指定的值。 下表显示了有效范围为每个日期和时间组件：

|日期/时间组件|有效范围|
|--------------------------|-----------------|
|年|100 - 9999|
|月|0 - 12|
|天|0 - 31|
|小时|0 - 23|
|分钟|0 - 59|
|第二个|0 - 59|

请注意，日期号数部分实际上限各不相同基础的月份和年份的组件。 有关详细信息，请参阅`SetDate`或`SetDateTime`成员函数。

下面是每个构造函数的简要说明：

- `COleDateTime(` **)** 构造`COleDateTime`对象初始化为 0 （午夜，30 1899 年 12 月）。

- `COleDateTime(` `dateSrc` **)** 构造`COleDateTime`从现有对象`COleDateTime`对象。

- `COleDateTime(` *varSrc* **)** 构造`COleDateTime`对象。 尝试将转换`VARIANT`结构或[COleVariant](../../mfc/reference/colevariant-class.md)日期/时间的对象 ( `VT_DATE`) 值。 如果此转换成功，转换后的值复制到新`COleDateTime`对象。 如果还没有，则`COleDateTime`对象设置为 0 （午夜，30 1899 年 12 月），其状态设置为无效。

- `COleDateTime(` `dtSrc` **)** 构造`COleDateTime`对象从`DATE`值。

- `COleDateTime(` `timeSrc` **)** 构造`COleDateTime`对象从`time_t`值。

- `COleDateTime(` *systimeSrc* **)** 构造`COleDateTime`对象从`SYSTEMTIME`值。

- `COleDateTime(` `filetimeSrc` **)** 构造`COleDateTime`对象从`FILETIME`值。 . 请注意，`FILETIME`使用协调世界时 (UTC)，因此如果结构中传递了本地时间，则结果将为不正确。 请参阅[文件时间](/windows/desktop/SysInfo/file-times)Windows SDK for 的详细信息中。

- `COleDateTime(` `nYear``nMonth`， `nDay`， `nHour`， `nMin`， `nSec` **)** 构造`COleDateTime`从指定的数字值的对象。

- `COleDateTime(` `wDosDate``wDosTime` **)** 构造`COleDateTime`从指定的 MS-DOS 日期和时间值的对象。

有关详细信息`time_t`数据类型，请参阅[时间](../../c-runtime-library/reference/time-time32-time64.md)函数，在*运行时库参考*。

有关详细信息，请参阅[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)并[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 中的结构。

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

> [!NOTE]
> 构造函数使用`DBTIMESTAMP`参数包括 OLEDB.h 时才可用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

创建日期/时间值的格式化表示形式。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*dwFlags*  
指示下列区域设置标志之一：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

- VAR_TIMEVALUEONLY 在分析过程中忽略日期部分。

- VAR_DATEVALUEONLY 在分析过程中忽略时间部分。

*lcid*  
指示要使用用于转换的区域设置 ID。 有关语言标识符的详细信息，请参阅[语言标识符](/windows/desktop/Intl/language-identifiers)。

*lpszFormat*  
格式设置字符串类似于`printf`格式设置字符串。 每个格式设置代码，注释按百分比 ( `%`) 登录，将替换为相应`COleDateTime`组件。 格式设置字符串中的其他字符被复制到返回的字符串不变。 请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)有关详细信息。 值和格式设置代码的含义`Format`是：

- `%H` 在当前的一天中的小时数

- `%M` 在当前小时内的分钟数

- `%S` 当前分钟的秒

- `%%` 百分比符号

*nFormatID*  
格式控制字符串资源 ID。

### <a name="return-value"></a>返回值

一个`CString`，其中包含带格式的日期/时间值。

### <a name="remarks"></a>备注

如果此状态`COleDateTime`对象为 null，则返回值为空字符串。 如果状态为无效，由字符串资源 ATL_IDS_DATETIME_INVALID 指定返回的字符串。

此函数的三种形式的简短说明如下所示：

`Format`( *dwFlags*， *lcid*)  
此窗体的使用的语言规范 （区域设置 Id） 设置格式的日期和时间的值。 使用默认参数，此窗体将打印日期和时间，时间部分为 0 （午夜），这种情况下它将打印只是日期或日期部分为 0 (30 1899 年 12 月)，除非在这种情况下它将打印在的时间。 如果日期/时间值为 0 (30 1899 年 12 月，午夜)，此窗体具有默认参数将打印午夜。

`Format`( *lpszFormat*)  
此窗体中通过使用格式字符串包含特殊的格式化代码前面带有百分号 （%） 的设置值`printf`。 格式设置字符串作为参数传递给函数。 有关格式设置代码的详细信息，请参阅[strftime、 wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)运行时库参考中。

`Format`( *nFormatID*)  
此窗体中通过使用格式字符串包含特殊的格式化代码前面带有百分号 （%） 的设置值`printf`。 格式设置字符串是一个资源。 此字符串资源的 ID 作为参数进行传递。 有关格式设置代码的详细信息，请参阅[strftime、 wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)中*运行时库参考*。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP

调用此方法以获取在时间`COleDateTime`对象作为`DBTIMESTAMP`数据结构。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>参数

*dbts*  
对引用[DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype)结构。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

将所生成的时间存储在被引用*dbts*结构。 `DBTIMESTAMP`由此函数初始化的数据结构将具有其`fraction`成员设置为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

调用此方法以获取在时间`COleDateTime`对象作为`SYSTEMTIME`数据结构。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>参数

*sysTime*  
对引用[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)接收从转换后的日期/时间值的结构`COleDateTime`对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUEFALSE 如果转换失败，或如果`COleDateTime`对象为 NULL 或无效。

### <a name="remarks"></a>备注

`GetAsSystemTime` 将所生成的时间存储在被引用*sysTime*对象。 `SYSTEMTIME`由此函数初始化的数据结构将具有其`wMilliseconds`成员设置为零。

请参阅[GetStatus](#getstatus)有关详细信息的状态信息保存在`COleDateTime`对象。

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

调用此方法以获取在时间`COleDateTime`对象作为`UDATE`数据结构。

```
bool GetAsUDATE(UDATE& udate) const throw();
```

### <a name="parameters"></a>参数

*udate*  
对引用`UDATE`结构，以接收转换后的日期/时间值从`COleDateTime`对象。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUEFALSE 如果转换失败，或如果`COleDateTime`对象为 NULL 或无效。

### <a name="remarks"></a>备注

一个`UDATE`结构表示"已解包"的日期。

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

调用此静态成员函数返回当前日期/时间值。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>  COleDateTime::GetDay

获取此日期/时间值所表示的月份的日期。

```
int GetDay() const throw();
```

### <a name="return-value"></a>返回值

此值所表示的每月天数`COleDateTime`对象或`COleDateTime::error`如果无法获取一天。

### <a name="remarks"></a>备注

有效的返回值的范围介于 1 和 31 之间。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

获取此日期/时间值所表示的月份的日期。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>返回值

此值所表示的星期几`COleDateTime`对象或`COleDateTime::error`如果无法获得日期是星期几。

### <a name="remarks"></a>备注

有效的返回值介于 1 和 7，其中 1 = 星期日，2 = 星期一，依次类推。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

获取此日期/时间值所表示的年份的日期。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>返回值

此值所表示的年的某一天`COleDateTime`对象或`COleDateTime::error`如果无法获取一年中的天。

### <a name="remarks"></a>备注

有效的返回值介于 1 和 366，其中 1 月 1 日 = 1。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>  COleDateTime::GetHour

获取表示此日期/时间值的小时。

```
int GetHour() const throw();
```

### <a name="return-value"></a>返回值

此设置的值表示的小时`COleDateTime`对象或`COleDateTime::error`如果无法获取在一小时。

### <a name="remarks"></a>备注

有效的返回值的范围介于 0 和 23 之间。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

获取此日期/时间值所表示的分钟。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>返回值

此值所表示的分钟`COleDateTime`对象或`COleDateTime::error`如果无法获得分钟。

### <a name="remarks"></a>备注

有效的返回值的范围介于 0 和 59 之间。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

有关示例，请参阅[GetHour](#gethour)。

##  <a name="getmonth"></a>  COleDateTime::GetMonth

获取此日期/时间值所表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>返回值

此值所表示的月份`COleDateTime`对象或`COleDateTime::error`如果无法获得每月。

### <a name="remarks"></a>备注

有效的返回值的范围介于 1 和 12 之间。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

有关示例，请参阅[GetDay](#getday)。

##  <a name="getsecond"></a>  COleDateTime::GetSecond

获取此日期/时间值所表示的第二个。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>返回值

此值所表示的第二个`COleDateTime`对象或`COleDateTime::error`如果无法获得第二个。

### <a name="remarks"></a>备注

有效的返回值的范围介于 0 和 59 之间。

> [!NOTE]
>  `COleDateTime`类不支持闰秒。

有关的实现详细信息`COleDateTime`，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>示例

有关示例，请参阅[GetHour](#gethour)。

##  <a name="getstatus"></a>  COleDateTime::GetStatus

获取状态 （有效期） 的给定`COleDateTime`对象。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>返回值

返回此状态`COleDateTime`值。 如果您调用`GetStatus`上`COleDateTime`使用默认值构造的对象，它将返回有效。 如果您调用`GetStatus`上`COleDateTime`对象初始化其构造函数设置为 null，`GetStatus`将返回 null。 请参阅**备注**有关详细信息。

### <a name="remarks"></a>备注

由定义的返回值`DateTimeStatus`枚举中定义的类型`COleDateTime`类。

```
enum DateTimeStatus  
{  
   error = -1,  
   valid = 0,  
   invalid = 1,    // Invalid date (out of range, etc.)  
   null = 2,       // Literally has no value  
};  
```

有关这些状态的值的简要说明，请参阅下面的列表：

- `COleDateTime::error` 指示错误发生时正在尝试获取日期/时间值的一部分。

- `COleDateTime::valid` 指示此`COleDateTime`对象是否有效。

- `COleDateTime::invalid` 指示此`COleDateTime`对象无效; 即，其值可能不正确。

- `COleDateTime::null` 指示此`COleDateTime`对象为 null，也即，已为此对象提供任何值。 （此为"null"数据库意义上的"无任何值，"，而不 c + + 为 NULL。）

状态`COleDateTime`对象是在以下情况下无效：

- 如果其值设置从`VARIANT`或`COleVariant`无法转换为日期/时间值的值。

- 如果其值设置从`time_t`， `SYSTEMTIME`，或`FILETIME`无法转换为有效的日期/时间值的值。

- 如果设置其值`SetDateTime`具有无效的参数值。

- 如果此对象已溢出或下溢在过程中遇到算术赋值运算，即`+=`或`-=`。

- 如果无效的值分配给此对象。

- 如果已显式设置该对象的状态为无效的使用`SetStatus`。

有关可能会将状态设置为无效的请参阅以下成员函数的操作的详细信息：

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [运算符 +、-](#operator_add_-)

- [运算符 + =、 =](#operator_add_eq_-_eq)

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>  COleDateTime::GetYear

获取此日期/时间值所表示的年份。

```
int GetYear() const throw();
```

### <a name="return-value"></a>返回值

此值所表示的年份`COleDateTime`对象或`COleDateTime::error`如果无法获取一年。

### <a name="remarks"></a>备注

返回有效值范围介于 100 和 9999 之间，其中包括世纪。

有关查询的此值的其他成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

有关示例，请参阅[GetDay](#getday)。

##  <a name="m_dt"></a>  COleDateTime::m_dt

基础`DATE`此结构`COleDateTime`对象。

```
DATE m_dt;
```

### <a name="remarks"></a>备注

> [!CAUTION]
>  更改中的值`DATE`对象访问此函数返回的指针将更改此设置的值`COleDateTime`对象。 它不会更改此状态`COleDateTime`对象。

有关实现的详细信息`DATE`对象，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="m_status"></a>  COleDateTime::m_status

包含此状态`COleDateTime`对象。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>备注

此数据成员的类型是枚举的类型`DateTimeStatus`，其定义内`COleDateTime`类。 请参阅[COleDateTime::GetStatus](#getstatus)有关详细信息。

> [!CAUTION]
>  此数据成员是针对高级编程情况。 应使用的内联成员函数[GetStatus](#getstatus)并[SetStatus](#setstatus)。 请参阅`SetStatus`有关显式设置此数据成员的其他注意事项。

##  <a name="operator_eq"></a>  COleDateTime::operator =

副本`COleDateTime`值。

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& udate) throw();
```

### <a name="remarks"></a>备注

这些重载的赋值运算符将源日期/时间值复制到此`COleDateTime`对象。 简要说明的每个这些重载赋值运算符如下所示：

- **运算符 = (** `dateSrc` **)** 的值和操作数的状态复制到此`COleDateTime`对象。

- **运算符 = (** *varSrc* **)** 如果的转换[变体](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)值 (或[COleVariant](../../mfc/reference/colevariant-class.md)对象) 到日期/时间 (| VT_日期） 成功时，转换后的值复制到此`COleDateTime`对象并将其状态设置为有效。 如果此转换不成功，此对象的值设置为零 (30 1899 年 12 月，午夜) 和其状态设置为无效。

- **运算符 = (** `dtSrc` **)** `DATE`值复制到此`COleDateTime`对象并将其状态设置为有效。

- **运算符 = (** `timeSrc` **)** `time_t`或`__time64_t`值转换，并复制到此`COleDateTime`对象。 如果转换成功，该对象的状态设置为有效，则为如果不成功，它将设置为无效。

- **运算符 = (** *systimeSrc* **)** [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)值转换，并复制到此`COleDateTime`对象。 如果转换成功，该对象的状态设置为有效，则为如果不成功，它将设置为无效。

- **运算符 = (** `udate` **)** `UDATE`值转换，并复制到此`COleDateTime`对象。 如果转换成功，该对象的状态设置为有效，则为如果不成功，它将设置为无效。 一个`UDATE`结构表示"已解包"的日期。 请参阅函数[VarDateFromUdate](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-vardatefromudate)的更多详细信息。

- **运算符 = (** `filetimeSrc` **)** [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)值转换，并复制到此`COleDateTime`对象。 如果转换成功，该对象的状态设置为有效，则为否则设置为无效。 `FILETIME` 使用协调世界时 (UTC)，因此，如果结构中传递 UTC 时间，结果将被转换从 UTC 时间为本地时间，并且将存储为变量时间。 此行为是与 Visual c + + 6.0 和 Visual c + +.NET 2003 SP2 中的相同。 请参阅[文件时间](/windows/desktop/SysInfo/file-times)Windows SDK for 的详细信息中。

有关详细信息，请参阅[变体](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)Windows SDK 中的条目。

有关详细信息`time_t`数据类型，请参阅[时间](../../c-runtime-library/reference/time-time32-time64.md)函数，在*运行时库参考*。

有关详细信息，请参阅[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)并[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 中的结构。

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_add_-"></a>  COleDateTime::operator +、-

加法和减法`ColeDateTime`值。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>备注

`COleDateTime` 对象表示绝对时间。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)对象表示相对的时间。 前两个运算符使您得以，加法和减法`COleDateTimeSpan`值从`COleDateTime`值。 第三个运算符可以减去`COleDateTime`从另一个用来产生值`COleDateTimeSpan`值。

如果任一操作数是 null，生成的状态`COleDateTime`值为 null。

如果得到`COleDateTime`值超出可接受的值，该状态的边界`COleDateTime`值无效。

如果任一操作数无效且不为 null，其他的生成状态`COleDateTime`值无效。

**+** 并**-** 运算符将断言如果`COleDateTime`对象设置为 null。 请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)有关的示例。

有关有效、 无效和 null 的状态值的详细信息，请参阅[m_status](#m_status)成员变量。

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTime::operator + =、 =

加法和减法`ColeDateTime`从此值`COleDateTime`对象。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>备注

这些运算符使您得以，加法和减法`COleDateTimeSpan`值到和从该`COleDateTime`。 如果任一操作数是 null，生成的状态`COleDateTime`值为 null。

如果得到`COleDateTime`值超出可接受的值，此状态的边界`COleDateTime`值设置为无效。

如果任一操作数无效且不为 null，其他的生成状态`COleDateTime`值无效。

有关有效、 无效和 null 的状态值的详细信息，请参阅[m_status](#m_status)成员变量。

**+=** 并**-=** 运算符将断言如果`COleDateTime`对象设置为 null。 请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)有关的示例。

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_date"></a>  COleDateTime::operator 日期

将转换`ColeDateTime`值到`DATE`。

```
operator DATE() const throw();
```

### <a name="remarks"></a>备注

此运算符返回`DATE`对象，其值复制从此`COleDateTime`对象。 有关实现的详细信息`DATE`对象，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

`DATE`运算符将断言如果`COleDateTime`对象设置为 null。 请参阅[COleDateTime 关系运算符](#coledatetime_relational_operators)有关的示例。

##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime

分析字符串中读取日期/时间值。

```
bool ParseDateTime(  
LPCTSTR lpszDate,
DWORD dwFlags = 0,
LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>参数

*lpszDate*  
指向以 null 结尾的字符串，这是要分析的指针。 有关详细信息，请参阅“备注”。

*dwFlags*  
指示用于区域设置和分析的标志。 一个或多个下列标志：

- LOCALE_NOUSEROVERRIDE 使用系统默认区域设置，而不是自定义用户设置。

- VAR_TIMEVALUEONLY 在分析过程中忽略日期部分。

- VAR_DATEVALUEONLY 在分析过程中忽略时间部分。

*lcid*  
指示要使用用于转换的区域设置 ID。

### <a name="return-value"></a>返回值

如果已成功将字符串转换为日期/时间值，否则为 FALSE，则返回 TRUE。

### <a name="remarks"></a>备注

如果字符串是否成功转换为日期/时间值，此设置的值`COleDateTime`对象设置为该值，并且其状态设置为有效。

> [!NOTE]
>  年份值必须介于 100 和 9999 之间 （含）。

*LpszDate*参数可以采用各种格式。 例如，以下字符串包含可接受的日期/时间格式：

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

请注意，是否可以接受的转换为日期/时间值的字符串格式，还将影响的区域设置 ID。

对于 VAR_DATEVALUEONLY，时间值设置为 0 或午夜的时间。 对于 VAR_TIMEVALUEONLY，日期值设置为日期 0，这意味着 1899 年 12 月 30。

如果无法为日期/时间值转换字符串或数值溢出，此状态时出现`COleDateTime`对象无效。

有关边界和实现详细信息`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="setdate"></a>  COleDateTime::SetDate

设置此日期`COleDateTime`对象。

```
int SetDate(  
int nYear,
int nMonth,
int nDay) throw();
```

### <a name="parameters"></a>参数

*nYear*， *nMonth*，*第几日*  
指示日期组件复制到此`COleDateTime`对象。

### <a name="return-value"></a>返回值

如果此值`COleDateTime`设置对象成功; 否则为 1。 此返回值取决于`DateTimeStatus`枚举类型。 有关详细信息，请参阅[SetStatus](#setstatus)成员函数。

### <a name="remarks"></a>备注

日期设置为指定的值。 时间设置为时间 0，午夜。

请参阅下表中的参数值的边界：

|参数|边界|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*第几日*|0 - 31|

如果每月天数溢出，它将转换为下个月和月份的正确天，和/或年就会相应地增加。 日期值为零指示上一个月份的最后一天。 行为等同于`SystemTimeToVariantTime`。

如果参数指定的日期值不是有效的该对象的状态设置为`COleDateTime::invalid`。 应使用[GetStatus](#getstatus)若要检查的有效性`DATE`值，并不应假定的值[m_dt](#m_dt)将保持不变。

下面是日期值的一些示例：

|*nYear*|*nMonth*|*第几日*|“值”|
|-------------|--------------|------------|-----------|
|2000|2|29|29 2000 年 2 月|
|1776|7|4|4 年 7 月圣瓦伦丁节|
|1925|4|35|35 年 4 月 1925 （无效的日期）|
|10000|1|1|1 年 1 月 10000 （无效的日期）|

若要设置日期和时间，请参阅[COleDateTime::SetDateTime](#setdatetime)。

有关查询的此值的成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

设置日期和时间这`COleDateTime`对象。

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

*nYear*， *nMonth*，*第几日*，*几点*， *nMin*， *nSec*  
指示要复制到此的日期和时间组件`COleDateTime`对象。

### <a name="return-value"></a>返回值

如果此值`COleDateTime`设置对象成功; 否则为 1。 此返回值取决于`DateTimeStatus`枚举类型。 有关详细信息，请参阅[SetStatus](#setstatus)成员函数。

### <a name="remarks"></a>备注

请参阅下表中的参数值的边界：

|参数|边界|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*第几日*|0 - 31|
|*几点*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果每月天数溢出，它将转换为下个月和月份的正确天，和/或年就会相应地增加。 日期值为零指示上一个月份的最后一天。 行为等同于[SystemTimeToVariantTime](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-systemtimetovarianttime)。

如果参数指定的日期或时间值不是有效的该对象的状态设置为无效，并且此对象的值不会更改。

下面是时间值的一些示例：

|*几点*|*nMin*|*nSec*|“值”|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|无效|
|9|60|0|无效|

下面是日期值的一些示例：

|*nYear*|*nMonth*|*第几日*|“值”|
|-------------|--------------|------------|-----------|
|1995|4|15|1995 年 4 月 15日|
|1789|7|14|17 年 7 月版|
|1925|2|30|无效|
|10000|1|1|无效|

若要设置的日期，请参阅[COleDateTime::SetDate](#setdate)。 若要设置的时间仅，请参阅[COleDateTime::SetTime](#settime)。

有关查询的此值的成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

有关示例，请参阅[GetStatus](#getstatus)。

##  <a name="setstatus"></a>  COleDateTime::SetStatus

设置此状态`COleDateTime`对象。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>参数

*status*  
为此新的状态值`COleDateTime`对象。

### <a name="remarks"></a>备注

*状态*参数值由定义`DateTimeStatus`枚举中定义的类型`COleDateTime`类。 请参阅[COleDateTime::GetStatus](#getstatus)有关详细信息。

> [!CAUTION]
>  此函数是针对高级编程情况。 此函数不会更改此对象中的数据。 通常将用于将状态设置为**null**或**无效**。 请注意，赋值运算符 ([运算符 =](#eq)) 和[SetDateTime](#setdatetime)设置基于源值的对象的状态。

### <a name="example"></a>示例

有关示例，请参阅[GetStatus](#getstatus)。

##  <a name="settime"></a>  COleDateTime::SetTime

设置此时间`COleDateTime`对象。

```
int SetTime(  
int nHour,
int nMin,
int nSec) throw();
```

### <a name="parameters"></a>参数

*几点*， *nMin*， *nSec*  
指示时间组件复制到此`COleDateTime`对象。

### <a name="return-value"></a>返回值

如果此值`COleDateTime`设置对象成功; 否则为 1。 此返回值取决于`DateTimeStatus`枚举类型。 有关详细信息，请参阅[SetStatus](#setstatus)成员函数。

### <a name="remarks"></a>备注

时间设置为指定的值。 日期设置为日期 0，这意味着 1899 年 12 月 30。

请参阅下表中的参数值的边界：

|参数|边界|
|---------------|------------|
|*几点*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果的时间由参数指定值不是有效的该对象的状态设置为无效，并且此对象的值不会更改。

下面是时间值的一些示例：

|*几点*|*nMin*|*nSec*|“值”|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|无效|
|9|60|0|无效|

若要设置日期和时间，请参阅[COleDateTime::SetDateTime](#setdatetime)。

有关查询的此值的成员函数的信息`COleDateTime`对象，请参阅以下成员函数：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

有关更多信息的边界`COleDateTime`值，请参阅文章[日期和时间： 自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

有关示例，请参阅[SetDate](#setdate)。

## <a name="see-also"></a>请参阅

[COleVariant 类](../../mfc/reference/colevariant-class.md)   
[CTime 类](../../atl-mfc-shared/reference/ctime-class.md)   
[CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)   
[层次结构图表](../../mfc/hierarchy-chart.md)   
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)

