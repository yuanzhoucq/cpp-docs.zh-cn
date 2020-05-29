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
ms.openlocfilehash: 2c2f8b787e5366ec893538a88049f6f53dc35caf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327386"
---
# <a name="ccomsafearraybound-class"></a>CComSafeArrayBound 类

此类是[SAFEARRAYBOUND](/windows/win32/api/oaidl/ns-oaidl-safearraybound)结构的包装器。

## <a name="syntax"></a>语法

```
class CComSafeArrayBound : public SAFEARRAYBOUND
```

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CComSafeArray绑定](#ccomsafearraybound)|构造函数。|
|[GetCount](#getcount)|调用此方法以返回元素数。|
|[获取下限](#getlowerbound)|调用此方法以返回下限。|
|[获取上部](#getupperbound)|调用此方法以返回上限。|
|[设置计数](#setcount)|调用此方法以设置元素数。|
|[设置下限](#setlowerbound)|调用此方法以设置下限。|

### <a name="operators"></a>运算符

|||
|-|-|
|[运算符 |](#operator_eq)|将`CComSafeArrayBound`设为新值。|

## <a name="remarks"></a>备注

此类是[CComSafeArray](../../atl/reference/ccomsafearray-class.md)`SAFEARRAYBOUND`使用的结构的包装器。 它提供了查询和设置`CComSafeArray`对象单个维度的上限和下限及其包含的元素数的方法。 多维`CComSafeArray`对象使用`CComSafeArrayBound`对象数组，每个维度一个。 因此，当使用[GetCount](#getcount)等方法时，请注意此方法不会返回多维数组中的元素总数。

**标头：** atlsafe.h

## <a name="requirements"></a>要求

**标头：** atlsafe.h

## <a name="ccomsafearrayboundccomsafearraybound"></a><a name="ccomsafearraybound"></a>CComSafeArray绑定：：CcomSafearray绑定

构造函数。

```
CComSafeArrayBound(ULONG ulCount = 0, LONG lLowerBound = 0) throw();
```

### <a name="parameters"></a>参数

*ulCount*<br/>
数组中的元素数。

*lLowerBound*<br/>
对数组进行编号的下限。

### <a name="remarks"></a>备注

如果要从C++程序访问阵列，建议将下限定义为 0。 如果数组要与其他语言（如 Visual Basic）一起使用，则最好使用不同的下限值。

## <a name="ccomsafearrayboundgetcount"></a><a name="getcount"></a>CComSafeArray绑定：：获取计数

调用此方法以返回元素数。

```
ULONG GetCount() const throw();
```

### <a name="return-value"></a>返回值

返回元素数。

### <a name="remarks"></a>备注

如果关联的`CComSafeArray`对象表示多维数组，则此方法将仅返回最右侧维度中的元素总数。 使用[CComSafeArray：getCount](../../atl/reference/ccomsafearray-class.md#getcount)获取元素的总数。

## <a name="ccomsafearrayboundgetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray绑定：：获取下限

调用此方法以返回下限。

```
LONG GetLowerBound() const throw();
```

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象的下限。

## <a name="ccomsafearrayboundgetupperbound"></a><a name="getupperbound"></a>CComSafeArray绑定：：获取上部

调用此方法以返回上限。

```
LONG GetUpperBound() const throw();
```

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象的上限。

### <a name="remarks"></a>备注

上限取决于元素数和下限值。 例如，如果下限为 0，元素数为 10，则上限将自动设置为 9。

## <a name="ccomsafearrayboundoperator-"></a><a name="operator_eq"></a>CComSafeArray绑定：：操作员 |

将`CComSafeArrayBound`设为新值。

```
CComSafeArrayBound& operator= (const CComSafeArrayBound& bound) throw();
CComSafeArrayBound& operator= (ULONG ulCount) throw();
```

### <a name="parameters"></a>参数

*绑定*<br/>
`CComSafeArrayBound` 对象。

*ulCount*<br/>
元素数量。

### <a name="return-value"></a>返回值

返回指向对象的`CComSafeArrayBound`指针。

### <a name="remarks"></a>备注

可以使用`CComSafeArrayBound`现有`CComSafeArrayBound`分配对象，也可以通过提供元素数来分配该对象，在这种情况下，默认情况下下限设置为 0。

## <a name="ccomsafearrayboundsetcount"></a><a name="setcount"></a>CComSafeArray绑定：：设置计数

调用此方法以设置元素数。

```
ULONG SetCount(ULONG ulCount) throw();
```

### <a name="parameters"></a>参数

*ulCount*<br/>
元素数量。

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象中的元素数。

## <a name="ccomsafearrayboundsetlowerbound"></a><a name="setlowerbound"></a>CComSafeArray绑定：：设置下限

调用此方法以设置下限。

```
LONG SetLowerBound(LONG lLowerBound) throw();
```

### <a name="parameters"></a>参数

*lLowerBound*<br/>
下限。

### <a name="return-value"></a>返回值

返回`CComSafeArrayBound`对象的新下限。

### <a name="remarks"></a>备注

如果要从 Visual C++ 程序访问阵列，建议将下限定义为 0。 如果数组要与其他语言（如 Visual Basic）一起使用，则最好使用不同的下限值。

上限取决于元素数和下限值。 例如，如果下限为 0，元素数为 10，则上限将自动设置为 9。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
