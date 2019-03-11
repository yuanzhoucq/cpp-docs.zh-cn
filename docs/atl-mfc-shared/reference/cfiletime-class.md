---
title: CFileTime 类
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: 07b888b031a38dc2f09404a14e729e26b3eaa019
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746092"
---
# <a name="cfiletime-class"></a>CFileTime 类

此类提供用于管理与文件相关联的日期和时间值的方法。

## <a name="syntax"></a>语法

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|调用此静态函数以检索`CFileTime`对象，表示当前系统日期和时间。|
|[CFileTime::GetTime](#gettime)|调用此方法来检索从时间`CFileTime`对象。|
|[CFileTime::LocalToUTC](#localtoutc)|调用此方法以将本地文件时间转换为基于协调世界时 (UTC) 上的文件时间。|
|[CFileTime::SetTime](#settime)|调用此方法以设置的日期和时间存储`CFileTime`对象。|
|[CFileTime::UTCToLocal](#utctolocal)|调用此方法将时间基于协调世界时 (UTC) 为本地文件时间转换。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CFileTime::operator -](#operator_-)|此运算符用于对执行减法`CFileTime`或`CFileTimeSpan`对象。|
|[CFileTime::operator !=](#operator_neq)|此运算符比较两个`CFileTime`对象是否不相等。|
|[CFileTime::operator +](#operator_add)|此运算符用于对 `CFileTimeSpan` 对象执行加法。|
|[CFileTime::operator +=](#operator_add_eq)|此运算符用于对 `CFileTimeSpan` 对象执行加法并对它赋予结果。|
|[CFileTime::operator &lt;](#operator_lt)|此运算符比较两个 `CFileTime` 对象以确定较小者。|
|[CFileTime::operator &lt;=](#operator_lt_eq)|此运算符比较两个 `CFileTime` 对象以确定是否相等或较小者。|
|[CFileTime::operator =](#operator_eq)|赋值运算符。|
|[CFileTime::operator -=](#operator_-_eq)|此运算符用于对执行减法`CFileTimeSpan`对象，并将结果分配给当前对象。|
|[CFileTime::operator ==](#operator_eq_eq)|此运算符比较两个 `CFileTime` 对象是否相等。|
|[CFileTime::operator &gt;](#operator_gt)|此运算符比较两个 `CFileTime` 对象以确定较大者。|
|[CFileTime::operator &gt;=](#operator_gt_eq)|此运算符比较两个 `CFileTime` 对象以确定是否相等或较大者。|

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[CFileTime::Day](#day)|静态数据成员存储构成了一天的 100 纳秒间隔数。|
|[CFileTime::Hour](#hour)|静态数据成员存储组成一小时的 100 纳秒间隔数。|
|[CFileTime::Millisecond](#millisecond)|静态数据成员存储组成一毫秒的 100 纳秒间隔数。|
|[CFileTime::Minute](#minute)|静态数据成员存储构成了一分钟的 100 纳秒间隔数。|
|[CFileTime::Second](#second)|静态数据成员存储组成一秒的 100 纳秒间隔数。|
|[CFileTime::Week](#week)|静态数据成员存储组成一周的 100 纳秒间隔数。|

## <a name="remarks"></a>备注

此类提供用于管理与创建、 访问和修改的文件关联的日期和时间值的方法。 方法和此类数据通常与结合使用`CFileTimeSpan`处理相对时间值的对象。

日期和时间值存储为表示从 1601 年 1 月 1 日起 100 纳秒间隔数的 64 位值。 这是协调世界时 (UTC) 格式。

提供了以下静态 const 成员变量以简化计算：

|成员变量|100 纳秒间隔数|
|---------------------|-----------------------------------------|
|毫秒|10,000|
|秒|毫秒\*1,000|
|分钟|第二个\*60|
|小时|分钟\*60|
|天|小时\*24|
|周|一天\*7|

**请注意**不是所有的文件系统可以记录创建和上次访问时间并不是所有的文件系统记录这些相同的方式。 示例中的，在 Windows NT FAT 文件系统上，则可以创建时具有的分辨率为 10 毫秒、 写入时具有的分辨率为 2 秒和访问时间具有的分辨率为 1 天 （访问日期）。 在 NTFS 中，访问时间程序的分辨率为 1 小时。 此外，FAT 记录在磁盘上的时间以本地时间，但 NTFS 在 UTC 中记录在磁盘上的时间。 有关详细信息，请参阅[文件时间](/windows/desktop/SysInfo/file-times)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`FILETIME`

`CFileTime`

## <a name="requirements"></a>要求

**标头：** atltime.h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

构造函数。

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
一个[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)结构。

*nTime*<br/>
日期和时间表示为一个 64 位值。

### <a name="remarks"></a>备注

`CFileTime`可以使用现有的日期和时间从创建对象`FILETIME`结构，或者表示为一个 64 位值 （在本地或协调世界时 (UTC) 时间格式）。 默认构造函数设置为 0 的时间。

##  <a name="day"></a>  CFileTime::Day

静态数据成员存储构成了一天的 100 纳秒间隔数。

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>示例

有关示例，请参阅[CFileTime::Millisecond](#millisecond)。

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

调用此静态函数以检索`CFileTime`对象，表示当前系统日期和时间。

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>返回值

以协调世界时 (UTC) 格式返回当前系统日期和时间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

调用此方法来检索从时间`CFileTime`对象。

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>返回值

返回日期和时间作为 64 位数字，这可能是本地或其格式为协调世界时 (UTC) 中。

##  <a name="hour"></a>  CFileTime::Hour

静态数据成员存储组成一小时的 100 纳秒间隔数。

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>示例

有关示例，请参阅[CFileTime::Millisecond](#millisecond)。

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

调用此方法以将本地文件时间转换为基于协调世界时 (UTC) 上的文件时间。

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>返回值

返回`CFileTime`对象，其中包含以 UTC 格式的时间。

### <a name="example"></a>示例

有关示例，请参阅[CFileTime::UTCToLocal](#utctolocal)。

##  <a name="millisecond"></a>  CFileTime::Millisecond

静态数据成员存储组成一毫秒的 100 纳秒间隔数。

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

静态数据成员存储构成了一分钟的 100 纳秒间隔数。

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>示例

有关示例，请参阅[CFileTime::Millisecond](#millisecond)。

##  <a name="operator_-"></a>  CFileTime::operator -

此运算符用于对执行减法`CFileTime`或`CFileTimeSpan`对象。

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

*ft*<br/>
一个 `CFileTime` 对象。

### <a name="return-value"></a>返回值

返回`CFileTime`对象或`CFileTimeSpan`对象，表示两个对象之间的时间差的结果。

##  <a name="operator_neq"></a>  CFileTime::operator ！ =

此运算符比较两个`CFileTime`对象是否不相等。

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果要比较的项不相等，则返回 TRUE`CFileTime`对象，否则为 FALSE。

##  <a name="operator_add"></a>  CFileTime::operator +

此运算符用于对 `CFileTimeSpan` 对象执行加法。

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回`CFileTime`对象表示结果的原始时间加上相对时间。

##  <a name="operator_add_eq"></a>  CFileTime::operator + =

此运算符用于对 `CFileTimeSpan` 对象执行加法并对它赋予结果。

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回已更新`CFileTime`对象，表示结果的原始时间加上相对时间。

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

此运算符比较两个 `CFileTime` 对象以确定较小者。

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于 （前面的时间） 第二个，则返回 FALSE 否则，则返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=

此运算符比较两个 `CFileTime` 对象以确定是否相等或较小者。

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象 （前面的时间） 小于或等于第二个，则返回 TRUE; 否则为 FALSE。

##  <a name="operator_eq"></a>  CFileTime::operator =

赋值运算符。

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
一个`CFileTime`对象，其中包含新的时间和日期。

### <a name="return-value"></a>返回值

返回已更新`CFileTime`对象。

##  <a name="operator_-_eq"></a>  CFileTime::operator -=

此运算符用于对执行减法`CFileTimeSpan`对象，并将结果分配给当前对象。

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个`CFileTimeSpan`对象，其中包含要减去的相对时间。

### <a name="return-value"></a>返回值

返回已更新`CFileTime`对象。

##  <a name="operator_eq_eq"></a>  CFileTime::operator = =

此运算符比较两个 `CFileTime` 对象是否相等。

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
`CFileTime`要比较的对象。

### <a name="return-value"></a>返回值

如果对象相等，否则为 FALSE，则返回 TRUE。

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

此运算符比较两个 `CFileTime` 对象以确定较大者。

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于 （更高版本的时间），则返回 TRUE 的第二个，否则为 FALSE。

##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=

此运算符比较两个 `CFileTime` 对象以确定是否相等或较大者。

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*ft*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象 （更高版本中时间） 大于或等于第二个，则返回 TRUE; 否则为 FALSE。

##  <a name="second"></a>  CFileTime::Second

静态数据成员存储构成了一天的 100 纳秒间隔数。

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>示例

有关示例，请参阅[CFileTime::Millisecond](#millisecond)。

##  <a name="settime"></a>  CFileTime::SetTime

调用此方法以设置的日期和时间存储`CFileTime`对象。

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>参数

*nTime*<br/>
表示的日期和时间，在本地或协调世界时 (UTC) 格式的 64 位值。

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

调用此方法将时间基于协调世界时 (UTC) 为本地文件时间转换。

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>返回值

返回`CFileTime`对象，其中包含本地文件时间格式的时间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

静态数据成员存储组成一周的 100 纳秒间隔数。

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>示例

有关示例，请参阅[CFileTime::Millisecond](#millisecond)。

## <a name="see-also"></a>请参阅

[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan 类](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
