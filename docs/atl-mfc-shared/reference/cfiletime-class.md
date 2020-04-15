---
title: 文件时间类
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
ms.openlocfilehash: bc9fe752898a5dfde2631352abd8c3cf5f8b378c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317894"
---
# <a name="cfiletime-class"></a>文件时间类

此类提供用于管理与文件关联的日期和时间值的方法。

## <a name="syntax"></a>语法

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[文件时间：：文件时间](#cfiletime)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[文件时间：：获取当前时间](#getcurrenttime)|调用此静态函数以检索表示`CFileTime`当前系统日期和时间的对象。|
|[文件时间：获取时间](#gettime)|调用此方法以从`CFileTime`对象检索时间。|
|[文件时间：：本地图](#localtoutc)|调用此方法，根据协调通用时间 （UTC） 将本地文件时间转换为文件时间。|
|[文件时间：：设置时间](#settime)|调用此方法以设置对象存储的`CFileTime`日期和时间。|
|[文件时间：：UTC 到本地](#utctolocal)|调用此方法，根据协调通用时间 （UTC） 将时间转换为本地文件时间。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[文件时间：：运算符 -](#operator_-)|此运算符用于对`CFileTime`或`CFileTimeSpan`对象执行减法。|
|[文件时间：：操作员！*](#operator_neq)|此运算符比较两`CFileTime`个对象为不等式。|
|[文件时间：：操作员 |](#operator_add)|此运算符用于对 `CFileTimeSpan` 对象执行加法。|
|[文件时间：：操作员 |](#operator_add_eq)|此运算符用于对 `CFileTimeSpan` 对象执行加法并对它赋予结果。|
|[文件时间：：运算符&lt;](#operator_lt)|此运算符比较两个 `CFileTime` 对象以确定较小者。|
|[文件时间：：运算符&lt;=](#operator_lt_eq)|此运算符比较两个 `CFileTime` 对象以确定是否相等或较小者。|
|[文件时间：：操作员 |](#operator_eq)|分配运算符。|
|[文件时间：：运算符 -*](#operator_-_eq)|此运算符用于对`CFileTimeSpan`对象执行减法并将结果分配给当前对象。|
|[文件时间：：操作员 |](#operator_eq_eq)|此运算符比较两个 `CFileTime` 对象是否相等。|
|[文件时间：：运算符&gt;](#operator_gt)|此运算符比较两个 `CFileTime` 对象以确定较大者。|
|[文件时间：：运算符&gt;=](#operator_gt_eq)|此运算符比较两个 `CFileTime` 对象以确定是否相等或较大者。|

### <a name="public-constants"></a>公共常量

|名称|说明|
|----------|-----------------|
|[文件时间：:D](#day)|存储构成一天的 100 纳秒间隔数的静态数据成员。|
|[文件时间：小时](#hour)|存储构成一小时的 100 纳秒间隔数的静态数据成员。|
|[文件时间：：毫秒](#millisecond)|存储构成一毫秒的 100 纳秒间隔数的静态数据成员。|
|[文件时间：分钟](#minute)|存储构成一分钟的 100 纳秒间隔数的静态数据成员。|
|[文件时间：第二](#second)|存储构成一秒的 100 纳秒间隔数的静态数据成员。|
|[文件时间：周](#week)|存储构成一周的 100 纳秒间隔数的静态数据成员。|

## <a name="remarks"></a>备注

此类提供用于管理与创建、访问和修改文件关联的日期和时间值的方法。 此类的方法和数据经常与`CFileTimeSpan`对象结合使用，对象处理相对的时间值。

日期和时间值存储为 64 位值，表示自 1601 年 1 月 1 日以来的 100 纳秒间隔数。 这是协调通用时间 （UTC） 格式。

提供了以下静态同流成员变量以简化计算：

|成员变量|100纳秒间隔数|
|---------------------|-----------------------------------------|
|Millisecond|10,000|
|秒|毫秒\*1，000|
|Minute|第\*二 60|
|Hour|分钟\*60|
|日期|小时\*24|
|Week|第\*7天|

**注意**并非所有文件系统都可以记录创建和最后访问时间，并非所有文件系统都能以相同的方式记录它们。 例如，在 Windows NT FAT 文件系统上，创建时间的分辨率为 10 毫秒，写入时间具有 2 秒的分辨率，访问时间的分辨率为 1 天（访问日期）。 在 NTFS 上，访问时间具有 1 小时的分辨率。 此外，FAT 记录磁盘在本地时间的时间，但 NTFS 记录在 UTC 中的磁盘上的时间。 有关详细信息，请参阅[文件时间](/windows/win32/SysInfo/file-times)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`FILETIME`

`CFileTime`

## <a name="requirements"></a>要求

**标题：** atltime.h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a>文件时间：：文件时间

构造函数。

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
[文件时间](/windows/win32/api/minwinbase/ns-minwinbase-filetime)结构。

*nTime*<br/>
以 64 位值表示的日期和时间。

### <a name="remarks"></a>备注

可以使用`CFileTime``FILETIME`结构中的现有日期和时间创建对象，或表示为 64 位值（以本地或协调通用时间 （UTC） 时间格式）。 默认构造函数将时间设置为 0。

## <a name="cfiletimeday"></a><a name="day"></a>文件时间：:D

存储构成一天的 100 纳秒间隔数的静态数据成员。

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>示例

请参阅[CFileTime：：毫秒的示例](#millisecond)。

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a>文件时间：：获取当前时间

调用此静态函数以检索表示`CFileTime`当前系统日期和时间的对象。

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>返回值

以协调通用时间 （UTC） 格式返回当前系统日期和时间。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a>文件时间：获取时间

调用此方法以从`CFileTime`对象检索时间。

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>返回值

将日期和时间作为 64 位数字返回，该数字可能采用本地或协调通用时间 （UTC） 格式。

## <a name="cfiletimehour"></a><a name="hour"></a>文件时间：小时

存储构成一小时的 100 纳秒间隔数的静态数据成员。

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>示例

请参阅[CFileTime：：毫秒的示例](#millisecond)。

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a>文件时间：：本地图

调用此方法，根据协调通用时间 （UTC） 将本地文件时间转换为文件时间。

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>返回值

返回包含`CFileTime`时间（UTC 格式）的对象。

### <a name="example"></a>示例

请参阅[CFileTime 示例：：UTCTolocal](#utctolocal)。

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a>文件时间：：毫秒

存储构成一毫秒的 100 纳秒间隔数的静态数据成员。

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a>文件时间：分钟

存储构成一分钟的 100 纳秒间隔数的静态数据成员。

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>示例

请参阅[CFileTime：：毫秒的示例](#millisecond)。

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a>文件时间：：运算符 -

此运算符用于对`CFileTime`或`CFileTimeSpan`对象执行减法。

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
`CFileTimeSpan` 对象。

*英尺*<br/>
`CFileTime` 对象。

### <a name="return-value"></a>返回值

返回表示`CFileTime`两个`CFileTimeSpan`对象之间的时差结果的对象或对象。

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a>文件时间：：操作员！*

此运算符比较两`CFileTime`个对象为不等式。

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果要比较的项不等于对象，`CFileTime`则返回 TRUE，否则为 FALSE。

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a>文件时间：：操作员 |

此运算符用于对 `CFileTimeSpan` 对象执行加法。

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
`CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回表示`CFileTime`原始时间的结果加上相对时间的对象。

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a>文件时间：：操作员 |

此运算符用于对 `CFileTimeSpan` 对象执行加法并对它赋予结果。

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
`CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回更新`CFileTime`的对象，表示原始时间的结果加上相对时间。

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a>文件时间：：运算符&lt;

此运算符比较两个 `CFileTime` 对象以确定较小者。

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于第二个对象（时间早期），则返回 TRUE，否则为 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a>文件时间：：运算符&lt;=

此运算符比较两个 `CFileTime` 对象以确定是否相等或较小者。

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于（时间早期）或等于第二个对象，否则返回 TRUE，否则为 FALSE。

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a>文件时间：：操作员 |

分配运算符。

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
包含`CFileTime`新时间和日期的对象。

### <a name="return-value"></a>返回值

返回更新`CFileTime`的对象。

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a>文件时间：：运算符 -*

此运算符用于对`CFileTimeSpan`对象执行减法并将结果分配给当前对象。

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
包含`CFileTimeSpan`要减去的相对时间的对象。

### <a name="return-value"></a>返回值

返回更新`CFileTime`的对象。

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a>文件时间：：操作员 |

此运算符比较两个 `CFileTime` 对象是否相等。

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果对象相等，则返回 TRUE，否则为 FALSE。

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a>文件时间：：运算符&gt;

此运算符比较两个 `CFileTime` 对象以确定较大者。

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于（时间较晚）大于第二个对象，则返回 TRUE，否则为 FALSE。

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a>文件时间：：运算符&gt;=

此运算符比较两个 `CFileTime` 对象以确定是否相等或较大者。

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>参数

*英尺*<br/>
要比较的 `CFileTime` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于（时间后期）或等于第二个对象，否则返回 TRUE，否则为 FALSE。

## <a name="cfiletimesecond"></a><a name="second"></a>文件时间：第二

存储构成一天的 100 纳秒间隔数的静态数据成员。

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>示例

请参阅[CFileTime：：毫秒的示例](#millisecond)。

## <a name="cfiletimesettime"></a><a name="settime"></a>文件时间：：设置时间

调用此方法以设置对象存储的`CFileTime`日期和时间。

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>参数

*nTime*<br/>
以本地或协调通用时间 （UTC） 格式表示日期和时间的 64 位值。

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a>文件时间：：UTC 到本地

调用此方法，根据协调通用时间 （UTC） 将时间转换为本地文件时间。

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>返回值

返回以`CFileTime`本地文件时间格式包含时间的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a>文件时间：周

存储构成一周的 100 纳秒间隔数的静态数据成员。

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>示例

请参阅[CFileTime：：毫秒的示例](#millisecond)。

## <a name="see-also"></a>另请参阅

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[文件时间跨度类](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
