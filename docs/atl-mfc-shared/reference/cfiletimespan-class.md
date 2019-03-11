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
ms.openlocfilehash: 001e6ddc78a41e118949e9b750b78609f3ff9e92
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746430"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 类

此类提供用于管理相对日期和时间值与文件关联的方法。

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
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|调用此方法来检索从的时间跨度`CFileTimeSpan`对象。|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|调用此方法以设置的时间跨度`CFileTimeSpan`对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CFileTimeSpan::operator -](#operator_-)|在执行减法`CFileTimeSpan`对象。|
|[CFileTimeSpan::operator !=](#operator_neq)|比较两个 `CFileTimeSpan` 对象是否相等。|
|[CFileTimeSpan::operator +](#operator_add)|在执行加法运算`CFileTimeSpan`对象。|
|[CFileTimeSpan::operator +=](#operator_add_eq)|在执行加法运算`CFileTimeSpan`对象，并将结果分配给当前对象。|
|[CFileTimeSpan::operator &lt;](#operator_lt)|比较两个`CFileTimeSpan`对象以确定较小值。|
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|比较两个`CFileTimeSpan`对象以确定是否相等或较小值。|
|[CFileTimeSpan::operator =](#operator_eq)|赋值运算符。|
|[CFileTimeSpan::operator -=](#operator_-_eq)|在执行减法`CFileTimeSpan`对象，并将结果分配给当前对象。|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|比较两个 `CFileTimeSpan` 对象是否相等。|
|[CFileTimeSpan::operator &gt;](#operator_gt)|比较两个`CFileTimeSpan`对象以确定较大者。|
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|比较两个`CFileTimeSpan`对象以确定是否相等或较大者。|

## <a name="remarks"></a>备注

此类提供用于管理相对句点方法的时间，经常会遇到时执行操作在何时文件已创建、 上一次访问或上次修改时间。 此类的方法与结合使用常用[CFileTime 类](../../atl-mfc-shared/reference/cfiletime-class.md)对象。

## <a name="example"></a>示例

有关示例，请参阅[CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)。

## <a name="requirements"></a>要求

**标头：** atltime.h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

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
以毫秒为单位的时间段。

### <a name="remarks"></a>备注

`CFileTimeSpan`可创建对象，使用一个现有`CFileTimeSpan`对象，或者表示为一个 64 位值。 默认构造函数设置为 0 的时间跨度。

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

调用此方法来检索从的时间跨度`CFileTimeSpan`对象。

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>返回值

返回以毫秒为单位的时间跨度。

##  <a name="operator_-"></a>  CFileTimeSpan::operator -

在执行减法`CFileTimeSpan`对象。

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回`CFileTimeSpan`对象，表示两个时间范围之间的差异的结果。

##  <a name="operator_neq"></a>  CFileTimeSpan::operator !=

比较两个 `CFileTimeSpan` 对象是否相等。

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果要比较的项不相等，则返回 TRUE`CFileTimeSpan`对象; 否则为 FALSE。

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

在执行加法运算`CFileTimeSpan`对象。

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回`CFileTimeSpan`对象包含两个时间之和的跨越。

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator + =

在执行加法运算`CFileTimeSpan`对象，并将结果分配给当前对象。

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回已更新`CFileTimeSpan`对象包含两个时间之和的跨越。

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

比较两个`CFileTimeSpan`对象以确定较小值。

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回 TRUE，如果第一个对象小于 （即，表示较短的时间段） 的第二个，否则为 FALSE。

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

比较两个`CFileTimeSpan`对象以确定是否相等或较小值。

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于 （即，表示较短的时间段），则返回 TRUE 或等于第二个返回; 否则为 FALSE。

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

赋值运算符。

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回已更新`CFileTimeSpan`对象。

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator -=

在执行减法`CFileTimeSpan`对象，并将结果分配给当前对象。

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*span*<br/>
一个 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回已更新`CFileTimeSpan`对象。

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

比较两个 `CFileTimeSpan` 对象是否相等。

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果对象相等，否则为 FALSE，则返回 TRUE。

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

比较两个`CFileTimeSpan`对象以确定较大者。

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

是否大于第一个对象，则返回 TRUE （也就是说，表示更长的时间） 的第二个，否则为 FALSE。

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

比较两个`CFileTimeSpan`对象以确定是否相等或较大者。

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*span*<br/>
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

是否大于第一个对象，则返回 TRUE （也就是说，表示更长的时间） 或等于第二个，否则为 FALSE。

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

调用此方法以设置的时间跨度`CFileTimeSpan`对象。

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>参数

*nSpan*<br/>
以毫秒为单位的时间跨度的新值。

## <a name="see-also"></a>请参阅

[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime 类](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
