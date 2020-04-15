---
title: CSimpleArrayEqualHelper 类
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 386b005777b3e31dd74916a41bc5af2ab82df210
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330874"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper 类

此类是[CSimpleArray](../../atl/reference/csimplearray-class.md)类的帮助程序。

## <a name="syntax"></a>语法

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>参数

*T*<br/>
派生类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSimplearray 平等帮助者：：是相等的](#isequal)|（静态）测试两`CSimpleArray`个对象元素的相等性。|

## <a name="remarks"></a>备注

此特征类是对`CSimpleArray`类的补充。 它提供了一种比较存储在对象中的两个`CSimpleArray`元素的方法。 默认情况下，使用**运算符 _（）** 比较元素，但如果数组包含缺少其自身相等运算符的复杂数据类型，则需要重写此类。

## <a name="requirements"></a>要求

**标题：** atlsimpcoll.h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a>CSimplearray 平等帮助者：：是相等的

测试两`CSimpleArray`个对象元素的相等性。

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>参数

*t1*<br/>
一个 T 类型的对象。

*t2*<br/>
一个 T 类型的对象。

### <a name="return-value"></a>返回值

如果元素相等，则返回 true，否则为 false。

## <a name="see-also"></a>另请参阅

[CSimpleArray 类](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse 类](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
