---
title: "CStringElementTraits 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f46ff072bcd0f772dac1bba52b114d82ee433112
ms.lasthandoff: 02/24/2017

---
# <a name="cstringelementtraits-class"></a>CStringElementTraits 类
此类提供了使用存储的集合类的静态函数`CString`对象。  
  
## <a name="syntax"></a>语法  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要在集合中存储的数据类型。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|说明|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|要用于将元素添加到集合类对象的数据类型。|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|要用于从集合类对象中检索元素的数据类型。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|（静态）调用此函数可比较两个字符串元素相等。|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|（静态）调用此函数可比较两个字符串元素。|  
|[CStringElementTraits::CopyElements](#copyelements)|（静态）调用此函数可将复制`CString`集合类对象中存储元素。|  
|[CStringElementTraits::Hash](#hash)|（静态）调用此函数来计算给定的字符串元素进行哈希值。|  
|[CStringElementTraits::RelocateElements](#relocateelements)|（静态）调用此函数可重新定位`CString`集合类对象中存储元素。|  
  
## <a name="remarks"></a>备注  
 此类提供静态函数复制、 移动和比较字符串和创建哈希值。 使用集合类来存储基于字符串的数据时，这些函数很有用。 使用[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)时不区分大小写的比较是必需。 使用[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)得到处理，作为引用的字符串对象的时间。  
  
 有关详细信息，请参阅[ATL 集合类](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>要求  
 **标头︰** cstringt.h  
  
##  <a name="compareelements"></a>CStringElementTraits::CompareElements  
 调用该静态函数用于比较两个字符串元素相等。  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串元素。  
  
 `str2`  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 如果元素均相等，则返回 false，则返回 true。  
  
##  <a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered  
 调用该静态函数用于比较两个字符串元素。  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>参数  
 `str1`  
 第一个字符串元素。  
  
 `str2`  
 第二个字符串元素。  
  
### <a name="return-value"></a>返回值  
 如果字符串是相同的则为零< 0="" if="">`str1`是小于`str2`，则为 0 1> 如果`str1`大于`str2`。 [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare)方法用于执行比较。  

  
##  <a name="copyelements"></a>CStringElementTraits::CopyElements  
 调用该静态函数以将复制`CString`集合类对象中存储元素。  
  
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
  
##  <a name="hash"></a>CStringElementTraits::Hash  
 调用该静态函数来计算给定的字符串元素进行哈希值。  
  
```
static ULONG Hash(INARGTYPE str);
```  
  
### <a name="parameters"></a>参数  
 `str`  
 字符串元素中。  
  
### <a name="return-value"></a>返回值  
 返回使用字符串的内容来计算哈希值。  
  
##  <a name="inargtype"></a>CStringElementTraits::INARGTYPE  
 要用于将元素添加到集合类对象的数据类型。  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>CStringElementTraits::OUTARGTYPE  
 要用于从集合类对象中检索元素的数据类型。  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="relocateelements"></a>CStringElementTraits::RelocateElements  
 调用该静态函数以重新定位`CString`集合类对象中存储元素。  
  
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
 此静态函数将调用[memmove](../../c-runtime-library/reference/memmove-wmemmove.md)，足以满足大多数数据类型。 如果要移动的对象包含它们自己的成员的指针，将需要此静态函数中被重写。  
  
## <a name="see-also"></a>另请参阅  
 [CElementTraitsBase 类](../../atl/reference/celementtraitsbase-class.md)   
 [CStringElementTraitsI 类](../../atl/reference/cstringelementtraitsi-class.md)   
 [类概述](../../atl/atl-class-overview.md)

