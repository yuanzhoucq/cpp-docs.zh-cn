---
title: "CElementTraitsBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: a06af7698afb24c1c2391b762673c7e3633018d4
ms.lasthandoff: 02/24/2017

---
# <a name="celementtraitsbase-class"></a>CElementTraitsBase 类
此类提供默认副本，并将移动的集合类的方法。  
  
## <a name="syntax"></a>语法  
  
```
template<typename T>  
class CElementTraitsBase
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要在集合中存储的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](#copyelements)|调用此方法将存储在集合类对象中的元素复制。|  
|[CElementTraitsBase::RelocateElements](#relocateelements)|调用此方法来重新定位在集合类对象中存储元素。|  
  
## <a name="remarks"></a>备注  
 此基类的类定义进行复制和重新定位在集合类元素的方法。 类使用它可以将[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)， [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)，和[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlcoll.h  
  
##  <a name="copyelements"></a>CElementTraitsBase::CopyElements  
 调用此方法将存储在集合类对象中的元素复制。  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>参数  
 `pDest`  
 指向将接收复制的数据的第一个元素的指针。  
  
 `pSrc`  
 指向要复制的第一个元素的指针。  
  
 `nElements`  
 要复制的元素数。  
  
### <a name="remarks"></a>备注  
 源和目标元素不应重叠。  
  
##  <a name="inargtype"></a>CElementTraitsBase::INARGTYPE  
 要用于将元素添加到集合的数据类型。  
  
```
typedef const T& INARGTYPE;
```  
  
##  <a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE  
 要用于从集合中检索元素的数据类型。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CElementTraitsBase::RelocateElements  
 调用此方法来重新定位在集合类对象中存储元素。  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>参数  
 `pDest`  
 指向将接收被重新定位的数据的第一个元素的指针。  
  
 `pSrc`  
 若要重新定位的第一个元素的指针。  
  
 `nElements`  
 要重新定位的元素数。  
  
### <a name="remarks"></a>备注  
 此方法调用[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，足以满足大多数数据类型。 如果正在移动的对象包含它们自己的成员的指针，将需要重写此方法。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../atl/atl-class-overview.md)

