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
ms.openlocfilehash: 6fa8772033a5a82940cf30b2a73d6ea356269d67
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226550"
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
要存储在集合中的数据的类型。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|调用此静态函数以比较两个字符串元素是否相等。|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|调用此静态函数以比较两个字符串元素。|
|[CStringRefElementTraits：： Hash](#hash)|调用此静态函数以计算给定字符串元素的哈希值。|

## <a name="remarks"></a>备注

此类提供用于比较字符串和创建哈希值的静态函数。 当使用集合类存储基于字符串的数据时，这些函数很有用。 与[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)不同， `CStringRefElementTraits` 导致 `CString` 参数作为 **`const`** `CString&` 引用传递。

有关详细信息，请参阅[ATL Collection 类](../../atl/atl-collection-classes.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>要求

**标头：** atlcoll

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements

调用此静态函数以比较两个字符串元素是否相等。

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>参数

*element1*<br/>
第一个字符串元素。

*element2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果元素相等，则返回 true，否则返回 false。

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered

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

如果字符串相同，则为零; 如果*str1*小于*str2*，则 < 0; 如果*str1*大于*str2*>，则为0。 [CStringT：： Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits：： Hash

调用此静态函数以计算给定字符串元素的哈希值。

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>参数

*字符串*<br/>
String 元素。

### <a name="return-value"></a>返回值

返回使用字符串内容计算所得的哈希值。

## <a name="see-also"></a>另请参阅

[CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
