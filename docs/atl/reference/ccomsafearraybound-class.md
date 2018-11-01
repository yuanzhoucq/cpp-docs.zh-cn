---
title: CComSafeArrayBound 类
ms.date: 11/04/2016
f1_keywords:
- CComSafeArrayBound
- ATLSAFE/ATL::CComSafeArrayBound
- ATLSAFE/ATL::GetCount
- ATLSAFE/ATL::GetLowerBound
- ATLSAFE/ATL::GetUpperBound
- ATLSAFE/ATL::SetCount
- ATLSAFE/ATL::SetLowerBound
helpviewer_keywords:
- CComSafeArrayBound class
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
ms.openlocfilehash: d57e038a4ebc55d08b4518f25e37b4f2d9cee05d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429193"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 类

此类是包装[SAFEARRAYBOUND](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearraybound)结构。

## <a name="syntax"></a>语法

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|构造函数。|
|[GetCount](#getcount)|调用此方法返回的元素数。|
|[GetLowerBound](#getlowerbound)|调用此方法以返回更低绑定。|
|[GetUpperBound](#getupperbound)|调用此方法以返回上限。|
|[SetCount](#setcount)|调用此方法以设置的元素数。|
|[SetLowerBound](#setlowerbound)|调用此方法以设置下限。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#operator_eq)|集`CComSafeArrayBound`为新值。|

## <a name="remarks"></a>备注

此类是包装`SAFEARRAYBOUND`结构，可由[CComSafeArray](../../atl/reference/ccomsafearray-class.md)。 它提供用于查询和设置的单个维度的上限和下限边界方法`CComSafeArray`对象和它包含的元素数。 多维`CComSafeArray`对象使用的数组`CComSafeArrayBound`对象，每个维度的一个对象。 因此，如使用方法时[GetCount](#getcount)，注意此方法将返回多维数组中的元素总数。

**标头：** atlsafe.h

## <a name="requirements"></a>要求

**标头：** atlsafe.h

##  <a name="ccomsafearraybound"></a>  CComSafeArrayBound::CComSafeArrayBound

构造函数。

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>参数

*ulCount*<br/>
数组中的元素数。

*lLowerBound*<br/>
从数组带编号的下限。

### <a name="remarks"></a>备注

如果数组是从 Visual c + + 程序进行访问，建议更低绑定被定义为 0。 它可能更可取的方法使用不同的下限值，如果数组为其他语言，如 Visual Basic 与一起使用。

##  <a name="getcount"></a>  CComSafeArrayBound::GetCount

调用此方法返回的元素数。

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回元素的数。

### <a name="remarks"></a>备注

如果关联`CComSafeArray`对象表示多维数组，此方法将仅在最右边的维度中返回的元素总数。 使用[CComSafeArray::GetCount](../../atl/reference/ccomsafearray-class.md#getcount)若要获取的元素总数。

##  <a name="getlowerbound"></a>  CComSafeArrayBound::GetLowerBound

调用此方法以返回更低绑定。

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>返回值

返回的下限`CComSafeArrayBound`对象。

##  <a name="getupperbound"></a>  CComSafeArrayBound::GetUpperBound

调用此方法以返回上限。

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>返回值

返回的上限`CComSafeArrayBound`对象。

### <a name="remarks"></a>备注

上限取决于元素和下界值的数目。 例如，如果下限为 0，元素数为 10，将自动为 9 设置上限。

##  <a name="operator_eq"></a>  CComSafeArrayBound::operator =

集`CComSafeArrayBound`为新值。

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>参数

*绑定*<br/>
一个 `CComSafeArrayBound` 对象。

*ulCount*<br/>
元素数量。

### <a name="return-value"></a>返回值

返回一个指向`CComSafeArrayBound`对象。

### <a name="remarks"></a>备注

`CComSafeArrayBound`对象可使用的现有分配`CComSafeArrayBound`，或通过提供在其中用例下界默认设置为 0 的元素数。

##  <a name="setcount"></a>  CComSafeArrayBound::SetCount

调用此方法以设置的元素数。

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>参数

*ulCount*<br/>
元素数量。

### <a name="return-value"></a>返回值

返回中的元素数`CComSafeArrayBound`对象。

##  <a name="setlowerbound"></a>  CComSafeArrayBound::SetLowerBound

调用此方法以设置下限。

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>参数

*lLowerBound*<br/>
下限。

### <a name="return-value"></a>返回值

返回的新下限`CComSafeArrayBound`对象。

### <a name="remarks"></a>备注

如果数组是从 Visual c + + 程序进行访问，建议更低绑定被定义为 0。 它可能更可取的方法使用不同的下限值，如果数组为其他语言，如 Visual Basic 与一起使用。

上限取决于元素和下界值的数目。 例如，如果下限为 0，元素数为 10，将自动为 9 设置上限。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
