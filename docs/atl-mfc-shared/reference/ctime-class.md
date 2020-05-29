---
title: CTime 类
ms.date: 10/18/2018
f1_keywords:
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
ms.openlocfilehash: e6e471fe648c5fa370cce750e8569e158eb1ffe4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317569"
---
# <a name="ctime-class"></a>CTime 类

表示绝对时间和日期。

## <a name="syntax"></a>语法

```
class CTime
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[时间：：CTime](#ctime)|以各种方式构造`CTime`对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C时间：：格式](#format)|根据本地时区`CTime`将对象转换为格式化字符串。|
|[时间：：格式Gmt](#formatgmt)|根据 UTC`CTime`将对象转换为格式化字符串。|
|[C时间：获取 ASDBTIMESTAMP](#getasdbtimestamp)|将存储在对象中`CTime`的时间信息转换为与 Win32 兼容的 DBTIMESTAMP 结构。|
|[时间：：获取系统时间](#getassystemtime)|将存储在对象中`CTime`的时间信息转换为与 Win32 兼容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构。|
|[时间：：获取当前时间](#getcurrenttime)|创建`CTime`表示当前时间的对象（静态成员函数）。|
|[C时间：：获取日](#getday)|返回对象表示的`CTime`天。|
|[时间：：获取周](#getdayofweek)|返回由`CTime`对象表示的星期一。|
|[时间：：获取GmtTm](#getgmttm)|根据 UTC`CTime`将对象分解为组件。|
|[时间：：获取小时](#gethour)|返回对象表示的`CTime`小时。|
|[时间：：获取本地Tm](#getlocaltm)|根据本地时区`CTime`将对象分解为组件。|
|[C时间：：获取分钟](#getminute)|返回对象表示的`CTime`分钟。|
|[时间：：获取月份](#getmonth)|返回对象表示的`CTime`月份。|
|[C时间：：获取第二](#getsecond)|返回由对象表示的第二`CTime`个。|
|[时间：：获取时间](#gettime)|返回给定 **__time64_t**`CTime`对象的__time64_t值。|
|[C时间：：获取年份](#getyear)|返回对象表示的`CTime`年份。|
|[时间：：序列化64](#serialize64)|将数据序列化到存档或从存档中序列化。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 = -](#operator_add_-)|这些运算符添加、减去`CTimeSpan`对象`CTime`。|
|[运算符 *， -]](#operator_add_eq_-_eq)|这些运算符在此`CTimeSpan``CTime`对象中添加和减去对象。|
|[运算符 |](#operator_eq)|分配运算符。|
|[运算符 *，< 等。](#ctime_comparison_operators)|比较运算符。|

## <a name="remarks"></a>备注

`CTime`没有基类。

`CTime`值基于协调的通用时间 （UTC），这相当于协调通用时间（格林威治标准时间、GMT）。 有关如何确定时区的信息，请参阅[时间管理](../../c-runtime-library/time-management.md)。

创建`CTime`对象时，将`nDST`参数设置为 0 以指示标准时间有效，或设置为大于 0 的值以指示夏令时有效，或设置为小于零的值，以便 C 运行时库代码计算标准时间或夏令时是否有效。 `tm_isdst` 是必填字段。 如果未设置，则其值未定义，[来自 mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)的返回值不可预测。 如果`timeptr`指向以前调用[asctime_s、_gmtime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)或[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)返回的[_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)tm 结构，则`tm_isdst`该字段包含正确的值。

配套类[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)表示时间间隔。

和`CTime``CTimeSpan`类不是为派生而设计的。 由于没有虚拟函数，因此 和`CTime``CTimeSpan`对象的大小正好为 8 个字节。 大多数成员函数是内联的。

> [!NOTE]
> 上限为 12/31/3000。 下限为 1970 年 1 月 1 日 12：00：00 GMT。

有关使用`CTime`的详细信息，请参阅"运行时库参考"中的文章[日期和时间](../../atl-mfc-shared/date-and-time.md)以及[时间管理](../../c-runtime-library/time-management.md)。

> [!NOTE]
> 结构`CTime`从 MFC 7.1 更改为 MFC 8.0。 如果使用 MFC `CTime` 8.0 或更高版本的**运算符 <<** 对结构进行序列化，则生成的文件在旧版本的 MFC 上是不可读的。

## <a name="requirements"></a>要求

**标题：** atltime.h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a>CTime 比较运算符

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

如果条件为 true，这些运算符比较两个绝对时间并返回 TRUE;否则 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a>时间：：CTime

创建使用指定`CTime`时间初始化的新对象。

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

*时间Src*<br/>
指示已`CTime`存在的对象。

*time*<br/>
`__time64_t`时间值，即 1970 年 1 月 1 日之后的秒数 UTC。 请注意，这将根据您的本地时间进行调整。 例如，如果您在纽约，并通过传递参数 0 来`CTime`创建对象[，CTime：：getMonth](#getmonth)将返回 12。

*nYear*， *nMonth*， *nDay*， *nHour*， *nMin*， *nSec*<br/>
指示要复制到新`CTime`对象的日期和时间值。

*nDST*<br/>
指示夏令时是否有效。 可以具有三个值之一：

- *nDST*设置为 0 标准时间有效。

- *nDST*设置为大于 0 夏令时的值有效。

- *nDST*设置为小于 0 的值默认值。 自动计算标准时间或夏令时是否有效。

*wDosDate*， *wDosTime*<br/>
要转换为日期/时间值并复制到新`CTime`对象的 MS-DOS 日期和时间值。

*圣*<br/>
要转换为日期/时间值并复制到新`CTime`对象的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构。

*英尺*<br/>
要转换为日期/时间值并复制到新`CTime`对象的[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。

*dbts*<br/>
对包含当前本地时间的 DBTIMESTAMP 结构的引用。

### <a name="remarks"></a>备注

下面将介绍每个构造函数：

- `CTime();`构造未初始化`CTime`的对象。 此构造函数允许您定义`CTime`对象数组。 在使用之前，应用有效时间初始化此类数组。

- `CTime( const CTime& );`从另一`CTime`个`CTime`值构造对象。

- `CTime( __time64_t );`从__time64_t类型`CTime`构造对象。 **__time64_t** 此构造函数需要 UTC 时间，并在存储结果之前将结果转换为本地时间。

- `CTime( int, int, ...);`构造来自本地`CTime`时间组件的对象，每个组件都受限制在以下范围：

   |组件|范围|
   |---------------|-----------|
   |*n年*|1970-3000|
   |*n月*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   此构造函数进行适当的转换到 UTC。 Microsoft 基础类库的调试版本断言一个或多个时间组件是否超过范围。 在调用之前，必须验证参数。 此构造函数需要本地时间。

- `CTime( WORD, WORD );`从指定的`CTime`MS-DOS 日期和时间值构造对象。 此构造函数需要本地时间。

- `CTime( const SYSTEMTIME& );`从`SYSTEMTIME`结构构造`CTime`对象。 此构造函数需要本地时间。

- `CTime( const FILETIME& );`从`FILETIME`结构构造`CTime`对象。 您很可能不会直接使用`CTime FILETIME`初始化。 如果使用`CFile`对象操作文件，则`CFile::GetStatus`通过使用`CTime``FILETIME`结构初始化的对象检索文件时间戳。 此构造函数假定基于 UTC 的时间，并在存储结果之前自动将值转换为本地时间。

   > [!NOTE]
   > 仅当包含 OLEDB.h 时，使用`DBTIMESTAMP`参数的构造函数才可用。

有关详细信息，请参阅 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。 另请参阅 Windows SDK 中的[MS-DOS 日期和时间](/windows/win32/SysInfo/ms-dos-date-and-time)条目。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a>C时间：：格式

调用此成员函数以创建日期时间值的格式化表示形式。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*psz格式*<br/>
类似于格式字符串的`printf`格式字符串。 格式代码（前面为百分比 （`%`） 符号，由相应的`CTime`组件替换。 格式字符串中的其他字符将复制到返回的字符串。 有关格式代码列表，请参阅运行时函数[时刻。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*nFormatID*<br/>
标识此格式的字符串的 ID。

### <a name="return-value"></a>返回值

包含格式化时间的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

如果此`CTime`对象的状态为 null，则返回值为空字符串。

如果格式化的日期和时间值范围不是从 1970 年 1 月 1 日午夜到 3000 年 12 月 31 日通用协调时间 （UTC），则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a>时间：：格式Gmt

生成对应于此`CTime`对象的格式化字符串。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*psz格式*<br/>
指定类似于格式字符串的`printf`格式字符串。 有关详细信息，请参阅运行时函数[时刻。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*nFormatID*<br/>
标识此格式的字符串的 ID。

### <a name="return-value"></a>返回值

包含格式化时间的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>备注

时间值不会转换，因此反映 UTC。

如果格式化的日期和时间值范围不是从 1970 年 1 月 1 日午夜到 3000 年 12 月 31 日通用协调时间 （UTC），则此方法将引发异常。

### <a name="example"></a>示例

请参阅[CTime：：格式](#format)的示例。

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>C时间：获取 ASDBTIMESTAMP

调用此成员函数将存储在对象中`CTime`的时间信息转换为与 Win32 兼容的 DBTIMESTAMP 结构。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>参数

*dbts*<br/>
对包含当前本地时间的 DBTIMESTAMP 结构的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

将结果的时间存储在引用的*dbts*结构中。 此`DBTIMESTAMP`函数初始化的数据结构将使其`fraction`成员设置为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a>时间：：获取系统时间

调用此成员函数将存储在对象中`CTime`的时间信息转换为与 Win32 兼容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>参数

*时间时间*<br/>
对将保存`CTime`对象转换的日期/时间值的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的引用。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

`GetAsSystemTime`将生成的时间存储在引用*的时间最点一元*结构中。 此`SYSTEMTIME`函数初始化的数据结构将使其`wMilliseconds`成员设置为零。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a>时间：：获取当前时间

返回表示`CTime`当前时间的对象。

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>备注

在协调通用时间 （UTC） 中返回当前系统日期和时间。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a>C时间：：获取日

返回对象表示的`CTime`天。

```
int GetDay() const throw();
```

### <a name="return-value"></a>返回值

返回每月的一天，基于本地时间，在范围 1 到 31 中。

### <a name="remarks"></a>备注

此函数调用`GetLocalTm`，它使用内部静态分配的缓冲区。 由于调用其他成员`CTime`函数，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a>时间：：获取周

返回由`CTime`对象表示的星期一。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>返回值

根据本地时间返回星期一;1 = 周日，2 = 星期一，到 7 = 星期六。

### <a name="remarks"></a>备注

此函数调用`GetLocalTm`，它使用内部静态分配的缓冲区。 由于调用其他成员`CTime`函数，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a>时间：：获取GmtTm

获取包含此`CTime`对象中包含的时间的分解**结构 tm。**

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>参数

*ptm*<br/>
指向将接收时间数据的缓冲区。 如果此指针为 NULL，则引发异常。

### <a name="return-value"></a>返回值

指向包含文件 TIME 中定义的填充**结构 tm 的**指针。H。 有关结构布局，请参阅[gmtime、_gmtime32、_gmtime64。](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)

### <a name="remarks"></a>备注

`GetGmtTm`返回 UTC。

*ptm*不能为 NULL。 如果要还原到旧行为（其中*ptm*可以是 NULL 以指示应使用内部静态分配的缓冲区），则取消定义_SECURE_ATL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a>时间：：获取小时

返回对象表示的`CTime`小时。

```
int GetHour() const throw();
```

### <a name="return-value"></a>返回值

返回基于本地时间在范围 0 到 23 中的小时。

### <a name="remarks"></a>备注

此函数调用`GetLocalTm`，它使用内部静态分配的缓冲区。 由于调用其他成员`CTime`函数，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a>时间：：获取本地Tm

获取包含此`CTime`对象中包含的时间的分解**结构 tm。**

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>参数

*ptm*<br/>
指向将接收时间数据的缓冲区。 如果此指针为 NULL，则引发异常。

### <a name="return-value"></a>返回值

指向包含文件 TIME 中定义的填充**结构 tm 的**指针。H。 有关结构布局，请参阅[gmtime、_gmtime32、_gmtime64。](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)

### <a name="remarks"></a>备注

`GetLocalTm`返回本地时间。

*ptm*不能为 NULL。 如果要还原到旧行为（其中*ptm*可以是 NULL 以指示应使用内部静态分配的缓冲区），则取消定义_SECURE_ATL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a>C时间：：获取分钟

返回对象表示的`CTime`分钟。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>返回值

返回基于本地时间的范围 0 到 59 的分钟。

### <a name="remarks"></a>备注

此函数调用`GetLocalTm`，它使用内部静态分配的缓冲区。 由于调用其他成员`CTime`函数，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

## <a name="ctimegetmonth"></a><a name="getmonth"></a>时间：：获取月份

返回对象表示的`CTime`月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>返回值

返回基于本地时间的范围 1 到 12（1 = 1 月）的月份。

### <a name="remarks"></a>备注

此函数调用`GetLocalTm`，它使用内部静态分配的缓冲区。 由于调用其他成员`CTime`函数，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

## <a name="ctimegetsecond"></a><a name="getsecond"></a>C时间：：获取第二

返回由对象表示的第二`CTime`个。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>返回值

返回基于本地时间的第二个范围 0 到 59。

### <a name="remarks"></a>备注

此函数调用`GetLocalTm`，它使用内部静态分配的缓冲区。 由于调用其他成员`CTime`函数，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

## <a name="ctimegettime"></a><a name="gettime"></a>时间：：获取时间

返回给定 **__time64_t**`CTime`对象的__time64_t值。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>返回值

`GetTime`将返回当前`CTime`对象与 1970 年 1 月 1 日之间的秒数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a>C时间：：获取年份

返回对象表示的`CTime`年份。

```
int GetYear();
```

### <a name="return-value"></a>返回值

返回 1970 年 1 月 1 日至 2038 年 1 月 18 日（含）的年份，基于本地时间。

### <a name="remarks"></a>备注

此函数调用`GetLocalTm`，它使用内部静态分配的缓冲区。 由于调用其他成员`CTime`函数，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

## <a name="ctimeoperator-"></a><a name="operator_eq"></a>时间：：运算符 |

分配运算符。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>参数

*time*<br/>
新的日期/时间值。

### <a name="return-value"></a>返回值

更新`CTime`的对象。

### <a name="remarks"></a>备注

此重载赋值运算符将源时间复制到此`CTime`对象中。 `CTime`对象中的内部时间存储与时区无关。 在分配期间不需要时区转换。

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a>CTime：：运算符 +， -

这些运算符添加、减去`CTimeSpan`对象`CTime`。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>参数

*时间跨度*<br/>
要`CTimeSpan`添加或减去的对象。

*time*<br/>
要`CTime`减去的对象。

### <a name="return-value"></a>返回值

`CTime`表示操作结果`CTimeSpan`的对象。

### <a name="remarks"></a>备注

`CTime`对象表示绝对时间，`CTimeSpan`对象表示相对时间。 前两个运算符允许您在`CTimeSpan``CTime`对象中添加和减去对象。 第三个运算符允许您从另一`CTime`个对象中减去一个`CTimeSpan`对象以产生一个对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a>C时间：：运算符 *，-*

这些运算符在此`CTimeSpan``CTime`对象中添加和减去对象。

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
要`CTimeSpan`添加或减去的对象。

### <a name="return-value"></a>返回值

更新`CTime`的对象。

### <a name="remarks"></a>备注

这些运算符允许您在此`CTimeSpan``CTime`对象中添加和减去对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a>时间：：序列化64

> [!NOTE]
> 此方法仅在 MFC 项目中可用。

序列化与成员变量关联的存档或从存档中的数据。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
要`CArchive`更新的对象。

### <a name="return-value"></a>返回值

更新`CArchive`的对象。

## <a name="see-also"></a>另请参阅

[asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s、_ftime32_s、_ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
