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
ms.openlocfilehash: a3a59971ec57378aee2ec4f65f221b96c46300b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219100"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 类

表示一个相对时间，时间跨度。

## <a name="syntax"></a>语法

```
class COleDateTimeSpan
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|构造 `COleDateTimeSpan` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[COleDateTimeSpan：： Format](#format)|生成对象的格式化字符串表示形式 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetDays](#getdays)|返回此对象所表示的范围的日部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetHours](#gethours)|返回此对象所表示的跨度的小时部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetMinutes](#getminutes)|返回此对象所表示的跨度的分钟部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetSeconds](#getseconds)|返回此对象所表示的范围的第二部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetStatus](#getstatus)|获取此对象的状态（有效性） `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|返回此对象所表示的天数 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|返回此对象所表示的小时数 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|返回此对象所表示的分钟数 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|返回此对象所表示的秒数 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|设置此对象的值 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： SetStatus](#setstatus)|设置此对象的状态（有效性） `COleDateTimeSpan` 。|

### <a name="public-operators"></a>公共运算符

|||
|-|-|
|[operator +、-](#operator_add_-)|添加、减和更改值的符号 `COleDateTimeSpan` 。|
|[operator + =，-=](#operator_add_eq_-_eq)|`COleDateTimeSpan`在此值中添加和减去值 `COleDateTimeSpan` 。|
|[operator =](#operator_eq)|复制 `COleDateTimeSpan` 值。|
|[operator = =，<，<=](#coledatetimespan_relational_operators)|比较两个 `COleDateTimeSpan` 值。|
|[运算符 double](#operator_double)|将此 `COleDateTimeSpan` 值转换为 **`double`** 。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleDateTimeSpan：： m_span](#m_span)|包含 **`double`** 此对象的基础 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： m_status](#m_status)|包含此对象的状态 `COleDateTimeSpan` 。|

## <a name="remarks"></a>备注

`COleDateTimeSpan`没有基类。

`COleDateTimeSpan`保留时间（以天为单位）。

`COleDateTimeSpan`与伴随类[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)一起使用。 `COleDateTime`封装 `DATE` OLE 自动化的数据类型。 `COleDateTime`表示绝对时间值。 所有 `COleDateTime` 计算都涉及 `COleDateTimeSpan` 值。 这两个类之间的关系类似于[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之间的关系。

有关和类的详细 `COleDateTime` 信息 `COleDateTimeSpan` ，请参阅文章[日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="requirements"></a>要求

**标头：** Atlcomtime。h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan 关系运算符

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

*dateSpan*<br/>
要比较的 `COleDateTimeSpan`。

### <a name="return-value"></a>返回值

这些运算符比较两个日期/时间范围值，如果条件为 true，则返回 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

> [!NOTE]
> 如果任一操作数无效，就会发生 ATLASSERT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan

构造 `COleDateTimeSpan` 对象。

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>参数

*dblSpanSrc*<br/>
要复制到新对象中的天数 `COleDateTimeSpan` 。

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
指示要复制到新对象中的日期和时间值 `COleDateTimeSpan` 。

### <a name="remarks"></a>备注

所有这些构造函数将创建 `COleDateTimeSpan` 初始化为指定值的新对象。 以下是每个构造函数的简要说明：

- **COleDateTimeSpan （）** 构造 `COleDateTimeSpan` 初始化为0的对象。

- **COleDateTimeSpan （** `dblSpanSrc` **）** `COleDateTimeSpan` 从浮点值构造对象。

- **COleDateTimeSpan （** `lDays` **、** `nHours` **、** `nMins` **、** `nSecs` **）** 构造 `COleDateTimeSpan` 初始化为指定数值的对象。

新对象的状态 `COleDateTimeSpan` 设置为 "有效"。

有关值界限的详细信息 `COleDateTimeSpan` ，请参阅文章[日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan：： Format

生成对象的格式化字符串表示形式 `COleDateTimeSpan` 。

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>参数

*pFormat*<br/>
格式字符串类似于格式设置 `printf` 字符串。 格式设置代码前面以百分号（ `%` ）符号替换为相应的 `COleDateTimeSpan` 组件。 格式字符串中的其他字符将按原样复制到返回的字符串中。 下面列出了的格式设置代码的值和含义 `Format` ：

- **% H**当天的小时

- **% M**当前小时内的分钟数

- **% S**当前分钟中的秒数

- **%%** 百分号

上面列出的四个格式代码是该格式将接受的唯一代码。

-

*nID*<br/>
格式控制字符串的资源 ID。

### <a name="return-value"></a>返回值

一个 `CString` ，它包含格式化日期/时间范围值。

### <a name="remarks"></a>备注

调用这些函数可创建时间跨度值的格式化表示形式。 如果此对象的状态 `COleDateTimeSpan` 为 null，则返回值为空字符串。 如果状态无效，则返回字符串由字符串资源 IDS_INVALID_DATETIMESPAN 指定。

此函数的窗体的简要说明如下所示：

**格式（** *pFormat* **）**<br/>
此窗体使用包含以百分号（%）开头的特殊格式设置代码的格式字符串设置值的格式，如中所示 `printf` 。 格式化字符串作为参数传递给函数。

**Format （** *nID* **）**<br/>
此窗体使用包含以百分号（%）开头的特殊格式设置代码的格式字符串设置值的格式，如中所示 `printf` 。 格式化字符串是资源。 此字符串资源的 ID 作为参数传递。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays

检索此日期/时间跨度值的日部分。

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的日部分。

### <a name="remarks"></a>备注

此函数的返回值介于大约-3615000 和3615000之间。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [获取时间](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan：： GetHours

检索此日期/时间跨度值的小时部分。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的小时部分。

### <a name="remarks"></a>备注

此函数的返回值介于-23 到23之间。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan：： GetMinutes

检索此日期/时间跨度值的分钟部分。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的分钟部分。

### <a name="remarks"></a>备注

此函数的返回值范围为-59 到59。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [获取时间](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan：： GetSeconds

检索此日期/时间跨度值的第二部分。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值的秒部分。

### <a name="remarks"></a>备注

此函数的返回值范围为-59 到59。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [获取时间](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan：： GetStatus

获取此对象的状态（有效性） `COleDateTimeSpan` 。

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>返回值

此值的状态 `COleDateTimeSpan` 。

### <a name="remarks"></a>备注

返回值由 `DateTimeSpanStatus` 枚举类型定义，该类型是在类中定义的 `COleDateTimeSpan` 。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleDateTimeSpan::valid`指示此 `COleDateTimeSpan` 对象有效。

- `COleDateTimeSpan::invalid`指示此 `COleDateTimeSpan` 对象无效; 也就是说，它的值可能不正确。

- `COleDateTimeSpan::null`指示此 `COleDateTimeSpan` 对象为 null，即没有为此对象提供值。 （这在数据库意义上是 "null"，而不是 c + + NULL。）

对象的状态 `COleDateTimeSpan` 在下列情况下无效：

- 如果此对象在算术赋值操作期间遇到溢出或下溢，则为 `+=` 或 `-=` 。

- 如果分配给此对象的值无效。

- 如果此对象的状态使用显式设置为 "无效"，则为 `SetStatus` 。

有关可能将状态设置为 "无效" 的操作的详细信息，请参阅[COleDateTimeSpan：： operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan：： operator + =，-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

有关值界限的详细信息 `COleDateTimeSpan` ，请参阅文章[日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

检索以天表示的此日期/时间跨度值。

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值（以天为单位）。 尽管此函数是原型以返回 double，但它将始终返回整数值。

### <a name="remarks"></a>备注

此函数的返回值范围是 3.65 e6 和 3.65 e6 之间的值。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [获取时间](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours

检索以小时为单位的此日期/时间跨度值。

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值（以小时为单位）。 尽管此函数是原型以返回 double，但它将始终返回整数值。

### <a name="remarks"></a>备注

此函数的返回值范围是 8.77 e7 和 8.77 e7 之间的值。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [获取时间](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

请参阅[GetTotalDays](#gettotaldays)的示例。

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes

检索以分钟表示的此日期/时间跨度值。

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值，以分钟为单位。 尽管此函数是原型以返回 double，但它将始终返回整数值。

### <a name="remarks"></a>备注

此函数的返回值范围是 5.26 e9 和 5.26 e9 之间的值。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [获取时间](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

请参阅[GetTotalDays](#gettotaldays)的示例。

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds

检索以秒表示的此日期/时间跨度值。

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>返回值

此日期/时间跨度值（以秒为单位）。 尽管此函数是原型以返回 double，但它将始终返回整数值。

### <a name="remarks"></a>备注

此函数的返回值范围是从大约 3.16 e11 到 3.16 e11 之间的值。

有关查询对象的值的其他函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [获取时间](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>示例

请参阅[GetTotalDays](#gettotaldays)的示例。

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan：： m_span

**`double`** 此对象的基础值 `COleDateTime` 。

```
double m_span;
```

### <a name="remarks"></a>备注

此值以天为单位表示日期/时间跨度。

> [!CAUTION]
> 更改数据成员中的值 **`double`** 将更改此对象的值 `COleDateTimeSpan` 。 它不会更改此对象的状态 `COleDateTimeSpan` 。

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan：： m_status

此数据成员的类型是在 `DateTimeSpanStatus` 类中定义的枚举类型 `COleDateTimeSpan` 。

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

- `COleDateTimeSpan::valid`指示此 `COleDateTimeSpan` 对象有效。

- `COleDateTimeSpan::invalid`指示此 `COleDateTimeSpan` 对象无效; 也就是说，它的值可能不正确。

- `COleDateTimeSpan::null`指示此 `COleDateTimeSpan` 对象为 null，即没有为此对象提供值。 （这在数据库意义上是 "null"，而不是 c + + NULL。）

对象的状态 `COleDateTimeSpan` 在下列情况下无效：

- 如果此对象在算术赋值操作期间遇到溢出或下溢，则为 `+=` 或 `-=` 。

- 如果分配给此对象的值无效。

- 如果使用[SetStatus](#setstatus)将此对象的状态显式设置为无效，则为。

有关可能将状态设置为 "无效" 的操作的详细信息，请参阅[COleDateTimeSpan：： operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan：： operator + =，-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

> [!CAUTION]
> 此数据成员适用于高级编程情况。 应使用内联成员函数[GetStatus](#getstatus)和[SetStatus](#setstatus)。 `SetStatus`有关显式设置此数据成员的其他注意事项，请参阅。

有关值界限的详细信息 `COleDateTimeSpan` ，请参阅文章[日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan：： operator =

复制 `COleDateTimeSpan` 值。

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>备注

此重载赋值运算符将源日期/时间范围值复制到此 `COleDateTimeSpan` 对象中。

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan：： operator +，-

添加、减和更改值的符号 `COleDateTimeSpan` 。

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>备注

前两个运算符允许添加和减少日期/时间跨度值。 第三种是允许您更改日期/时间范围值的符号。

如果任一操作数为 null，则结果值的状态 `COleDateTimeSpan` 为 null。

如果其中一个操作数无效，而另一个不为 null，则结果值的状态 `COleDateTimeSpan` 将无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan：： operator + =，-=

`COleDateTimeSpan`在此值中添加和减去值 `COleDateTimeSpan` 。

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>备注

通过这些运算符，可以在此对象中添加和减少日期/时间范围值 `COleDateTimeSpan` 。 如果任一操作数为 null，则结果值的状态 `COleDateTimeSpan` 为 null。

如果其中一个操作数无效，而另一个不为 null，则结果值的状态 `COleDateTimeSpan` 将无效。

有关有效、无效和 null 状态值的详细信息，请参阅[m_status](#m_status)成员变量。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan：： operator double

将此 `COleDateTimeSpan` 值转换为 **`double`** 。

```
operator double() const throw();
```

### <a name="remarks"></a>备注

此运算符将该值值 `COleDateTimeSpan` 作为浮点数返回。

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan

设置此日期/时间范围值的值。

```cpp
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>参数

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
指示要复制到此对象中的日期跨度和时间跨度值 `COleDateTimeSpan` 。

### <a name="remarks"></a>备注

对于查询对象的值的函数 `COleDateTimeSpan` ，请参阅以下成员函数：

- [GetDays](#getdays)

- [获取时间](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimeSpan：： SetStatus

设置此对象的状态（有效性） `COleDateTimeSpan` 。

```cpp
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>参数

*status*<br/>
此对象的新状态值 `COleDateTimeSpan` 。

### <a name="remarks"></a>备注

*状态*参数值由 `DateTimeSpanStatus` 枚举类型定义，该类型是在类中定义的 `COleDateTimeSpan` 。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

有关这些状态值的简要说明，请参阅以下列表：

- `COleDateTimeSpan::valid`指示此 `COleDateTimeSpan` 对象有效。

- `COleDateTimeSpan::invalid`指示此 `COleDateTimeSpan` 对象无效; 也就是说，它的值可能不正确。

- `COleDateTimeSpan::null`指示此 `COleDateTimeSpan` 对象为 null，即没有为此对象提供值。 （这在数据库意义上是 "null"，而不是 c + + NULL。）

   > [!CAUTION]
   > 此函数适用于高级编程情况。 此函数不会更改此对象中的数据。 通常用于将状态设置为**null**或**无效**。 请注意，赋值运算符（[operator =](#operator_eq)）和[SetDateTimeSpan](#setdatetimespan)根据源值设置对象的状态。

### <a name="example"></a>示例

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>另请参阅

[COleDateTime 类](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime 类](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 类](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
