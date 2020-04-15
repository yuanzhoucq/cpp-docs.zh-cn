---
title: COleDateTimeSpan 类
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 7173fa0b6261ea718a02d399d944a1b5bb98b9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317731"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 类

表示相对时间、时间跨度。

## <a name="syntax"></a>语法

```
class COleDateTimeSpan
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleDate时间跨度：COleDatetimeSpan](#coledatetimespan)|构造 `COleDateTimeSpan` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleDate时间跨度：：格式](#format)|生成`COleDateTimeSpan`对象的格式化字符串表示形式。|
|[COleDate时间跨度：获取天数](#getdays)|返回此`COleDateTimeSpan`对象表示的跨值的天部分。|
|[COleDateTimeSpan：获取小时数](#gethours)|返回此`COleDateTimeSpan`对象表示的跨值的小时部分。|
|[COleDateTimeSpan：获取分钟数](#getminutes)|返回此`COleDateTimeSpan`对象表示的跨值的分钟部分。|
|[COleDate时间跨度：获取秒数](#getseconds)|返回此`COleDateTimeSpan`对象表示的跨范围的第二部分。|
|[COleDate 时间跨度：获取状态](#getstatus)|获取此`COleDateTimeSpan`对象的状态（有效性）。|
|[COleDate时间跨度：获取总天数](#gettotaldays)|返回此`COleDateTimeSpan`对象表示的天数。|
|[COleDateTimeSpan：获取总小时数](#gettotalhours)|返回此`COleDateTimeSpan`对象表示的小时数。|
|[COleDateTimeSpan：获取总分钟数](#gettotalminutes)|返回此`COleDateTimeSpan`对象表示的分钟数。|
|[COleDate时间跨度：：获取总秒数](#gettotalseconds)|返回此`COleDateTimeSpan`对象表示的秒数。|
|[COleDate时间跨度：：设置时间跨度](#setdatetimespan)|设置此`COleDateTimeSpan`对象的值。|
|[COleDate 时间跨度：：设置状态](#setstatus)|设置此`COleDateTimeSpan`对象的状态（有效性）。|

### <a name="public-operators"></a>公共运算符

|||
|-|-|
|[运算符 +， -](#operator_add_-)|添加、减去和更改值的`COleDateTimeSpan`符号。|
|[运算符 *， -]](#operator_add_eq_-_eq)|从此值`COleDateTimeSpan`中添加`COleDateTimeSpan`和减去值。|
|[运算符 |](#operator_eq)|复制值`COleDateTimeSpan`。|
|[运算符 =、<、<|](#coledatetimespan_relational_operators)|比较两`COleDateTimeSpan`个值。|
|[运算符 double](#operator_double)|将此值`COleDateTimeSpan`转换为**双精度**值。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleDate 时间跨度：：m_span](#m_span)|包含此`COleDateTimeSpan`对象的基础**双精度值**。|
|[COleDate时间跨度：：m_status](#m_status)|包含此`COleDateTimeSpan`对象的状态。|

## <a name="remarks"></a>备注

`COleDateTimeSpan`没有基类。

A`COleDateTimeSpan`以天保持时间。

`COleDateTimeSpan`用于其配套类[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。 `COleDateTime`封装 OLE`DATE`自动化的数据类型。 `COleDateTime`表示绝对时间值。 所有`COleDateTime`计算都涉及`COleDateTimeSpan`值。 这些类之间的关系类似于 CTime 和[CTimeSpan](../../atl-mfc-shared/reference/ctime-class.md)之间的关系[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。

有关`COleDateTime`和`COleDateTimeSpan`类的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="requirements"></a>要求

**标题：** ATLComTime.h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan关系运算符

比较运算符。

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>参数

*日期斯潘*<br/>
要比较的 `COleDateTimeSpan`。

### <a name="return-value"></a>返回值

这些运算符比较两个日期/时间跨度值，如果条件为 true，则返回 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

> [!NOTE]
> 如果任一操作数无效，将发生 ATLASSERT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDate时间跨度：COleDatetimeSpan

构造 `COleDateTimeSpan` 对象。

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>参数

*德布尔斯潘斯克*<br/>
要复制到新`COleDateTimeSpan`对象的天数。

*l 天*， *nHours*， *nMins*， *nSecs*<br/>
指示要复制到新`COleDateTimeSpan`对象的日时值。

### <a name="remarks"></a>备注

所有这些构造函数都创建新`COleDateTimeSpan`的对象，初始化到指定值。 每个构造函数的简要描述如下：

- **COleDateTimeSpan）** 构造初始化`COleDateTimeSpan`为 0 的对象。

- **COleDateTimeSpan）** `dblSpanSrc` **)** 从浮点`COleDateTimeSpan`值构造对象。

- **COleDateTimeSpan（** `lDays` **，** `nHours` **，** `nMins` **，** `nSecs` **）** 构造初始化`COleDateTimeSpan`为指定数值的对象。

新`COleDateTimeSpan`对象的状态设置为有效。

有关`COleDateTimeSpan`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDate时间跨度：：格式

生成`COleDateTimeSpan`对象的格式化字符串表示形式。

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>参数

*p格式*<br/>
类似于格式字符串的`printf`格式字符串。 格式代码（前面为百分比 （`%`） 符号，由相应的`COleDateTimeSpan`组件替换。 格式字符串中的其他字符将复制到返回的字符串。 下面列出了格式化`Format`代码的值和含义：

- **%H**当天的小时数

- **%M**当前小时内的分钟数

- **%S**当前分钟中的秒数

- **%%** 百分比符号

上面列出的四个格式代码是格式将接受的唯一代码。

-

*nID*<br/>
格式控制字符串的资源 ID。

### <a name="return-value"></a>返回值

包含`CString`格式化日期/时间跨度值的 。

### <a name="remarks"></a>备注

调用这些函数以创建时间跨度值的格式化表示形式。 如果此`COleDateTimeSpan`对象的状态为 null，则返回值为空字符串。 如果状态无效，则返回字符串由字符串资源IDS_INVALID_DATETIMESPAN指定。

此函数的窗体的简要说明如下：

**格式（** *pFormat* **）**<br/>
此窗体使用格式字符串设置值，该格式字符串包含特殊格式代码，前面有百分比符号 （%），如 中`printf`。 格式化字符串作为参数传递给函数。

**格式***（nID）* **)**<br/>
此窗体使用格式字符串设置值，该格式字符串包含特殊格式代码，前面有百分比符号 （%），如 中`printf`。 格式化字符串是一个资源。 此字符串资源的 ID 作为参数传递。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDate时间跨度：获取天数

检索此日期/时间跨度值的天部分。

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的日部分。

### <a name="remarks"></a>备注

此函数的返回值介于大约 - 3，615，000 和 3，615，000 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取时间](#gethours)

- [获取分钟](#getminutes)

- [获取秒数](#getseconds)

- [获取总天数](#gettotaldays)

- [获取总小时数](#gettotalhours)

- [获取总分钟数](#gettotalminutes)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan：获取小时数

检索此日期/时间跨度值的小时部分。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的工时部分。

### <a name="remarks"></a>备注

此函数的返回值范围介于 - 23 和 23 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取分钟](#getminutes)

- [获取秒数](#getseconds)

- [获取总天数](#gettotaldays)

- [获取总小时数](#gettotalhours)

- [获取总分钟数](#gettotalminutes)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan：获取分钟数

检索此日期/时间跨度值的分钟部分。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的分钟部分。

### <a name="remarks"></a>备注

此函数的返回值范围介于 - 59 和 59 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取时间](#gethours)

- [获取秒数](#getseconds)

- [获取总天数](#gettotaldays)

- [获取总小时数](#gettotalhours)

- [获取总分钟数](#gettotalminutes)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDate时间跨度：获取秒数

检索此日期/时间跨度值的第二部分。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的秒部分。

### <a name="remarks"></a>备注

此函数的返回值范围介于 - 59 和 59 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取时间](#gethours)

- [获取分钟](#getminutes)

- [获取总天数](#gettotaldays)

- [获取总小时数](#gettotalhours)

- [获取总分钟数](#gettotalminutes)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDate 时间跨度：获取状态

获取此`COleDateTimeSpan`对象的状态（有效性）。

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>返回值

此值`COleDateTimeSpan`的状态。

### <a name="remarks"></a>备注

返回值由`DateTimeSpanStatus`枚举类型定义，该类型在类中`COleDateTimeSpan`定义。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleDateTimeSpan::valid`指示此`COleDateTimeSpan`对象有效。

