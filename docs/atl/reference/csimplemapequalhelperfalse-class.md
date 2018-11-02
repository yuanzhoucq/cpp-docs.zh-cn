---
title: CSimpleMapEqualHelperFalse 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: 7ccfe59e6741c267aded8f59828947a1d98bfbc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572687"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse 类

此类是一个帮助程序对于[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

## <a name="syntax"></a>语法

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|（静态）测试两个键相等。|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|（静态）返回 false。|

## <a name="remarks"></a>备注

此特征类是对的补充`CSimpleMap`类。 它提供了方法来比较两个元素中包含`CSimpleMap`对象，特别是两个值元素或两个重要元素。

值比较将始终返回 false，并且除了，将调用`ATLASSERT`参数为 false，如果曾经引用它。 在相等性测试不足够定义位置的情况下，此类允许包含键/值对的大多数方法正常运行，但失败，如依赖于比较的方法的定义完善的方式映射[CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval)。

## <a name="requirements"></a>要求

**标头：** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey

测试两个键相等。

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>参数

*版 k1*<br/>
第一个键。

*k2*<br/>
第二个密钥。

### <a name="return-value"></a>返回值

如果键相等，则返回 false 否则，则返回 true。

### <a name="remarks"></a>备注

此方法调用[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)。

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue

返回 false。

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>返回值

返回 false。

### <a name="remarks"></a>备注

此方法始终返回 false，并将调用`ATLASSERT`参数为 false，如果曾经引用它。 用途`CSimpleMapEqualHelperFalse::IsEqualValue`是强制方法使用的比较时尚未充分定义相等性测试，以明确定义的方式失败。

## <a name="see-also"></a>请参阅

[CSimpleMapEqualHelper 类](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
