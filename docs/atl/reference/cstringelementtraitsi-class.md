---
title: CStringElementTraitsI 类
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
ms.openlocfilehash: 35215546268c4c48f913e7aef763768fffc76d59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551718"
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI 类

此类提供与集合类对象中存储的字符串相关的静态函数。 它是类似于[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)，但执行不区分大小写的比较。

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

|名称|描述|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|调用此静态函数以比较两个字符串元素相等性，忽略大小写不同的。|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|调用此静态函数以比较两个字符串元素，忽略大小写不同的。|
|[CStringElementTraitsI::Hash](#hash)|调用此静态函数以计算给定的字符串元素的哈希值。|

## <a name="remarks"></a>备注

此类提供静态函数对字符串进行比较和用于创建哈希值。 使用集合类来存储基于字符串的数据时，这些函数很有用。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)字符串对象时要与处理作为引用。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="compareelements"></a>  CStringElementTraitsI::CompareElements

调用此静态函数以比较两个字符串元素相等性，忽略大小写不同的。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串元素。

*str2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果元素均相等，则返回 false，则返回 true。

### <a name="remarks"></a>备注

比较不区分大小写。

##  <a name="compareelementsordered"></a>  CStringElementTraitsI::CompareElementsOrdered

调用此静态函数以比较两个字符串元素，忽略大小写不同的。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串元素。

*str2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果字符串相等则为零，< 0 如果*str1*是小于*str2*，或 > 0 如果*str1*大于*str2*。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。

### <a name="remarks"></a>备注

比较不区分大小写。

##  <a name="hash"></a>  CStringElementTraitsI::Hash

调用此静态函数以计算给定的字符串元素的哈希值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>参数

*str*<br/>
字符串元素中。

### <a name="return-value"></a>返回值

返回使用字符串的内容计算的哈希值。

##  <a name="inargtype"></a>  CStringElementTraitsI::INARGTYPE

要用于将元素添加到集合类对象的数据类型。

```
typedef T::PCXSTR INARGTYPE;
```

##  <a name="outargtype"></a>  CStringElementTraitsI::OUTARGTYPE

要用于从集合类对象中检索元素的数据类型。

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>请参阅

[CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)<br/>
[CStringElementTraits 类](../../atl/reference/cstringelementtraits-class.md)
