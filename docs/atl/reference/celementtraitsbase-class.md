---
title: "CElementTraitsBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
dev_langs:
- C++
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 8680fc73480fd95c8b2d613f716868d8162a96c8
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 类
此类提供默认副本，并移动的集合类的方法。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要存储在集合中的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|要用来检索元素的集合类对象的数据类型。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|调用此方法以将集合类对象中存储的元素复制。|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|调用此方法可重新定位集合类对象中存储元素。|  
  
## <a name="remarks"></a>备注  
 此基类的类定义复制和重新指定的集合类中的元素的方法。 类使用[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)， [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)，和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlcoll.h  
  
##  <a name="copyelements"></a>CElementTraitsBase::CopyElements  
 调用此方法以将集合类对象中存储的元素复制。  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>参数  
 `pDest`  
 将接收复制的数据的第一个元素的指针。  
  
 `pSrc`  
 指向要复制的第一个元素的指针。  
  
 `nElements`  
 要复制的元素数。  
  
### <a name="remarks"></a>备注  
 不应重叠的源和目标的元素。  
  
##  <a name="inargtype"></a>CElementTraitsBase::INARGTYPE  
 要用于将元素添加到集合的数据类型。  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE  
 要用来从集合检索元素的数据类型。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CElementTraitsBase::RelocateElements  
 调用此方法可重新定位集合类对象中存储元素。  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>参数  
 `pDest`  
 将收到的被重新定位的数据的第一个元素的指针。  
  
 `pSrc`  
 若要重新定位的第一个元素的指针。  
  
 `nElements`  
 要重新定位的元素数。  
  
### <a name="remarks"></a>备注  
 此方法调用[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，这对大多数数据类型足够了。 如果要移动的对象包含指向其自己的成员的指针，此方法将需要重写。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

