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
ms.openlocfilehash: daf2a0d884a6b7a74b5edde2ed7db3b6aeea368d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491571"
---
# <a name="ctime-class"></a>CTime 类

表示绝对时间和日期。

## <a name="syntax"></a>语法

```
class CTime
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CTime：： CTime](#ctime)|以`CTime`多种方式构造对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CTime::Format](#format)|根据本地时区，将对象转换为带格式的字符串。`CTime`|
|[CTime::FormatGmt](#formatgmt)|`CTime`将对象转换为基于 UTC 的格式化字符串。|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|将`CTime`对象中存储的时间信息转换为与 Win32 兼容的 DBTIMESTAMP 结构。|
|[CTime::GetAsSystemTime](#getassystemtime)|将`CTime`对象中存储的时间信息转换为与 Win32 兼容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构。|
|[CTime::GetCurrentTime](#getcurrenttime)|创建一个`CTime`对象，该对象表示当前时间（静态成员函数）。|
|[CTime::GetDay](#getday)|返回由`CTime`对象表示的日期。|
|[CTime::GetDayOfWeek](#getdayofweek)|返回`CTime`对象所表示的周中的某一天。|
|[CTime::GetGmtTm](#getgmttm)|根据 UTC 将`CTime`对象分解为组件。|
|[CTime::GetHour](#gethour)|返回由`CTime`对象表示的小时。|
|[CTime::GetLocalTm](#getlocaltm)|根据本地时区，将对象分解为组件。`CTime`|
|[CTime：： GetMinute](#getminute)|返回由`CTime`对象表示的分钟数。|
|[CTime::GetMonth](#getmonth)|返回由`CTime`对象表示的月份。|
|[CTime::GetSecond](#getsecond)|返回由`CTime`对象表示的第二个。|
|[CTime::GetTime](#gettime)|返回给定 `CTime`对象的 __time64_t 值。|
|[CTime：： GetYear](#getyear)|返回由`CTime`对象表示的年份。|
|[CTime::Serialize64](#serialize64)|在存档中序列化数据。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator +-](#operator_add_-)|这些运算符添加并减去`CTimeSpan`和`CTime`对象。|
|[operator +=, -=](#operator_add_eq_-_eq)|这些运算符可在此`CTimeSpan` `CTime`对象中添加和减去对象。|
|[operator =](#operator_eq)|赋值运算符。|
|[operator = =、< 等。](#ctime_comparison_operators)|比较运算符。|

## <a name="remarks"></a>备注

`CTime`没有基类。

`CTime`值基于协调世界时（UTC），这相当于协调世界时（格林尼治标准时间）。 有关如何确定时区的信息，请参阅[时间管理](../../c-runtime-library/time-management.md)。

创建`CTime`对象时，请`nDST`将参数设置为0，以指示标准时间有效，或设置为大于0的值以指示夏令时有效，或设置为小于零的值，以使 C 运行时库代码计算机e 标准时间还是夏令时有效。 `tm_isdst` 是必填字段。 如果未设置，则未定义其值，并且[mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)中的返回值是不可预知的。 如果`timeptr`指向先前对[asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)、 [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)或[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)的调用返回的 tm 结构，则`tm_isdst`字段将包含正确的值。

伴生类[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)表示时间间隔。

`CTime` 和`CTimeSpan`类不用于派生。 由于没有虚函数， `CTime`因此和`CTimeSpan`对象的大小正好为8个字节。 大多数成员函数是内联的。

> [!NOTE]
>  上限日期限制为12/31/3000。 下限为 1/1/1970 12:00:00 AM GMT。

有关使用`CTime`的详细信息，请参阅文章[日期和时间](../../atl-mfc-shared/date-and-time.md)和运行时库参考中的[时间管理](../../c-runtime-library/time-management.md)。

> [!NOTE]
>  `CTime`结构从 mfc 7.1 更改为 mfc 8.0。 如果使用运算符序列`CTime`化结构，则在 mfc 8.0 或更高版本下面 **< <** ，生成的文件将在较旧版本的 mfc 上不可读。

## <a name="requirements"></a>要求

**标头：** atltime

##  <a name="ctime_comparison_operators"></a>CTime 比较运算符

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

这些运算符比较两个绝对时间，如果条件为 true，则返回 TRUE;否则为 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>CTime：： CTime

使用指定时间`CTime`创建初始化的新对象。

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
指示已存在的对象。`CTime`

*time*<br/>
一个`__time64_t`时间值，表示1970年1月1日之后的秒数。 请注意，这会调整为你的本地时间。 例如，如果你位于纽约并通过传递参数0创建`CTime`一个对象，则[CTime：： GetMonth](#getmonth)将返回12。

*nYear*、 *nMonth*、 *nDay*、 *nHour*、 *nMin*、 *nSec*<br/>
指示要复制到新`CTime`对象中的日期和时间值。

*nDST*<br/>
指示夏令时是否有效。 可以具有以下三个值之一：

- *nDST*设置为 0Standard time 有效。

- *nDST*设置为大于0Daylight 节省时间的值生效。

- *nDST*设置为小于0The 默认值。 自动计算标准时间或夏令时是否有效。

*wDosDate*、 *wDosTime*<br/>
要转换为日期/时间值并将其复制到新`CTime`对象中的 MS-DOS 日期和时间值。

*st*<br/>
要转换为日期/时间值并将其复制到新的`CTime`对象中的 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 结构。

*ft*<br/>
要转换为日期/时间值并将其复制到新的`CTime`对象中的 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 结构。

*dbts*<br/>
对包含当前本地时间的 DBTIMESTAMP 结构的引用。

### <a name="remarks"></a>备注

每个构造函数如下所述：

- `CTime();`构造未初始化`CTime`的对象。 此构造函数允许您定义`CTime`对象数组。 使用之前，应使用有效的时间初始化此类数组。

- `CTime( const CTime& );`从另一个`CTime`值构造对象。`CTime`

- `CTime( __time64_t );`从 **__time64_t**类型构造对象。`CTime` 此构造函数需要 UTC 时间，并在存储结果之前将结果转换为本地时间。

- `CTime( int, int, ...);`从本地时间组件构造对象，每个组件都受限于以下范围：`CTime`

   |组件|范围|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   此构造函数使适当的转换为 UTC。 如果一个或多个时间组件超出范围，则 Microsoft 基础类库的调试版本断言。 必须在调用之前验证参数。 此构造函数应为本地时间。

- `CTime( WORD, WORD );`从指定的 MS-DOS 日期和时间值构造对象。`CTime` 此构造函数应为本地时间。

- `CTime( const SYSTEMTIME& );`从结构构造`CTime`对象 `SYSTEMTIME` 。 此构造函数应为本地时间。

- `CTime( const FILETIME& );`从结构构造`CTime`对象 `FILETIME` 。 您很可能不会直接`CTime FILETIME`使用初始化。 如果使用`CFile`对象来操作文件， `CFile::GetStatus`则通过使用`FILETIME`结构初始化的`CTime`对象检索文件时间戳。 此构造函数假设基于 UTC 的时间，并在存储结果之前自动将值转换为本地时间。

   > [!NOTE]
   > 仅当包含`DBTIMESTAMP` OLEDB 时，使用参数的构造函数才可用。

有关详细信息，请参阅 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。 另请参阅 Windows SDK 中的[MS-DOS 日期和时间](/windows/win32/SysInfo/ms-dos-date-and-time)条目。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>CTime：： Format

调用此成员函数以创建日期时间值的格式化表示形式。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*pszFormat*<br/>
格式字符串类似`printf`于格式设置字符串。 格式设置代码前面以百分号（`%`）符号替换为相应`CTime`的组件。 格式字符串中的其他字符将按原样复制到返回的字符串中。 有关格式设置代码的列表，请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

*nFormatID*<br/>
标识此格式的字符串的 ID。

### <a name="return-value"></a>返回值

包含格式化时间的[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>备注

如果此`CTime`对象的状态为 null，则返回值为空字符串。

如果要设置格式的日期时间值不是从1970年1月1日午夜到3000协调世界时（UTC），则此方法将引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>CTime：： FormatGmt

生成与此`CTime`对象相对应的格式化字符串。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>参数

*pszFormat*<br/>
指定类似于`printf`格式设置字符串的格式设置字符串。 有关详细信息，请参阅运行时函数[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

*nFormatID*<br/>
标识此格式的字符串的 ID。

### <a name="return-value"></a>返回值

包含格式化时间的[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>备注

不转换时间值，因此反映 UTC。

如果要设置格式的日期时间值不是从1970年1月1日午夜到3000协调世界时（UTC），则此方法将引发异常。

### <a name="example"></a>示例

请参阅[CTime：： Format](#format)的示例。

##  <a name="getasdbtimestamp"></a>CTime：： GetAsDBTIMESTAMP

调用此成员函数可将`CTime`对象中存储的时间信息转换为与 Win32 兼容的 DBTIMESTAMP 结构。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>参数

*dbts*<br/>
对包含当前本地时间的 DBTIMESTAMP 结构的引用。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

在引用的*dbts*结构中存储生成的时间。 此函数初始化的`fraction` 数据结构将其成员设置为零。`DBTIMESTAMP`

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>CTime：： GetAsSystemTime

调用此成员函数可将`CTime`对象中存储的时间信息转换为与 Win32 兼容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>参数

*timeDest*<br/>
对[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)结构的引用，该结构将保存`CTime`对象的转换日期/时间值。

### <a name="return-value"></a>返回值

若成功，则为 TRUE；否则为 FALSE。

### <a name="remarks"></a>备注

`GetAsSystemTime`在引用的*timeDest*结构中存储生成的时间。 此函数初始化的`wMilliseconds` 数据结构将其成员设置为零。`SYSTEMTIME`

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>CTime：： GetCurrentTime

返回表示当前时间的对象。`CTime`

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>备注

返回以协调世界时（UTC）的当前系统日期和时间。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>CTime：： GetDay

返回由`CTime`对象表示的日期。

```
int GetDay() const throw();
```

### <a name="return-value"></a>返回值

返回一个月中的第几天，根据本地时间，范围为1到31。

### <a name="remarks"></a>备注

此函数将`GetLocalTm`调用，该函数使用内部静态分配的缓冲区。 由于对其他`CTime`成员函数的调用，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>CTime：： GetDayOfWeek

返回`CTime`对象所表示的周中的某一天。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>返回值

基于当地时间返回一周中的第几天;1 = 星期日，2 = 星期一，7 = 星期六。

### <a name="remarks"></a>备注

此函数将`GetLocalTm`调用，该函数使用内部静态分配的缓冲区。 由于对其他`CTime`成员函数的调用，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>CTime：： GetGmtTm

获取一个**结构 tm** ，其中包含此`CTime`对象中包含的时间的分解。

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>参数

*ptm*<br/>
指向将接收时间数据的缓冲区。 如果此指针为 NULL，则会引发异常。

### <a name="return-value"></a>返回值

指向在包含文件时间中定义的已填充的**结构 tm**的指针。高. 有关结构布局，请参阅[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 。

### <a name="remarks"></a>备注

`GetGmtTm`返回 UTC。

*ptm*不能为 NULL。 如果要恢复到旧行为，在这种情况下， *ptm*可能为 NULL 以指示应使用内部静态分配的缓冲区，然后取消定义 _SECURE_ATL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>CTime：： GetHour

返回由`CTime`对象表示的小时。

```
int GetHour() const throw();
```

### <a name="return-value"></a>返回值

根据本地时间，返回介于0到23之间的小时。

### <a name="remarks"></a>备注

此函数将`GetLocalTm`调用，该函数使用内部静态分配的缓冲区。 由于对其他`CTime`成员函数的调用，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>CTime：： GetLocalTm

获取一个**结构 tm** ，其中包含此`CTime`对象中包含的时间的分解。

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>参数

*ptm*<br/>
指向将接收时间数据的缓冲区。 如果此指针为 NULL，则会引发异常。

### <a name="return-value"></a>返回值

指向在包含文件时间中定义的已填充的**结构 tm**的指针。高. 有关结构布局，请参阅[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 。

### <a name="remarks"></a>备注

`GetLocalTm`返回本地时间。

*ptm*不能为 NULL。 如果要恢复到旧行为，在这种情况下， *ptm*可能为 NULL 以指示应使用内部静态分配的缓冲区，然后取消定义 _SECURE_ATL。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>CTime：： GetMinute

返回由`CTime`对象表示的分钟数。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>返回值

返回从0到59范围内的本地时间的分钟数。

### <a name="remarks"></a>备注

此函数将`GetLocalTm`调用，该函数使用内部静态分配的缓冲区。 由于对其他`CTime`成员函数的调用，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

##  <a name="getmonth"></a>CTime：： GetMonth

返回由`CTime`对象表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>返回值

返回基于本地时间的月份，范围为1到12（1 = 1-1）。

### <a name="remarks"></a>备注

此函数将`GetLocalTm`调用，该函数使用内部静态分配的缓冲区。 由于对其他`CTime`成员函数的调用，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

##  <a name="getsecond"></a>CTime：： GetSecond

返回由`CTime`对象表示的第二个。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>返回值

根据本地时间，返回介于0到59范围内的第二个。

### <a name="remarks"></a>备注

此函数将`GetLocalTm`调用，该函数使用内部静态分配的缓冲区。 由于对其他`CTime`成员函数的调用，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetHour](#gethour)的示例。

##  <a name="gettime"></a>CTime：： GetTime

返回给定 `CTime`对象的 __time64_t 值。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>返回值

`GetTime`将返回当前`CTime`对象与1970年1月1日之间的秒数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>CTime：： GetYear

返回由`CTime`对象表示的年份。

```
int GetYear();
```

### <a name="return-value"></a>返回值

返回基于当地时间的年份，范围为1970年1月1日到2038年1月18日（含）。

### <a name="remarks"></a>备注

此函数将`GetLocalTm`调用，该函数使用内部静态分配的缓冲区。 由于对其他`CTime`成员函数的调用，此缓冲区中的数据将被覆盖。

### <a name="example"></a>示例

请参阅[GetDay](#getday)的示例。

##  <a name="operator_eq"></a>CTime：： operator =

赋值运算符。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>参数

*time*<br/>
新的日期/时间值。

### <a name="return-value"></a>返回值

已更新`CTime`的对象。

### <a name="remarks"></a>备注

此重载赋值运算符将源时间复制到此`CTime`对象中。 `CTime`对象中的内部时间存储独立于时区。 分配期间不需要时区转换。

##  <a name="operator_add_-"></a>CTime：： operator +，-

这些运算符添加并减去`CTimeSpan`和`CTime`对象。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>参数

*timeSpan*<br/>
要`CTimeSpan`添加或减去的对象。

*time*<br/>
要`CTime`减去的对象。

### <a name="return-value"></a>返回值

表示操作`CTimeSpan`结果的或对象。`CTime`

### <a name="remarks"></a>备注

`CTime`对象表示绝对时间， `CTimeSpan`对象表示相对时间。 前两个运算符允许在对象之间`CTimeSpan` `CTime`添加和减少对象。 第三个运算符允许您从一个`CTime`对象中减去另一个对象`CTimeSpan`以生成一个对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>CTime：： operator + =，-=

这些运算符可在此`CTimeSpan` `CTime`对象中添加和减去对象。

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要`CTimeSpan`添加或减去的对象。

### <a name="return-value"></a>返回值

已更新`CTime`的对象。

### <a name="remarks"></a>备注

通过这些运算符，可以在此`CTimeSpan` `CTime`对象中添加和减去对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>CTime：： Serialize64

> [!NOTE]
> 此方法仅在 MFC 项目中可用。

从存档中将与成员变量关联的数据序列化。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
要`CArchive`更新的对象。

### <a name="return-value"></a>返回值

已更新`CArchive`的对象。

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
