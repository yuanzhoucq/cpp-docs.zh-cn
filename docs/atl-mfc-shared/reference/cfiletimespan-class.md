---
title: CFileTimeSpan 类
description: 活动模板库 （ATL） 和 Microsoft 基础类 （MFC） CFileTimeSpan 类以 FILETIME 单位为单位管理时间间隔。
ms.date: 01/10/2020
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
ms.openlocfilehash: 87737ea1c778660a68510b484bcdfa3a4670e8ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317852"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 类

此类提供用于管理与文件关联的相对日期和时间值的方法。

## <a name="syntax"></a>语法

```cpp
class CFileTimeSpan
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[文件时间跨度：：文件时间跨度](#cfiletimespan)|构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[文件时间跨度：获取时间跨度](#gettimespan)|调用此方法以从`CFileTimeSpan`对象检索时间跨度。|
|[文件时间跨度：：设置时间跨度](#settimespan)|调用此方法以设置`CFileTimeSpan`对象的时间跨度。|

### <a name="public-operators"></a>公共运营商

|名称|说明|
|----------|-----------------|
|[文件时间跨度：：运算符 -](#operator_-)|对`CFileTimeSpan`对象执行减法。|
|[文件时间跨度：：操作员！*](#operator_neq)|比较两个 `CFileTimeSpan` 对象是否相等。|
|[文件时间跨度：：操作员 |](#operator_add)|对`CFileTimeSpan`对象执行添加。|
|[文件时间跨度：：操作员 |](#operator_add_eq)|对`CFileTimeSpan`对象执行添加，并将结果分配给当前对象。|
|[文件时间跨度：：运算符&lt;](#operator_lt)|比较两`CFileTimeSpan`个对象以确定较小的对象。|
|[文件时间跨度：：运算符&lt;=](#operator_lt_eq)|比较两`CFileTimeSpan`个对象以确定相等性或较小的对象。|
|[文件时间跨度：：运算符 |](#operator_eq)|分配运算符。|
|[文件时间跨度：：运算符 -*](#operator_-_eq)|对`CFileTimeSpan`对象执行减法，并将结果分配给当前对象。|
|[文件时间跨度：：运算符 |](#operator_eq_eq)|比较两个 `CFileTimeSpan` 对象是否相等。|
|[文件时间跨度：：运算符&gt;](#operator_gt)|比较两`CFileTimeSpan`个对象以确定较大的对象。|
|[文件时间跨度：：运算符&gt;=](#operator_gt_eq)|比较两`CFileTimeSpan`个对象以确定相等性或较大。|

## <a name="remarks"></a>备注

该`CFileTimeSpan`类提供了处理文件系统使用单位中相对时间段的方法。 这些单元通常用于文件操作，例如创建文件、上次访问或上次修改文件的时间。 此类的方法经常与[CFileTime 类](../../atl-mfc-shared/reference/cfiletime-class.md)对象结合使用。

## <a name="example"></a>示例

请参阅[CFileTime：：毫秒的示例](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)。

## <a name="requirements"></a>要求

**标题：** atltime.h

## <a name="cfiletimespancfiletimespan"></a><a name="cfiletimespan"></a>文件时间跨度：：文件时间跨度

构造函数。

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>参数

*跨度*\
一个现有的 `CFileTimeSpan` 对象。

*恩斯潘*\
以 FILETIME 单位为单位的时间段。

### <a name="remarks"></a>备注

可以使用`CFileTimeSpan`现有`CFileTimeSpan`对象创建对象，或以 100 纳秒的 FILETIME 单位表示为 64 位值。 有关详细信息，请参阅[CFileTime](cfiletime-class.md)。 默认构造函数将时间跨度设置为 0。

## <a name="cfiletimespangettimespan"></a><a name="gettimespan"></a>文件时间跨度：获取时间跨度

调用此方法以从`CFileTimeSpan`对象检索时间跨度。

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>返回值

返回以 100 纳秒 FILETIME 单位为单位的时间跨度。 有关详细信息，请参阅[CFileTime](cfiletime-class.md)。

## <a name="cfiletimespanoperator--"></a><a name="operator_-"></a>文件时间跨度：：运算符 -

对`CFileTimeSpan`对象执行减法。

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
`CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回表示`CFileTimeSpan`两个时间跨度之间差值结果的对象。

## <a name="cfiletimespanoperator-"></a><a name="operator_neq"></a>文件时间跨度：：操作员！*

比较两个 `CFileTimeSpan` 对象是否相等。

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果要比较的项不等于对象，`CFileTimeSpan`则返回 TRUE;否则 FALSE。

## <a name="cfiletimespanoperator-"></a><a name="operator_add"></a>文件时间跨度：：操作员 |

对`CFileTimeSpan`对象执行添加。

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
`CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回包含`CFileTimeSpan`两个时间跨度总和的对象。

## <a name="cfiletimespanoperator-"></a><a name="operator_add_eq"></a>文件时间跨度：：操作员 |

对`CFileTimeSpan`对象执行添加，并将结果分配给当前对象。

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*跨度*\
`CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回包含两`CFileTimeSpan`个时间跨度总和的更新对象。

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt"></a>文件时间跨度：：运算符&lt;

比较两`CFileTimeSpan`个对象以确定较小的对象。

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于第二个对象（即表示较短的时间段），则返回 TRUE，否则为 FALSE。

## <a name="cfiletimespanoperator-lt"></a><a name="operator_lt_eq"></a>文件时间跨度：：运算符&lt;=

比较两`CFileTimeSpan`个对象以确定相等性或较小的对象。

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于（即表示较短的时间段）或等于第二个对象，否则为 FALSE，则返回 TRUE。

## <a name="cfiletimespanoperator-"></a><a name="operator_eq"></a>文件时间跨度：：运算符 |

分配运算符。

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>参数

*跨度*\
`CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回更新`CFileTimeSpan`的对象。

## <a name="cfiletimespanoperator--"></a><a name="operator_-_eq"></a>文件时间跨度：：运算符 -*

对`CFileTimeSpan`对象执行减法，并将结果分配给当前对象。

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>参数

*跨度*\
`CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

返回更新`CFileTimeSpan`的对象。

## <a name="cfiletimespanoperator-"></a><a name="operator_eq_eq"></a>文件时间跨度：：运算符 |

比较两个 `CFileTimeSpan` 对象是否相等。

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果对象相等，则返回 TRUE，否则为 FALSE。

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt"></a>文件时间跨度：：运算符&gt;

比较两`CFileTimeSpan`个对象以确定较大的对象。

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于（即表示较长的时间段）大于第二个对象（否则 FALSE），则返回 TRUE。

## <a name="cfiletimespanoperator-gt"></a><a name="operator_gt_eq"></a>文件时间跨度：：运算符&gt;=

比较两`CFileTimeSpan`个对象以确定相等性或较大。

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>参数

*跨度*\
要比较的 `CFileTimeSpan` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于（即表示较长的时间段）或等于第二个对象，否则为 FALSE，则返回 TRUE。

## <a name="cfiletimespansettimespan"></a><a name="settimespan"></a>文件时间跨度：：设置时间跨度

调用此方法以设置`CFileTimeSpan`对象的时间跨度。

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>参数

*恩斯潘*\
时间跨度的新值（以 100 纳秒的 FILETIME 单位为单位）。 有关详细信息，请参阅[CFileTime](cfiletime-class.md)。

## <a name="see-also"></a>另请参阅

[文件时间](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[文件时间类](cfiletime-class.md)\
[层次结构图表](../../mfc/hierarchy-chart.md)\
[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
