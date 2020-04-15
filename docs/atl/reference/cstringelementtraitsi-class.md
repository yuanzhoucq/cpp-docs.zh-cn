---
title: 弦元素特性I类
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 32980e19443cb17a3a688c85ff21195c60ed2124
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330587"
---
# <a name="cstringelementtraitsi-class"></a>弦元素特性I类

此类提供与集合类对象中存储的字符串相关的静态函数。 它类似于[CStringElementTraits，](../../atl/reference/cstringelementtraits-class.md)但执行不区分大小写的比较。

## <a name="syntax"></a>语法

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[弦元素特征I：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|
|[弦元素特征I：OUTARGTYPE](#outargtype)|用于从集合类对象检索元素的数据类型。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[弦元素特征I：比较元素](#compareelements)|调用此静态函数以比较两个字符串元素以实现相等性，忽略情况下的差异。|
|[弦元素特征I：：比较元素排序](#compareelementsordered)|调用此静态函数以比较两个字符串元素，忽略情况下的差异。|
|[弦乐元素：哈希](#hash)|调用此静态函数以计算给定字符串元素的哈希值。|

## <a name="remarks"></a>备注

此类提供用于比较字符串和创建哈希值的静态函数。 当使用集合类存储基于字符串的数据时，这些函数非常有用。 当要处理字符串对象作为引用处理时，请使用[CStringRefElementTraits。](../../atl/reference/cstringrefelementtraits-class.md)

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[元素库](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a>弦元素特征I：比较元素

调用此静态函数以比较两个字符串元素以实现相等性，忽略情况下的差异。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串元素。

*str2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果元素相等，则返回 true，否则为 false。

### <a name="remarks"></a>备注

比较不区分大小写。

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>弦元素特征I：：比较元素排序

调用此静态函数以比较两个字符串元素，忽略情况下的差异。

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

### <a name="remarks"></a>备注

比较不区分大小写。

## <a name="cstringelementtraitsihash"></a><a name="hash"></a>弦乐元素：哈希

调用此静态函数以计算给定字符串元素的哈希值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>参数

*Str*<br/>
字符串元素。

### <a name="return-value"></a>返回值

返回使用字符串内容计算的哈希值。

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a>弦元素特征I：：INARGTYPE

用于向集合类对象添加元素的数据类型。

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a>弦元素特征I：OUTARGTYPE

用于从集合类对象检索元素的数据类型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>另请参阅

[CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits 类](../../atl/reference/cstringelementtraits-class.md)
