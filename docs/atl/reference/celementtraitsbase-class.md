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
ms.openlocfilehash: 769fa5abff223ad570847b8bf68378ce85df664e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509008"
---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 类

此类提供默认复制并移动集合类的方法。

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

|名称|描述|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|调用此方法将存储在集合类对象中的元素复制。|
|[CElementTraitsBase::RelocateElements](#relocateelements)|调用此方法来重新定位集合类对象中存储的元素。|

## <a name="remarks"></a>备注

此基类的类定义用于复制和重新定位元素的集合类中的方法。 类使用[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)， [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)，并[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。

有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。

## <a name="requirements"></a>要求

**标头：** atlcoll.h

##  <a name="copyelements"></a>  CElementTraitsBase::CopyElements

调用此方法将存储在集合类对象中的元素复制。

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>参数

*pDest*<br/>
指向将接收复制的数据的第一个元素的指针。

*pSrc*<br/>
指向要复制的第一个元素的指针。

*nElements*<br/>
要复制的元素数。

### <a name="remarks"></a>备注

不应重叠的源和目标元素。

##  <a name="inargtype"></a>  CElementTraitsBase::INARGTYPE

要用于将元素添加到集合的数据类型。

```
typedef const T& INARGTYPE;
```

##  <a name="outargtype"></a>  CElementTraitsBase::OUTARGTYPE

要用于从集合检索元素的数据类型。

```
typedef T& OUTARGTYPE;
```

##  <a name="relocateelements"></a>  CElementTraitsBase::RelocateElements

调用此方法来重新定位集合类对象中存储的元素。

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>参数

*pDest*<br/>
指向将接收重新定位的数据的第一个元素的指针。

*pSrc*<br/>
指向要重新定位的第一个元素的指针。

*nElements*<br/>
要重新定位的元素数。

### <a name="remarks"></a>备注

此方法调用[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，足以满足大多数数据类型。 如果要移动的对象包含指向其自己的成员的指针，将需要重写此方法。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
