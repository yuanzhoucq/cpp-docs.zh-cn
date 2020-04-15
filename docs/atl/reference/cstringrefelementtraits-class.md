---
title: CStringRefElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: b4dd76b9592b255a1553be3ca7a249f58fb2672e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330583"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits 类

此类提供与集合类对象中存储的字符串相关的静态函数。 字符串对象作为引用处理。

## <a name="syntax"></a>语法

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStringRefElement：：比较元素](#compareelements)|调用此静态函数以比较两个字符串元素以获得相等性。|
|[CStringRefElement：：比较元素排序](#compareelementsordered)|调用此静态函数以比较两个字符串元素。|
|[弦乐元素：哈希](#hash)|调用此静态函数以计算给定字符串元素的哈希值。|

## <a name="remarks"></a>备注

此类提供用于比较字符串和创建哈希值的静态函数。 当使用集合类存储基于字符串的数据时，这些函数非常有用。 与[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)和[CStringElementTraitsI 不同](../../atl/reference/cstringelementtraitsi-class.md)，`CStringRefElementTraits``CString`这些参数作为**const**`CString&`引用传递。

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[元素库](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElement：：比较元素

调用此静态函数以比较两个字符串元素以获得相等性。

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>参数

*元素1*<br/>
第一个字符串元素。

*元素2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果元素相等，则返回 true，否则为 false。

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElement：：比较元素排序

调用此静态函数以比较两个字符串元素。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串元素。

*str2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果字符串相同，则为零，如果*str1*小于*str2，* 则< 0;如果*str1*大于*str2，* 则> 0。 [CStringT：：比较](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>弦乐元素：哈希

调用此静态函数以计算给定字符串元素的哈希值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>参数

*Str*<br/>
字符串元素。

### <a name="return-value"></a>返回值

返回使用字符串内容计算的哈希值。

## <a name="see-also"></a>另请参阅

[CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