- `COleDateTimeSpan::invalid`指示此对象`COleDateTimeSpan`无效;如果表明此对象无效。也就是说，其值可能不正确。

- `COleDateTimeSpan::null`指示此`COleDateTimeSpan`对象为 null，即未为此对象提供任何值。 （这是"无值"的数据库意义上的"空"，而不是C++ NULL。

在以下情况下，`COleDateTimeSpan`对象的状态无效：

- 如果此对象在算术赋值操作期间（即`+=`或`-=`） 经历了溢出或下溢。

- 如果为此对象分配了无效值。

- 如果此对象的状态被显式设置为无效使用`SetStatus`。

有关可能将状态设置为无效的操作的详细信息，请参阅[COleDateTimeSpan：：运算符 *，-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan：：运算符 *，-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

有关`COleDateTimeSpan`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDate时间跨度：获取总天数

检索以天表示的此日期/时间跨度值。

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值以天表示。 尽管此函数是原型返回 double，但它始终将返回整数值。

### <a name="remarks"></a>备注

此函数的返回值介于大约 - 3.65e6 和 3.65e6 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取时间](#gethours)

- [获取分钟](#getminutes)

- [获取秒数](#getseconds)

- [获取总小时数](#gettotalhours)

- [获取总分钟数](#gettotalminutes)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan：获取总小时数

检索以小时表示的此日期/时间跨度值。

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值以小时表示。 尽管此函数是原型返回 double，但它始终将返回整数值。

### <a name="remarks"></a>备注

此函数的返回值介于大约 - 8.77e7 和 8.77e7 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取时间](#gethours)

- [获取分钟](#getminutes)

- [获取秒数](#getseconds)

- [获取总天数](#gettotaldays)

- [获取总分钟数](#gettotalminutes)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

请参阅[GetTotalDays 日的示例](#gettotaldays)。

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan：获取总分钟数

检索以分钟表示的此日期/时间跨度值。

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值以分钟表示。 尽管此函数是原型返回 double，但它始终将返回整数值。

### <a name="remarks"></a>备注

此函数的返回值介于大约 - 5.26e9 和 5.26e9 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取时间](#gethours)

- [获取分钟](#getminutes)

- [获取秒数](#getseconds)

- [获取总天数](#gettotaldays)

- [获取总小时数](#gettotalhours)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

请参阅[GetTotalDays 日的示例](#gettotaldays)。

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDate时间跨度：：获取总秒数

检索以秒表示的此日期/时间跨度值。

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值以秒为单位表示。 尽管此函数是原型返回 double，但它始终将返回整数值。

### <a name="remarks"></a>备注

此函数的返回值介于大约 - 3.16e11 到 3.16e11 之间。

对于查询`COleDateTimeSpan`对象值的其他函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取时间](#gethours)

- [获取分钟](#getminutes)

- [获取秒数](#getseconds)

- [获取总天数](#gettotaldays)

- [获取总小时数](#gettotalhours)

- [获取总分钟数](#gettotalminutes)

### <a name="example"></a>示例

请参阅[GetTotalDays 日的示例](#gettotaldays)。

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDate 时间跨度：：m_span

此`COleDateTime`对象的基础**双精度值**。

```
double m_span;
```

### <a name="remarks"></a>备注

此值表示日期/时间跨度（以天表示）。

> [!CAUTION]
> 更改**双**数据成员中的值将更改此`COleDateTimeSpan`对象的值。 它不会更改此`COleDateTimeSpan`对象的状态。

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDate时间跨度：：m_status

此数据成员的类型是枚举类型`DateTimeSpanStatus`，在类中`COleDateTimeSpan`定义。

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>备注

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleDateTimeSpan::valid`指示此`COleDateTimeSpan`对象有效。

- `COleDateTimeSpan::invalid`指示此对象`COleDateTimeSpan`无效;如果表明此对象无效。也就是说，其值可能不正确。

- `COleDateTimeSpan::null`指示此`COleDateTimeSpan`对象为 null，即未为此对象提供任何值。 （这是"无值"的数据库意义上的"空"，而不是C++ NULL。

在以下情况下，`COleDateTimeSpan`对象的状态无效：

- 如果此对象在算术赋值操作期间（即`+=`或`-=`） 经历了溢出或下溢。

- 如果为此对象分配了无效值。

- 如果此对象的状态被显式设置为无效使用[SetStatus](#setstatus)。

有关可能将状态设置为无效的操作的详细信息，请参阅[COleDateTimeSpan：：运算符 *，-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan：：运算符 *，-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

> [!CAUTION]
> 此数据成员适用于高级编程情况。 应使用内联成员函数["获取状态"](#getstatus)和["设置状态](#setstatus)"。 有关`SetStatus`显式设置此数据成员的进一步注意事项，请参阅。

有关`COleDateTimeSpan`值边界的详细信息，请参阅文章["日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)"。

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDate时间跨度：：运算符 |

复制值`COleDateTimeSpan`。

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>备注

此重载分配运算符将源日期/时间跨度值复制到此`COleDateTimeSpan`对象中。

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan：：运算符 +， -

添加、减去和更改值的`COleDateTimeSpan`符号。

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>备注

前两个运算符允许您添加和减去日期/时间跨度值。 第三个允许您更改日期/时间跨度值的符号。

如果任一操作数为空，则结果`COleDateTimeSpan`值的状态为 null。

如果任一操作数无效，另一个操作数不为空，则结果`COleDateTimeSpan`值的状态无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDate时间跨度：：运算符 *，-*

从此值`COleDateTimeSpan`中添加`COleDateTimeSpan`和减去值。

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>备注

这些运算符允许您在此`COleDateTimeSpan`对象中添加和减去日期/时间跨度值。 如果任一操作数为空，则结果`COleDateTimeSpan`值的状态为 null。

如果任一操作数无效，另一个操作数不为空，则结果`COleDateTimeSpan`值的状态无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDate 时间跨度：：运算符双精度

将此值`COleDateTimeSpan`转换为**双精度**值。

```
operator double() const throw();
```

### <a name="remarks"></a>备注

此运算符将此值`COleDateTimeSpan`的值作为浮点天数返回。

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDate时间跨度：：设置时间跨度

设置此日期/时间跨度值的值。

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>参数

*l 天*， *nHours*， *nMins*， *nSecs*<br/>
指示要复制到此`COleDateTimeSpan`对象的日期跨度和时间跨度值。

### <a name="remarks"></a>备注

对于查询`COleDateTimeSpan`对象值的函数，请参阅以下成员函数：

- [获取天数](#getdays)

- [获取时间](#gethours)

- [获取分钟](#getminutes)

- [获取秒数](#getseconds)

- [获取总天数](#gettotaldays)

- [获取总小时数](#gettotalhours)

- [获取总分钟数](#gettotalminutes)

- [获取总秒数](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDate 时间跨度：：设置状态

设置此`COleDateTimeSpan`对象的状态（有效性）。

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>参数

*状态*<br/>
此`COleDateTimeSpan`对象的新状态值。

### <a name="remarks"></a>备注

*状态*参数值由`DateTimeSpanStatus`枚举类型定义，该类型在类中`COleDateTimeSpan`定义。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleDateTimeSpan::valid`指示此`COleDateTimeSpan`对象有效。

- `COleDateTimeSpan::invalid`指示此对象`COleDateTimeSpan`无效;如果表明此对象无效。也就是说，其值可能不正确。

- `COleDateTimeSpan::null`指示此`COleDateTimeSpan`对象为 null，即未为此对象提供任何值。 （这是"无值"的数据库意义上的"空"，而不是C++ NULL。

   > [!CAUTION]
   > 此功能适用于高级编程情况。 此函数不会更改此对象中的数据。 它最常用于将状态设置为**null**或**无效**。 请注意，赋值运算符 （[运算符 =](#operator_eq)） 和[SetDateTimeSpan](#setdatetimespan)确实根据源值设置对象的状态。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>另请参阅

[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime 类](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
