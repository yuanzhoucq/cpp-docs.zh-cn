---
title: CStringElementTraits 类
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 078cfd5ff93bfcd8acc747904ea05e6a2e762bc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330622"
---
# <a name="cstringelementtraits-class"></a>CStringElementTraits 类

此类提供存储`CString`对象的集合类使用的静态函数。

## <a name="syntax"></a>语法

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[弦元素：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|
|[弦元素：：OUTARGTYPE](#outargtype)|用于从集合类对象检索元素的数据类型。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[弦元素：：比较元素](#compareelements)|（静态）调用此函数以比较两个字符串元素以表示相等。|
|[弦元素：：比较元素排序](#compareelementsordered)|（静态）调用此函数以比较两个字符串元素。|
|[弦元素：：复制元素](#copyelements)|（静态）调用此函数以复制`CString`存储在集合类对象中的元素。|
|[弦乐元素：哈希](#hash)|（静态）调用此函数以计算给定字符串元素的哈希值。|
|[弦元素：：重新定位元素](#relocateelements)|（静态）调用此函数以重新定位`CString`存储在集合类对象中的元素。|

## <a name="remarks"></a>备注

此类提供用于复制、移动和比较字符串以及创建哈希值的静态函数。 当使用集合类存储基于字符串的数据时，这些函数非常有用。 当需要不区分大小写的比较时，请使用[CStringElementTraitsI。](../../atl/reference/cstringelementtraitsi-class.md) 当字符串对象要作为引用处理时，请使用[CStringRefElementTraits。](../../atl/reference/cstringrefelementtraits-class.md)

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** cstringt.h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a>弦元素：：比较元素

调用此静态函数以比较两个字符串元素以获得相等性。

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串元素。

*str2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果元素相等，则返回 true，否则为 false。

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>弦元素：：比较元素排序

调用此静态函数以比较两个字符串元素。

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串元素。

*str2*<br/>
第二个字符串元素。

### <a name="return-value"></a>返回值

如果字符串相同，则为零，如果*str1*小于*str2，* 则< 0;如果*str1*大于*str2，* 则> 0。 [CStringT：：比较](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a>弦元素：：复制元素

调用此静态函数以复制`CString`存储在集合类对象中的元素。

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>参数

*pDest*<br/>
指向将接收复制数据的第一个元素的指针。

*pSrc*<br/>
指向要复制的第一个元素的指针。

*n元素*<br/>
要复制的元素数。

### <a name="remarks"></a>备注

源元素和目标元素不应重叠。

## <a name="cstringelementtraitshash"></a><a name="hash"></a>弦乐元素：哈希

调用此静态函数以计算给定字符串元素的哈希值。

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>参数

*Str*<br/>
字符串元素。

### <a name="return-value"></a>返回值

返回使用字符串内容计算的哈希值。

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a>弦元素：：INARGTYPE

用于向集合类对象添加元素的数据类型。

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a>弦元素：：OUTARGTYPE

用于从集合类对象检索元素的数据类型。

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>弦元素：：重新定位元素

调用此静态函数以重新定位`CString`存储在集合类对象中的元素。

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>参数

*pDest*<br/>
指向将接收重新定位数据的第一个元素的指针。

*pSrc*<br/>
指向要重新定位的第一个元素的指针。

*n元素*<br/>
要重新定位的元素数。

### <a name="remarks"></a>备注

此静态函数称为[memmove，](../../c-runtime-library/reference/memmove-wmemmove.md)对于大多数数据类型来说，这就足够了。 如果要移动的对象包含指向其自己的成员的指针，则需要重写此静态函数。

## <a name="see-also"></a>另请参阅

[CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)<br/>
[弦元素特性I类](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
