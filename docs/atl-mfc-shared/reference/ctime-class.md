---
title: CTime 类
ms.date: 10/18/2018
f1_keywords:
- CTime
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: a73baab3e43467b76c1b4e3592314a4323d22ffb
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893972"
---
# <a name="ctime-class"></a>CTime 类

表示一个绝对时间和日期。

## <a name="syntax"></a>语法

```
class CTime
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CTime::CTime](#ctime)|构造`CTime`以各种方式的对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CTime::Format](#format)|将转换`CTime`格式化的字符串对象 — 基于本地时区。|
|[CTime::FormatGmt](#formatgmt)|将转换`CTime`格式化的字符串对象 — UTC 为基础。|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|将时间信息存储在转换`CTime`对象与 Win32 兼容 DBTIMESTAMP 结构。|
|[CTime::GetAsSystemTime](#getassystemtime)|将时间信息存储在转换`CTime`对象与 Win32 兼容[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构。|
|[CTime::GetCurrentTime](#getcurrenttime)|创建`CTime`对象，表示当前时间 （静态成员函数）。|
|[CTime::GetDay](#getday)|返回由一天表示`CTime`对象。|
|[CTime::GetDayOfWeek](#getdayofweek)|返回表示星期几`CTime`对象。|
|[CTime::GetGmtTm](#getgmttm)|分解`CTime`对象组件 — UTC 为基础。|
|[CTime::GetHour](#gethour)|返回表示的小时`CTime`对象。|
|[CTime::GetLocalTm](#getlocaltm)|分解`CTime`为组件的对象，根据本地时区。|
|[CTime::GetMinute](#getminute)|返回表示分钟`CTime`对象。|
|[CTime::GetMonth](#getmonth)|返回由表示的当月`CTime`对象。|
|[CTime::GetSecond](#getsecond)|返回由第二个`CTime`对象。|
|[CTime::GetTime](#gettime)|返回 **__time64_t**值给定`CTime`对象。|
|[CTime::GetYear](#getyear)|返回所表示的年份`CTime`对象。|
|[CTime::Serialize64](#serialize64)|序列化或从存档的数据。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator + -](#operator_add_-)|这些运算符，加法和减法`CTimeSpan`和`CTime`对象。|
|[operator +=, -=](#operator_add_eq_-_eq)|这些运算符，加法和减法`CTimeSpan`对象与此`CTime`对象。|
|[operator =](#operator_eq)|赋值运算符。|
|[运算符 = =、 <，等等。](#ctime_comparison_operators)|比较运算符。|

## <a name="remarks"></a>备注

`CTime` 没有基类。

`CTime` 值基于协调世界时 (UTC)，这等同于协调世界时 （格林威治标准时间，格林威治标准时间）。 请参阅[时间管理](../../c-runtime-library/time-management.md)有关如何确定时区信息。

当您创建`CTime`对象，设置`nDST`参数为 0 以指示标准时间是否生效，或到的值大于 0，表示该夏令时是否生效，或为一个值小于零，具有 C 运行时库代码这么做e 标准时间还是夏令时是否生效。 `tm_isdst` 是必填字段。 如果未设置，其值未定义和返回值从[mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)是不可预知的。 如果`timeptr`指向以前调用返回 tm 结构[asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)， [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)，或[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)，则`tm_isdst`字段包含正确的值。

伴生类， [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)，表示时间间隔。

`CTime`和`CTimeSpan`类并不设计用于派生。 由于没有虚函数的大小`CTime`和`CTimeSpan`对象是完全 8 个字节。 大多数成员函数是内联。

> [!NOTE]
>  上部日期限制为 12/31/3000。 较低的限制为 1970 年 1 月 1 日格林威治标准时间上午 12:00:00。

有关使用详细信息`CTime`，请参阅文章[日期和时间](../../atl-mfc-shared/date-and-time.md)，和[时间管理](../../c-runtime-library/time-management.md)运行时库参考中。

> [!NOTE]
>  `CTime`结构从 MFC 7.1 更改为 MFC 8.0。 如果序列化`CTime`结构的**运算符 <<** 在 MFC 8.0 或更高版本下，生成的文件不会在较旧版本的 MFC 中阅读。

## <a name="requirements"></a>要求

**标头：** atltime.h

##  <a name="ctime_comparison_operators"></a>  CTime 比较运算符

比较运算符。

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>参数

*time*<br/>
要比较的 `CTime` 对象。

### <a name="return-value"></a>返回值

这些运算符比较两个绝对时间并返回 TRUE，如果条件为 true;否则为 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>  CTime::CTime

创建一个新`CTime`对象初始化使用指定的时间。

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>参数

*timeSrc*<br/>
指示`CTime`已存在的对象。

*time*<br/>
一个`__time64_t`时间值，该值是自 1970 年 1 月 1 日 UTC 之后的秒数。 请注意这将调整为本地时间。 例如，如果位于纽约和创建`CTime`通过将为 0 时，参数传递的对象[CTime::GetMonth](#getmonth)将返回 12。

*nYear*， *nMonth*，*第几日*，*几点*， *nMin*， *nSec*<br/>
指示要复制到新的日期和时间值`CTime`对象。

*nDST*<br/>
指示夏令时是否生效。 可以具有三个值之一：

- *nDST*设置为 0Standard 时间是否生效。

- *nDST*设置为值大于 0Daylight 实际上是节省时间。

- *nDST*设置为小于 0The 默认的值。 自动计算标准时间还是夏令时是否生效。

*wDosDate*， *wDosTime*<br/>
MS-DOS 日期和时间值转换为日期/时间值并复制到新`CTime`对象。

*st*<br/>
一个[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构转换为日期/时间值并复制到新`CTime`对象。

*ft*<br/>
一个[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)结构转换为日期/时间值并复制到新`CTime`对象。

*dbts*<br/>
对包含当前本地时间的 DBTIMESTAMP 结构的引用。

### <a name="remarks"></a>备注

下面描述了每个构造函数：

- `CTime();` 构造未初始化`CTime`对象。 此构造函数，可定义`CTime`对象数组。 你应初始化此类数组与之前使用的有效时间。

- `CTime( const CTime& );` 构造`CTime`从另一个对象`CTime`值。

- `CTime( __time64_t );` 构造`CTime`对象从 **__time64_t**类型。 此构造函数需要 UTC 时间，并将结果存储在之前将结果转换为本地时间。

- `CTime( int, int, ...);` 构造`CTime`从每个组件的本地时间组件的对象限制为以下范围：

   |组件|范围|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   此构造函数生成相应的转换为 UTC。 Microsoft 基础类库的调试版本断言，如果一个或多个时间组件不在范围。 你必须验证之前调用的参数。 此构造函数需要本地时间。

- `CTime( WORD, WORD );` 构造`CTime`从指定的 MS-DOS 日期和时间值的对象。 此构造函数需要本地时间。

- `CTime( const SYSTEMTIME& );` 构造`CTime`对象从`SYSTEMTIME`结构。 此构造函数需要本地时间。

- `CTime( const FILETIME& );` 构造`CTime`对象从`FILETIME`结构。 您很可能不会使用`CTime FILETIME`直接初始化。 如果您使用`CFile`对象来处理一个文件，`CFile::GetStatus`为你通过检索文件时间戳`CTime`使用对象初始化`FILETIME`结构。 此构造函数采用基于 UTC 的时间，并自动将值转换为本地时间，将结果存储在之前。

   > [!NOTE]
   > 构造函数使用`DBTIMESTAMP`参数包括 OLEDB.h 时才可用。

有关详细信息，请参阅[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)并[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) Windows SDK 中的结构。 另请参阅[MS-DOS 日期和时间](/windows/desktop/SysInfo/ms-dos-date-and-time)Windows SDK 中的条目。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>  CTime::Format

调用此成员函数来创建日期时间值的格式化表示形式。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*pszFormat*<br/>
格式设置字符串类似于`printf`格式设置字符串。 格式设置代码，前面有百分比 (`%`) 登录，将替换为相应`CTime`组件。 格式设置字符串中的其他字符被复制到返回的字符串不变。 请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)的格式设置代码的列表。

*nFormatID*<br/>
用于标识此格式的字符串的 ID。

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含带格式的时间。

### <a name="remarks"></a>备注

如果此状态`CTime`对象为 null，则返回值为空字符串。

此方法将引发异常，如果要设置格式的日期时间值的范围从 1970 年 1 月 1 日通过 3000 年 12 月 31 日午夜协调世界时 (UTC)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>  CTime::FormatGmt

生成对应于此的格式化的字符串`CTime`对象。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*pszFormat*<br/>
指定的格式设置字符串类似于`printf`格式设置字符串。 请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)有关详细信息。

*nFormatID*<br/>
用于标识此格式的字符串的 ID。

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)包含带格式的时间。

### <a name="remarks"></a>备注

时间值不会转换，因此反映 UTC。

此方法将引发异常，如果要设置格式的日期时间值的范围从 1970 年 1 月 1 日通过 3000 年 12 月 31 日午夜协调世界时 (UTC)。

### <a name="example"></a>示例

有关示例，请参阅[CTime::Format](#format)。

##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP

调用此成员函数将转换中存储的时间信息`CTime`对象与 Win32 兼容 DBTIMESTAMP 结构。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>参数

*dbts*<br/>
对包含当前本地时间的 DBTIMESTAMP 结构的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

将所生成的时间存储在被引用*dbts*结构。 `DBTIMESTAMP`由此函数初始化的数据结构将具有其`fraction`成员设置为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime

调用此成员函数将转换中存储的时间信息`CTime`对象与 Win32 兼容[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>参数

*timeDest*<br/>
对引用[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)结构，它将保存转换后的日期/时间值的`CTime`对象。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

`GetAsSystemTime` 将所生成的时间存储在被引用*timeDest*结构。 `SYSTEMTIME`由此函数初始化的数据结构将具有其`wMilliseconds`成员设置为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime

返回`CTime`对象，表示当前时间。

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>备注

返回当前系统日期和时间以协调世界时 (UTC)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>  CTime::GetDay

返回由一天表示`CTime`对象。

```
int GetDay() const throw();
```

### <a name="return-value"></a>返回值

返回月份，基于本地时间，范围从 1 到 31 天。

### <a name="remarks"></a>备注

此函数将调用`GetLocalTm`，它使用的内部的静态分配的缓冲区。 此缓冲区中的数据覆盖由于调用其他`CTime`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek

返回表示星期几`CTime`对象。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>返回值

返回基于本地时间; 星期几1 = 星期日，2 = 星期一，7 = 星期六。

### <a name="remarks"></a>备注

此函数将调用`GetLocalTm`，它使用内部以静态方式已分配的缓冲区。 此缓冲区中的数据覆盖由于调用其他`CTime`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>  CTime::GetGmtTm

获取**struct tm** ，其中包含的包含在此时间分解`CTime`对象。

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>参数

*ptm*<br/>
指向将接收时间数据的缓冲区。 如果该指针为 NULL，将引发异常。

### <a name="return-value"></a>返回值

指向已填写的指针**struct tm** include 文件时间中定义。H. 请参阅[gmtime，_gmtime32，_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)结构布局。

### <a name="remarks"></a>备注

`GetGmtTm` 返回 UTC。

*ptm*不能为 NULL。 如果你想要还原到旧行为，在其中*ptm*可以为 NULL，以指示内部，应使用静态分配的缓冲区，然后取消定义 _SECURE_ATL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>  CTime::GetHour

返回表示的小时`CTime`对象。

```
int GetHour() const throw();
```

### <a name="return-value"></a>返回值

返回表示小时，基于本地时间，从 0 到 23 范围内。

### <a name="remarks"></a>备注

此函数将调用`GetLocalTm`，它使用内部以静态方式已分配的缓冲区。 此缓冲区中的数据覆盖由于调用其他`CTime`成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>  CTime::GetLocalTm

获取**struct tm**包含的包含在此时间分解`CTime`对象。

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>参数

*ptm*<br/>
指向将接收时间数据的缓冲区。 如果该指针为 NULL，将引发异常。

### <a name="return-value"></a>返回值

指向已填写的指针**struct tm** include 文件时间中定义。H. 请参阅[gmtime，_gmtime32，_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)结构布局。

### <a name="remarks"></a>备注

`GetLocalTm` 返回本地时间。

*ptm*不能为 NULL。 如果你想要还原到旧行为，在其中*ptm*可以为 NULL，以指示内部，应使用静态分配的缓冲区，然后取消定义 _SECURE_ATL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>  CTime::GetMinute

返回表示分钟`CTime`对象。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>返回值

返回分钟，基于本地时间，在范围 0 到 59 之间。

### <a name="remarks"></a>备注

此函数将调用`GetLocalTm`，它使用内部以静态方式已分配的缓冲区。 此缓冲区中的数据覆盖由于调用其他`CTime`成员函数。

### <a name="example"></a>示例

有关示例，请参阅[GetHour](#gethour)。

##  <a name="getmonth"></a>  CTime::GetMonth

返回由表示的当月`CTime`对象。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>返回值

返回基于本地时间，范围从 1 到 12 的月份 (1 = 年 1 月)。

### <a name="remarks"></a>备注

此函数将调用`GetLocalTm`，它使用内部以静态方式已分配的缓冲区。 此缓冲区中的数据覆盖由于调用其他`CTime`成员函数。

### <a name="example"></a>示例

有关示例，请参阅[GetDay](#getday)。

##  <a name="getsecond"></a>  CTime::GetSecond

返回由第二个`CTime`对象。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>返回值

返回第二类是基于本地时间，在范围 0 到 59 之间。

### <a name="remarks"></a>备注

此函数将调用`GetLocalTm`，它使用内部以静态方式已分配的缓冲区。 此缓冲区中的数据覆盖由于调用其他`CTime`成员函数。

### <a name="example"></a>示例

有关示例，请参阅[GetHour](#gethour)。

##  <a name="gettime"></a>  CTime::GetTime

返回 **__time64_t**值给定`CTime`对象。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>返回值

`GetTime` 将返回当前之间的秒数`CTime`对象和自 1970 年 1 月 1 日。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>  CTime::GetYear

返回所表示的年份`CTime`对象。

```
int GetYear();
```

### <a name="return-value"></a>返回值

返回年份，基于本地时间，在范围内年 1 月 1,1970 到 2038 年 1 月 18，（含）。

### <a name="remarks"></a>备注

此函数将调用`GetLocalTm`，它使用内部以静态方式已分配的缓冲区。 此缓冲区中的数据覆盖由于调用其他`CTime`成员函数。

### <a name="example"></a>示例

有关示例，请参阅[GetDay](#getday)。

##  <a name="operator_eq"></a>  CTime::operator =

赋值运算符。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>参数

*time*<br/>
新的日期/时间值中。

### <a name="return-value"></a>返回值

已更新`CTime`对象。

### <a name="remarks"></a>备注

此重载的赋值运算符复制到此源时间`CTime`对象。 中的内部时间存储`CTime`对象是独立于时区。 在分配期间不需要时区转换。

##  <a name="operator_add_-"></a>  CTime::operator +、-

这些运算符，加法和减法`CTimeSpan`和`CTime`对象。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>参数

*timeSpan*<br/>
`CTimeSpan`要添加或减去的对象。

*time*<br/>
`CTime`要减去的对象。

### <a name="return-value"></a>返回值

一个`CTime`或`CTimeSpan`对象，表示操作的结果。

### <a name="remarks"></a>备注

`CTime` 对象表示绝对时间`CTimeSpan`对象表示相对时间。 前两个运算符使您得以，加法和减法`CTimeSpan`对象与`CTime`对象。 第三个运算符可以减去`CTime`对象从另一个用来生成`CTimeSpan`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTime::operator + =、 =

这些运算符，加法和减法`CTimeSpan`对象与此`CTime`对象。

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
`CTimeSpan`要添加或减去的对象。

### <a name="return-value"></a>返回值

已更新`CTime`对象。

### <a name="remarks"></a>备注

这些运算符使您得以，加法和减法`CTimeSpan`对象与此`CTime`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>  CTime::Serialize64

> [!NOTE]
> 此方法才在 MFC 项目中可用。

序列化到或从存档的成员变量与关联的数据。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
`CArchive`你想要更新的对象。

### <a name="return-value"></a>返回值

已更新`CArchive`对象。

## <a name="see-also"></a>请参阅

[asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s、_ftime32_s、_ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
