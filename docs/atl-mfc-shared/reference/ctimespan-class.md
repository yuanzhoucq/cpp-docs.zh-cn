---
title: CTimeSpan 类
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 14aa5eb52e2c631a92e40ae7053c566284e00e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317504"
---
# <a name="ctimespan-class"></a>CTimeSpan 类

时间量，在内部存储为时间跨度中的秒数。

## <a name="syntax"></a>语法

```
class CTimeSpan
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CTimeSpan：CTimeSpan](#ctimespan)|以各种方式构造`CTimeSpan`对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CTimeSpan：格式](#format)|将 转换为`CTimeSpan`格式化的字符串。|
|[CTimeSpan：获取天](#getdays)|返回表示此`CTimeSpan`中完整天数的值。|
|[CTimeSpan：获取小时数](#gethours)|返回表示当天小时数的值（-23 到 23）。|
|[CTimeSpan：获取分钟数](#getminutes)|返回表示当前小时中的分钟数的值 （-59 到 59）。|
|[CTimeSpan：获取秒数](#getseconds)|返回表示当前分钟（-59 到 59）中的秒数的值。|
|[CTimeSpan：获取时间跨度](#gettimespan)|返回`CTimeSpan`对象的值。|
|[CTimeSpan：获取总小时数](#gettotalhours)|返回表示此`CTimeSpan`中完整小时总数的值。|
|[CTimeSpan：获取总分钟数](#gettotalminutes)|返回表示此`CTimeSpan`中完整分钟总数的值。|
|[CTimeSpan：获取总秒数](#gettotalseconds)|返回表示此`CTimeSpan`中完整秒总数的值。|
|[CTimeSpan：序列化64](#serialize64)|将数据序列化到存档或从存档中序列化。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 = -](#operator_add_-)|添加和减去`CTimeSpan`对象。|
|[运算符 = -}](#operator_add_eq_-_eq)|在此添加和减去`CTimeSpan`对象。 `CTimeSpan`|
|[运算符 = < 等。](#ctimespan_comparison_operators)|比较两个相对的时间值。|

## <a name="remarks"></a>备注

`CTimeSpan`没有基类。

`CTimeSpan`函数将秒转换为天、小时、分钟和秒的各种组合。

对象`CTimeSpan`存储在 **__time64_t**结构中，该结构为 8 个字节。

配套类[CTime](../../atl-mfc-shared/reference/ctime-class.md)表示绝对时间。

和`CTime``CTimeSpan`类不是为派生而设计的。 由于没有虚拟函数，因此两个`CTime`函数和`CTimeSpan`对象的大小正好为 8 个字节。 大多数成员函数是内联的。

`CTimeSpan`有关使用 的详细信息，请参阅*运行时库参考*中的文章[日期和时间](../../atl-mfc-shared/date-and-time.md)以及[时间管理](../../c-runtime-library/time-management.md)。

## <a name="requirements"></a>要求

**标题：** atltime.h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a>CTimeSpan 比较运算符

比较运算符。

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
要比较的对象。

### <a name="return-value"></a>返回值

这些运算符比较两个相对时间值。 如果条件为 true，它们返回 TRUE;否则 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a>CTimeSpan：CTimeSpan

以各种方式构造`CTimeSpan`对象。

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>参数

*时间斯潘斯克*<br/>
已`CTimeSpan`存在的对象。

*time*<br/>
**__time64_t**时间值，即时间跨度中的秒数。

*l 天*， *nHours*， *nMins*， *nSecs*<br/>
天、小时、分钟和秒。

### <a name="remarks"></a>备注

所有这些构造函数都创建一个使用`CTimeSpan`指定相对时间初始化的新对象。 下面将介绍每个构造函数：

- `CTimeSpan( );`构造未初始化`CTimeSpan`的对象。

- `CTimeSpan( const CTimeSpan& );`从另一`CTimeSpan`个`CTimeSpan`值构造对象。

- `CTimeSpan( __time64_t );`从__time64_t类型`CTimeSpan`构造对象。 **__time64_t**

- `CTimeSpan( LONG, int, int, int );`从组件构造`CTimeSpan`一个对象，每个组件都受限制在以下范围：

   |组件|范围|
   |---------------|-----------|
   |*l 天*|0-25，000 （大约）|
   |*n小时*|0-23|
   |*n明斯*|0-59|
   |*nSecs*|0-59|

请注意，如果一个或多个时间日组件不在范围内，Microsoft 基础类库的调试版本将断言。 您有责任在调用之前验证参数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a>CTimeSpan：格式

生成对应于此`CTimeSpan`的格式化字符串。

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>参数

*p格式*， *psz格式*<br/>
类似于格式字符串的`printf`格式字符串。 格式代码（前面为百分比 （`%`） 符号，由相应的`CTimeSpan`组件替换。 格式字符串中的其他字符将复制到返回的字符串。 下面列出了格式化`Format`代码的值和含义：

- **%D**此总计天数`CTimeSpan`

- **%H**当天的小时数

- **%M**当前小时内的分钟数

- **%S**当前分钟中的秒数

- **%%** 百分比符号

*nID*<br/>
标识此格式的字符串的 ID。

### <a name="return-value"></a>返回值

包含`CString`格式化时间的对象。

### <a name="remarks"></a>备注

如果代码不在上述列表中，则库的调试版本将检查格式代码并断言。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a>CTimeSpan：获取天

返回表示此`CTimeSpan`中完整天数的值。

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>返回值

返回时间跨度中已完成 24 小时天数的数量。 如果时间跨度为负数，则此值可能是负值。

### <a name="remarks"></a>备注

请注意，夏令时可能会导致`GetDays`返回可能令人惊讶的结果。 例如，当 DST 生效时，`GetDays`将 4 月 1 日至 5 月 1 日期间的天数报告为 29 天，而不是 30 天，因为 4 月的一天缩短为一小时，因此不计为完整日期。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a>CTimeSpan：获取小时数

返回表示当天小时数的值（-23 到 23）。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>返回值

返回当天的小时数。 范围为 -23 到 23。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a>CTimeSpan：获取分钟数

返回表示当前小时中的分钟数的值 （-59 到 59）。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>返回值

返回当前小时内的分钟数。 范围为 -59 到 59。

### <a name="example"></a>示例

请参阅[GetHours](#gethours)的示例。

## <a name="ctimespangetseconds"></a><a name="getseconds"></a>CTimeSpan：获取秒数

返回表示当前分钟（-59 到 59）中的秒数的值。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>返回值

返回当前分钟中的秒数。 范围为 -59 到 59。

### <a name="example"></a>示例

请参阅[GetHours](#gethours)的示例。

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a>CTimeSpan：获取时间跨度

返回`CTimeSpan`对象的值。

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>返回值

返回`CTimeSpan`对象的当前值。

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a>CTimeSpan：获取总小时数

返回表示此`CTimeSpan`中完整小时总数的值。

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>返回值

返回此`CTimeSpan`中的完整小时总数。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a>CTimeSpan：获取总分钟数

返回表示此`CTimeSpan`中完整分钟总数的值。

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>返回值

返回此`CTimeSpan`中的完整分钟总数。

### <a name="example"></a>示例

请参阅[GetTotalHours 的示例](#gettotalhours)。

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a>CTimeSpan：获取总秒数

返回表示此`CTimeSpan`中完整秒总数的值。

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>返回值

返回此`CTimeSpan`中的完整秒总数。

### <a name="example"></a>示例

请参阅[GetTotalHours 的示例](#gettotalhours)。

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a>CTimeSpan：：运算符 +， -

添加和减去`CTimeSpan`对象。

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
要添加到对象的值`CTimeSpan`。

### <a name="return-value"></a>返回值

表示`CTimeSpan`操作结果的对象。

### <a name="remarks"></a>备注

这两个运算符允许您相互添加和减去`CTimeSpan`对象。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>CTimeSpan：：运算符 *，-*

在此添加和减去`CTimeSpan`对象。 `CTimeSpan`

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*跨度*<br/>
要添加到对象的值`CTimeSpan`。

### <a name="return-value"></a>返回值

更新`CTimeSpan`的对象。

### <a name="remarks"></a>备注

这些运算符允许您在此和 中添加和`CTimeSpan`减去对象`CTimeSpan`。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a>CTimeSpan：序列化64

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

[asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
