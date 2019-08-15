---
title: CComSafeArrayBound 类
ms.date: 05/06/2019
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
ms.openlocfilehash: bd77c2a788e769c74518d73b45c3c05ff27b3f58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496900"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 类

此类是[SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-tagsafearraybound)结构的包装器。

## <a name="syntax"></a>语法

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CComSafeArrayBound](#ccomsafearraybound)|构造函数。|
|[GetCount](#getcount)|调用此方法以返回元素的数目。|
|[GetLowerBound](#getlowerbound)|调用此方法以返回下限。|
|[GetUpperBound](#getupperbound)|调用此方法以返回上限。|
|[SetCount](#setcount)|调用此方法可设置元素的数目。|
|[SetLowerBound](#setlowerbound)|调用此方法可以设置下限。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator =](#operator_eq)|将设置`CComSafeArrayBound`为新值。|

## <a name="remarks"></a>备注

此类是`SAFEARRAYBOUND` [CComSafeArray](../../atl/reference/ccomsafearray-class.md)使用的结构的包装器。 它提供用于查询和设置`CComSafeArray`对象的单个维度的上限和下限以及它所包含的元素数的方法。 多维`CComSafeArray`对象使用`CComSafeArrayBound`对象的数组, 每个维度对应一个对象。 因此, 使用[GetCount](#getcount)等方法时, 请注意, 此方法不会返回多维数组中的元素总数。

**标头：** atlsafe.h

## <a name="requirements"></a>要求

**标头：** atlsafe.h

##  <a name="ccomsafearraybound"></a>CComSafeArrayBound::CComSafeArrayBound

构造函数。

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>参数

*ulCount*<br/>
数组中的元素数。

*lLowerBound*<br/>
数组的编号下限。

### <a name="remarks"></a>备注

如果要从C++程序访问数组, 则建议将下限定义为0。 如果数组要与其他语言 (如 Visual Basic) 一起使用, 则最好使用其他下限值。

##  <a name="getcount"></a>CComSafeArrayBound:: GetCount

调用此方法以返回元素的数目。

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回元素的数目。

### <a name="remarks"></a>备注

如果关联`CComSafeArray`的对象表示一个多维数组, 则此方法将仅返回最右侧维度中的元素总数。 使用[CComSafeArray:: GetCount](../../atl/reference/ccomsafearray-class.md#getcount)获取元素总数。

##  <a name="getlowerbound"></a>CComSafeArrayBound::GetLowerBound

调用此方法以返回下限。

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象的下限。

##  <a name="getupperbound"></a>CComSafeArrayBound:: System.array.getupperbound

调用此方法以返回上限。

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象的上限。

### <a name="remarks"></a>备注

上限取决于元素数和下限值。 例如, 如果下限为 0, 元素数为 10, 则上限将自动设置为9。

##  <a name="operator_eq"></a>CComSafeArrayBound:: operator =

将设置`CComSafeArrayBound`为新值。

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

返回一个指向`CComSafeArrayBound`对象的指针。

### <a name="remarks"></a>备注

可以使用现有`CComSafeArrayBound`的或通过提供元素数来分配对象,在这种情况下,下限默认设置为0。`CComSafeArrayBound`

##  <a name="setcount"></a>CComSafeArrayBound::SetCount

调用此方法可设置元素的数目。

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>参数

*ulCount*<br/>
元素数量。

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象中的元素数。

##  <a name="setlowerbound"></a>CComSafeArrayBound::SetLowerBound

调用此方法可以设置下限。

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>参数

*lLowerBound*<br/>
下限。

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象的新下限。

### <a name="remarks"></a>备注

如果要从视觉对象C++程序访问该数组, 则建议将下限定义为0。 如果数组要与其他语言 (如 Visual Basic) 一起使用, 则最好使用其他下限值。

上限取决于元素数和下限值。 例如, 如果下限为 0, 元素数为 10, 则上限将自动设置为9。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
