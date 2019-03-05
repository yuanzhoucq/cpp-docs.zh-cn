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
ms.openlocfilehash: c57fda64689a80dfa548977e56b0416641bb4360
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301618"
---
# <a name="cstringrefelementtraits-class"></a>CStringRefElementTraits 类

此类提供与集合类对象中存储的字符串相关的静态函数。 以引用方式处理字符串对象。

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

|名称|描述|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|调用此静态函数以比较相等的两个字符串元素。|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|调用此静态函数以比较两个字符串元素。|
|[CStringRefElementTraits::Hash](#hash)|调用此静态函数以计算给定的字符串元素的哈希值。|

## <a name="remarks"></a>备注

此类提供静态函数对字符串进行比较和用于创建哈希值。 使用集合类来存储基于字符串的数据时，这些函数很有用。 与不同[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)并[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)，`CStringRefElementTraits`导致`CString`参数作为传递**const** `CString&`引用。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements

调用此静态函数以比较相等的两个字符串元素。

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>参数

*element1*<br/>
第一个字符串元素。

*element2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果元素均相等，则返回 false，则返回 true。

##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered

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

如果字符串相等则为零，< 0 如果*str1*是小于*str2*，或 > 0 如果*str1*大于*str2*。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。

##  <a name="hash"></a>  CStringRefElementTraits::Hash

调用此静态函数以计算给定的字符串元素的哈希值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>参数

*str*<br/>
字符串元素中。

### <a name="return-value"></a>返回值

返回使用字符串的内容计算的哈希值。

## <a name="see-also"></a>请参阅

[CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
