---
title: CElementTraitsBase 类
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 5a29e8778cf2f3400df25b55574950a005bad995
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327008"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 类

此类为集合类提供默认复制和移动方法。

## <a name="syntax"></a>语法

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>参数

*T*<br/>
要存储在集合中的数据类型。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|说明|
|----------|-----------------|
|[元素特征库：：INARGTYPE](#inargtype)|用于向集合类对象添加元素的数据类型。|
|[元素特征库：：OUTARGTYPE](#outargtype)|用于从集合类对象检索元素的数据类型。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[元素库基础：：复制元素](#copyelements)|调用此方法以复制存储在集合类对象中的元素。|
|[元素库基础：：重新定位元素](#relocateelements)|调用此方法以重新定位存储在集合类对象中的元素。|

## <a name="remarks"></a>备注

此基类定义用于复制和重新定位集合类中的元素的方法。 它被类[CDefaultElementTraits、CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)使用。 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

有关详细信息，请参阅[ATL 收集类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标题：** atlcoll.h

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a>元素库基础：：复制元素

调用此方法以复制存储在集合类对象中的元素。

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

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a>元素特征库：：INARGTYPE

用于向集合中添加元素的数据类型。

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a>元素特征库：：OUTARGTYPE

用于从集合检索元素的数据类型。

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a>元素库基础：：重新定位元素

调用此方法以重新定位存储在集合类对象中的元素。

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

此方法调用[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，对于大多数数据类型来说，这就足够了。 如果要移动的对象包含指向其自己的成员的指针，则需要重写此方法。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
