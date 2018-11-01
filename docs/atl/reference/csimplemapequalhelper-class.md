---
title: CSimpleMapEqualHelper 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: a530254bbaabce723b97d21313abb81e1b375833
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527382"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper 类

此类是一个帮助程序对于[CSimpleMap](../../atl/reference/csimplemap-class.md)类。

## <a name="syntax"></a>语法

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>参数

*TKey*<br/>
键的元素。

*TVal*<br/>
Value 元素中。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|（静态）测试两个键相等。|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|（静态）测试两个值相等。|

## <a name="remarks"></a>备注

此特征类是对的补充`CSimpleMap`类。 它提供用于比较两个方法`CSimpleMap`对象是否相等的元素 （具体而言，键和值的组件）。 默认情况下的键和值使用比较**operator==()**，但如果映射包含缺少其自己的相等运算符的复杂数据类型，此类可以重写以提供需要更多的功能。

## <a name="requirements"></a>要求

**标头：** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

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

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

测试两个值相等。

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>参数

*v1*<br/>
第一个值。

*v2*<br/>
第二个值。

### <a name="return-value"></a>返回值

如果值均相等，则返回 false，则返回 true。

## <a name="see-also"></a>请参阅

[CSimpleMapEqualHelperFalse 类](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
