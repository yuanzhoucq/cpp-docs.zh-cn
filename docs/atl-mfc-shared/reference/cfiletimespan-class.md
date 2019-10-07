---
title: CFileTimeSpan 类
ms.date: 10/18/2018
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: f9bb42ba4c142f671a83dcfa7e99cff940fff047
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491282"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 类

此类提供用于管理与文件关联的相对日期和时间值的方法。

## <a name="syntax"></a>语法

```
class CFileTimeSpan
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|调用此方法从`CFileTimeSpan`对象中检索时间跨度。|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|调用此方法可设置`CFileTimeSpan`对象的时间跨度。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CFileTimeSpan:: operator-](#operator_-)|对`CFileTimeSpan`对象执行减法运算。|
|[CFileTimeSpan::operator !=](#operator_neq)|比较两个 `CFileTimeSpan` 对象是否相等。|
|[CFileTimeSpan:: operator +](#operator_add)|对`CFileTimeSpan`对象执行加法。|
|[CFileTimeSpan:: operator + =](#operator_add_eq)|对`CFileTimeSpan`对象执行加法, 并将结果分配给当前的对象。|
|[CFileTimeSpan:: operator&lt;](#operator_lt)|比较两`CFileTimeSpan`个对象以确定较小的对象。|
|[CFileTimeSpan:: operator&lt;=](#operator_lt_eq)|比较两`CFileTimeSpan`个对象以确定是否相等或较低。|
|[CFileTimeSpan::operator =](#operator_eq)|赋值运算符。|
|[CFileTimeSpan::operator -=](#operator_-_eq)|对`CFileTimeSpan`对象执行减法运算, 并将结果赋给当前的对象。|
|[CFileTimeSpan:: operator = =](#operator_eq_eq)|比较两个 `CFileTimeSpan` 对象是否相等。|
|[CFileTimeSpan:: operator&gt;](#operator_gt)|比较两`CFileTimeSpan`个对象以确定更大的对象。|
|[CFileTimeSpan:: operator&gt;=](#operator_gt_eq)|比较两`CFileTimeSpan`个对象以确定相等或更大。|

## <a name="remarks"></a>备注

此类提供了一些方法, 用于管理在执行与文件创建、上次访问时间或上次修改时间有关的操作时经常遇到的相对时间段。 此类的方法经常与[CFileTime 类](../../atl-mfc-shared/reference/cfiletime-class.md)对象结合使用。

## <a name="example"></a>示例

请参阅[CFileTime:: 毫秒](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)的示例。

## <a name="requirements"></a>要求

**标头:** atltime

##  <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

构造函数。

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个现有的 `CFileTimeSpan` 对象。

*nSpan*<br/>
时间段 (以毫秒为单位)。

### <a name="remarks"></a>备注

对象可以使用现有`CFileTimeSpan`对象创建, 也可以表示为64位值。 `CFileTimeSpan` 默认构造函数将时间跨度设置为0。

##  <a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

调用此方法从`CFileTimeSpan`对象中检索时间跨度。

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>返回值

返回时间跨度 (以毫秒为单位)。

##  <a name="operator_-"></a>CFileTimeSpan:: operator-

对`CFileTimeSpan`对象执行减法运算。

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回一个`CFileTimeSpan`对象, 该对象表示两个时间范围之间的差异的结果。

##  <a name="operator_neq"></a>CFileTimeSpan:: operator! =

比较两个 `CFileTimeSpan` 对象是否相等。

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果要比较的项与`CFileTimeSpan`对象不相等, 则返回 TRUE; 否则返回 FALSE。

##  <a name="operator_add"></a>CFileTimeSpan:: operator +

对`CFileTimeSpan`对象执行加法。

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回一个`CFileTimeSpan`对象, 该对象包含两个时间范围之和。

##  <a name="operator_add_eq"></a>CFileTimeSpan:: operator + =

对`CFileTimeSpan`对象执行加法, 并将结果赋给当前的对象。

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回一个更新`CFileTimeSpan`的对象, 其中包含两个时间范围之和。

##  <a name="operator_lt"></a>CFileTimeSpan:: operator&lt;

比较两`CFileTimeSpan`个对象以确定较小的对象。

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于第二个对象 (即表示较短的时间段), 则返回 TRUE, 否则返回 FALSE。

##  <a name="operator_lt_eq"></a>CFileTimeSpan:: operator&lt;=

比较两`CFileTimeSpan`个对象以确定是否相等或较低。

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于 (即表示较短的时间段) 或等于第二个对象, 则返回 TRUE; 否则返回 FALSE。

##  <a name="operator_eq"></a>CFileTimeSpan:: operator =

赋值运算符。

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回已更新`CFileTimeSpan`的对象。

##  <a name="operator_-_eq"></a>CFileTimeSpan:: operator-=

对`CFileTimeSpan`对象执行减法运算, 并将结果赋给当前的对象。

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回已更新`CFileTimeSpan`的对象。

##  <a name="operator_eq_eq"></a>CFileTimeSpan:: operator = =

比较两个 `CFileTimeSpan` 对象是否相等。

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果对象相等, 则返回 TRUE; 否则返回 FALSE。

##  <a name="operator_gt"></a>CFileTimeSpan:: operator&gt;

比较两`CFileTimeSpan`个对象以确定更大的对象。

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于 (即表示较长的时间段) 而不是第二个对象, 则返回 TRUE; 否则返回 FALSE。

##  <a name="operator_gt_eq"></a>CFileTimeSpan:: operator&gt;=

比较两`CFileTimeSpan`个对象以确定相等或更大。

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于 (即表示较长的时间段) 或等于第二个对象, 则返回 TRUE; 否则返回 FALSE。

##  <a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

调用此方法可设置`CFileTimeSpan`对象的时间跨度。

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>参数

*nSpan*<br/>
时间跨度的新值 (以毫秒为单位)。

## <a name="see-also"></a>请参阅

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime 类](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
