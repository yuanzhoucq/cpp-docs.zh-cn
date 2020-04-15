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
ms.openlocfilehash: d137a35a517ea93139f036f6e9a7a8de06d518a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330744"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper 类

此类是[CSimpleMap](../../atl/reference/csimplemap-class.md)类的帮助程序。

## <a name="syntax"></a>语法

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>参数

*TKey*<br/>
关键元素。

*TVal*<br/>
值元素。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSimpleMap平等帮助者：：是平等密钥](#isequalkey)|（静态）测试两个键的相等性。|
|[CSimpleMap 等值帮助者：：等于值](#isequalvalue)|（静态）测试两个值的相等性。|

## <a name="remarks"></a>备注

此特征类是对`CSimpleMap`类的补充。 它提供了比较两`CSimpleMap`个对象元素（特别是键和值组件）的相等性的方法。 默认情况下，使用**运算符 _（）** 比较键和值，但如果地图包含缺少其自身相等运算符的复杂数据类型，则可以重写此类以提供所需的额外功能。

## <a name="requirements"></a>要求

**标题：** atlsimpcoll.h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMap平等帮助者：：是平等密钥

测试两个键的相等性。

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>参数

*k1*<br/>
第一个键。

*k2*<br/>
第二个键。

### <a name="return-value"></a>返回值

如果键相等，则返回 true，否则为 false。

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMap 等值帮助者：：等于值

测试两个值的相等性。

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>参数

*v1*<br/>
第一个值。

*v2*<br/>
第二个值。

### <a name="return-value"></a>返回值

如果值相等，则返回 true，否则为 false。

## <a name="see-also"></a>另请参阅

[CSimpleMapEqualHelperFalse 类](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
