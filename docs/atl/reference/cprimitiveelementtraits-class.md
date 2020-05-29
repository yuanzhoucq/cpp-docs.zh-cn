---
title: CPrimitiveElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 6b45d93420d1832091cc451a3e6eb309f61d07a3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331437"
---
# <a name="cprimitiveelementtraits-class"></a>CPrimitiveElementTraits 类

此类为由基元数据类型组成的集合类提供默认方法和函数。

## <a name="syntax"></a>语法

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合类对象中的数据类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[原始元素：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|
|[原始元素：：OUTARGTYPE](#outargtype)|用于从集合类对象检索元素的数据类型。|

## <a name="remarks"></a>备注

此类提供用于移动、复制、比较和哈希存储在集合类对象中的原始数据类型元素的默认静态函数和方法。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[C默认比较特征](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[元素库](../../atl/reference/celementtraitsbase-class.md)

[CDefault元素](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a>原始元素：：INARGTYPE

用于向集合类对象添加元素的数据类型。

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a>原始元素：：OUTARGTYPE

用于从集合类对象检索元素的数据类型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>另请参阅

[CDefaultElementTraits 类](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
